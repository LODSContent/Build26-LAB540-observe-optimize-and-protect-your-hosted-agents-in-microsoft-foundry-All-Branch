# Return to Codespace

Your GitHub Codespace should be ready by now. Switch back to that tab and let's move to **code-first observability.**

1. [] Verify that you see something like this. This shows the Codespace is loaded and ready. Click **Trust Folder & Continue** to dismiss the dialog. 

   ![The VS Code dialog asking whether you trust the authors of the files in this folder, with the Trust Folder & Continue button](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-01-trust-folder.png)

1. [] Verify that the Foundry Toolkit (FTK) extension is installed by checking the VS Code sidebar. This is required to use the **Foundry MCP Server**. _Note: As shown, the FTK icon may sometimes not be rendered correctly - hover over the spot to see if the extension exists_.

   ![The VS Code sidebar with the Foundry Toolkit icon highlighted and its tooltip shown](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-01-foundry-toolkit.png)

>[!Hint] If the Codespace had stopped (idle timeout), select restart or reload the tab and wait till it loads completely. It should take just a minute or so this time.

>[!Hint] If the FTK extension is not installed, call a proctor to ask for help installing it manually.

<br/>

## Validate Environment

1. [] Open a terminal (**Terminal → New Terminal**).

>[!Alert] The first time you paste into the terminal, you will see a browser pop-up asking for permission to access the clipboard. Select **Allow** — otherwise you will be unable to copy-paste into the terminal later.

1. [] Copy and paste each command below in the terminal to verify command-line tools are installed:

   ++az version++

   ++azd version++

   ++python --version++


## Reset the baseline

The _.foundry/_ folder contains state from previous Foundry skills runs. Run these commands to clear any stale state so you start at the same intentionally under-optimized prompt as everyone else:

1. [] Run this command in the terminal to remove stale folders. 

   +++rm -rf zava/src/zava-travel-concierge/.foundry+++

1. [] Run this command to reset instructions.

   +++bash zava/src/zava-travel-concierge/scripts/reset-instructions.sh+++

>[!Alert] You may see a pop-up the first time you run this command as well. Select **Allow** to continue.

## Study the agent (**main.py**)

1. [] Open the agent's source file **zava/src/zava-travel-concierge/main.py** and skim it. This is the agent you've been observing — and the code the optimize loop will change.
1. [] Read the description below to understand the components that make up our **zava-concierge** hosted agent.

**main.py** defines the whole **multi-agent system** with the **Microsoft Agent
Framework (MAF)** — Microsoft's open-source SDK for building agents in Python or
C#, where agents, tools, and orchestration are all defined in code.

| Component | What it is |
|:----------|:-----------|
| **Specialist agents** | **flight_agent**, **hotel_agent**, and **car_rental_agent** — each with its own instructions and a single typed Python **tool** (**search_flights**, **search_hotels**, **search_car_rentals**) that queries one CSV catalog. |
| **Concierge agent** | **zava-concierge** exposes the three specialists **as tools** and orchestrates them — delegating in parallel and merging the results into a single itinerary. |
| **Concierge instructions** | The concierge's system prompt, loaded from **instructions/concierge.md**. **This is the file the optimize loop will edit** to improve quality. |
| **ResponsesHostServer** | Wraps the concierge so it runs as a Foundry **hosted agent** behind the Responses protocol. |

---

> ✅ **Success:** your Codespace is open, **az**, **azd**, and **python** are all
> available, you've reviewed the agent code, there's no stale **.foundry**
> folder, and the concierge prompt is reset to the baseline.
