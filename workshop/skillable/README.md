@lab.Title

# Get Started

Welcome to **LAB540**! You're about to take the **Zava Travel Concierge** — a multi-agent travel planner running as a **Hosted Agent** on **Microsoft Foundry** — and make it observable, measurable, and better.

>[!Knowledge] **Meet the agent.** Zava Travel's concierge coordinates three specialist sub-agents — **flights**, **hotels**, and **car rentals** — each grounded in its own data. The concierge never answers from its own knowledge; it delegates to the specialists and composes the itinerary.

<br/>

## What you'll do

This lab runs in three short stages:

1. **Setup** &nbsp;•&nbsp; Get the infrastructure and your Codespace ready.
2. **Observe** &nbsp;•&nbsp; Explore the hosted agent in the playground and learn Foundry's built-in observability features.
3. **Optimize** &nbsp;•&nbsp; Run the eval → fix → redeploy loop with Microsoft Foundry Skills and GitHub Copilot.

>[!Note] **Level:** 200–300 &nbsp;•&nbsp; **Duration:** 60 minutes

<br/>

## Before you start

Take a moment to confirm your lab environment loaded correctly:

1. [] Confirm you see an **Instructions** tab and a **Resources** tab in the lab interface.
1. [] Confirm the virtual machine shows a **login screen**, as in the screenshot below.

   ![Lab interface with Instructions and Resources tabs and the VM login screen](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/00-intro-lab-tabs-vm-login.png)

1. [] Click the **Resources** tab and verify it has the **Subscription**,
   **Username**, and **TAP** values filled in.
1. [] Switch back to the **Instructions** tab to continue.


<br/>

>[!Alert] If you don't see these, raise your hand and ask a proctor for help before continuing.

===

# Log Into VM, Launch Browser

First, sign in to the lab VM, then open the browser. You'll work across three
browser tabs during this lab: the **Azure Portal**, the **Foundry Portal**, and
your **GitHub Codespace**.

>[!Knowledge] Text shown +++like this+++ is **type text** — click it and it is typed into the VM at the current focus point, so you avoid typos. 
>
>[!Knowledge] Text shown ++like this++ is **copy text** — click to copy to clipboard, then paste it anywhere. _Useful for large inputs where type-text takes too long._
>
>[!Knowledge] Each step has a **checkbox** — tick it as you go to mark it done. The lab tracks these so you (and we) can see how far you've progressed.

<br/>

## Sign in to the lab VM

1. [] Click in the **password input** field in the VM to give it focus.

1. [] Sign in using the password below:

   **Password:** +++@lab.VirtualMachine(Win11-Pro-Base).Password+++

<!-- TODO screenshot: Windows 11 desktop after sign-in -->

<br/>

## Open the browser

1. [] On the desktop, select the **Microsoft Edge** icon in the taskbar to
   launch a new browser window.

<!-- TODO screenshot: Edge icon in the Windows taskbar -->

>[!Hint] Keep this browser window open for the rest of the lab — you'll add one
> tab per step over the next three pages.

>[!Hint] Prefer dark mode? Click the **...** menu in the Edge toolbar, open
> **Settings**, and switch the appearance to **dark**.

<br/>

---

> ✅ **Success:** You signed into the VM and launched the browser for next steps.

===

# Tab 1 — Azure Portal

Your first tab is the **Azure Portal**, where your pre-provisioned resource group lives.

1. [] Click in the **address bar** of new tab to give it focus, then navigate to +++https://portal.azure.com+++
1. [] Sign in with the lab credentials below:

   - **Username:** +++@lab.CloudPortalCredential(User1).Username+++
   - **Password (TAP):** +++@lab.CloudPortalCredential(User1).AccessToken+++

1. [] If prompted to save the password, **dismiss** it.
1. [] If prompted to stay signed in, check **Don't show this again** and select
   **Yes**.

   ![Azure portal home](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-02-azure-portal-home.png)

1. [] Select **Resource groups** in the portal to view the list of resource
   groups.  Maximize **Edge** if you do not see the **Resource groups**
1. [] Confirm you see **two** resource groups, one of which starts with
   **rg-lab540**.

<br/>

>[!Alert] If you do **not** see a resource group starting with **rg-lab540**,
> raise your hand and ask a proctor for help. This is likely a cold-start
> problem where provisioning hasn't finished yet.

>[!Knowledge] Everything in your resource group — the Foundry project, model
> deployment, container registry, and Application Insights — was pre-provisioned
> for you by the Skillable environment.

>[!Hint] Prefer dark mode? Click the **gear** icon in the portal toolbar, open
> **Appearance**, and switch the theme to **dark**. Click the **gear** icon
> again to return to the default portal page.

---

> ✅ **Success:** the Azure Portal home page is open in **Tab 1**.

===

# Tab 2 — Foundry Portal

Your second tab is the **Microsoft Foundry Portal**, where your hosted agent is
deployed.

1. [] Open a **new tab** in Edge. Click to focus and type +++https://ai.azure.com+++ as address.
1. [] Select the **Sign in** button to login with your credentials.
1. [] After signing in, confirm that the **New Foundry** switch is enabled. If it isn't already active, toggle it on.
1. [] On the **All resources** page, select the existing **ai-project-lab540-...** project.
1. [] After the project opens, select **Agents** from the left navigation menu.
1. [] Confirm that the existing **zava-concierge** agent is displayed. 
1. [] Select the single project you see, then choose **Let's go**.

<!-- TODO screenshot: Foundry portal home with New Foundry toggle on -->

<br/>

>[!Note] A welcome tour or "create an agent" dialog may appear. Close it — your
> agent already exists and you'll open it in the next stage.

---

> ✅ **Success:** the Foundry Portal home is open in **Tab 2** with New Foundry on.

===

# Tab 3 — Launch Codespace

Your third tab is your **GitHub Codespace** — the cloud dev environment where
you'll run the optimize loop later. It takes a few minutes to build, so you'll
start it now and let it warm up while you explore the agent.

## Sign in to the Skillable GitHub org

1. [] Open a **new tab** and navigate to
   +++https://github.com/enterprises/skillable-events/sso+++
1. [] Select **Continue** and complete the sign-in process. You’ll be authenticated with the same lab credentials. 

<!-- TODO screenshot: GitHub SSO Continue with GHE button -->

>[!Alert] If you receive a **404** error, wait for several minutes and then try again.
 
## Launch the Codespace

1. [] Navigate to the workshop repo at +++https://aka.ms/build26/lab540/skillable+++
1. [] Select the green **Code** button, then the **Codespaces** tab.
1. [] Select **Create new codespace** — a new tab opens and begins building.

<!-- TODO screenshot: Code button > Codespaces > Create new codespace -->

>[!Alert] **Don't wait for it to finish.** The Codespace can take several
> minutes to build. Leave this tab open and continue to the next stage — you'll
> come back to it once it's ready.

<br/>

---

> ✅ **Success:** your Codespace is building in **Tab 3**.
>
> 🏁 **Stage 1 complete.** You have three tabs open — Azure Portal, Foundry
> Portal, and your Codespace — and your dev environment is warming up. While it
> builds, you'll explore the hosted agent and Foundry's built-in observability.

===

# Open Playground

While your Codespace builds, switch to the **Foundry Portal** tab (Tab 2) and
meet your hosted agent.

1. [] In the Foundry Portal, click on the **Build** option in navigation bar.
1. [] Next, click the **Agents** option in the left navigation.
1. [] Select the **zava-concierge** agent to open it.

   <!-- Images are sourced from the self-guided tree to keep a single image set. -->
   ![The Foundry portal showing the pre-deployed Zava Travel Concierge agent](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-07-agent.png)

1. [] Click the agent name. An agent playground opens with three panels as shown. Click the highlighted toggles to hide or reveal the side panels. For now, close the left **details** panel but leave the right **logs** panel open.


   ![The Zava Travel Concierge agent playground open in the Foundry portal](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-01-playground.png)

>[!Knowledge] The **playground** is a live chat against your deployed hosted
> agent. Every message you send runs through the real concierge and its
> specialist sub-agents — and is captured for observability.

---

> ✅ **Success:** the Zava Travel Concierge playground is open and ready.

===

# Set Up Metrics

Before you send the first prompt, let's turn on the **evaluators** so Foundry scores each response as it happens.

1. [] In the playground, click the **metrics** button to
   expose the selections as shown.
1. [] Enable all the built-in evaluators for the agent, then
   click to close.

   ![The playground metrics panel with built-in evaluators enabled](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-02-metrics.png)

<br/>

>[!Knowledge] **Evaluators** are automatic graders. Foundry's built-in evaluators score each response on dimensions like **task completion**, **coherence**, and safety (such as **indirect attack** resistance) — no test code required. These are then displayed in aggregate as _AI Quality_ and _AI Safety_ metrics on each response as we will see later.

---

> ✅ **Success:** evaluators are on and the playground is ready for your first
> prompt.

===

# Run Prompt 1

Send a simple, single-specialist request and watch the metrics light up.

1. [] In the playground, type this prompt as input:

   +++What flights are available from Chicago to Rome?+++

1. [] Wait for the concierge to reply with flight options (this takes a few  seconds). 
1. [] Note the default response, the **log stream** of agent actions, the
   auto-evaluated **quality & safety metrics**, and the link to **traces** for this request.

   ![The prompt 1 flight response with evaluator metrics in the playground](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-03-prompt1.png)

## View Evaluation Metrics

1. [] Hover over the **metrics** panel shown in green. You should see the evaluation score components behind it.
1. [] Click on one of the metrics in the green box. It should open up a trace view as shown below. Note how the trace visualizes the sequence of actions within the flow along with token costs and latency per response.
1. [] Note the **evaluations attached to the trace** — the actual scores for the selected quality metrics plus latency, token costs, and the events that produced this response. This lets you correlate metrics with the actions taken, for more effective debugging when needed.

   ![The trace view with quality evaluations attached for the prompt 1 turn](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-03-trace.png)

>[!Knowledge] **Evaluators** are automatic graders that score each response live
> on quality and safety — no test code required. A **trace** is the step-by-step
> record of how the agent produced its answer, including the call it made to the
> **Flight Specialist**. The evaluator scores hang right off the trace, so
> quality and execution live in one place.

## View Monitoring Metrics

1. [] Close the trace window, then click the **Monitor** tab in the playground
   navigation. This is the production monitoring view for your deployed agent —
   a single pane of glass showing how many times it was called, tokens consumed,
   tools invoked, and failures across its lifetime.

   ![The Monitor tab showing aggregated agent metrics and evaluations](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-03-monitor.png)

1. [] Click the **agent helper** icon within any chart to get an AI-generated
   analysis of that metric, surfacing insights into agent performance.

   ![The Runs and token metrics chart with an AI-generated analysis of agent runs and token usage](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-03-monitor-analyze.png)

>[!Knowledge] The **Monitor** tab is your single pane of glass in production. It
> aggregates calls, token usage, tool invocations, and failures across the
> agent's lifetime, with AI-generated analysis to surface insights.

---

> ✅ **Success:** you've seen a response scored live, opened its trace with
> evaluations, and explored production monitoring.

===

# Run Prompt 2

Now send a multi-part request that makes the concierge coordinate all three
specialists.

1. [] In the playground, send this prompt:

   +++Plan a trip from Chicago to Rome for the first two weeks of November. I need flights, a hotel, and a car rental.+++

1. [] Wait for the concierge to compose the full itinerary — the response now
   includes flight, hotel, and car results, so all three specialists were called
   before composing the final answer.

   ![The prompt 2 itinerary response combining flights, hotel, and car rental](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-prompt2.png)

## Explore Trace Viewer

1. [] Select **Traces**.
1. [] Select **Conversation view**.
1. [] Locate the recorded conversation and select the **Conversation ID.**
1. [] In the trace detail window, select the **Trajectories** tab if it is not already selected.   
1. [] **Trajectory** view visualizes this turns trace as a **conversation** — the concierge delegating
   to the flight, hotel, and car-rental agents. Click **Play** to watch it unfold, and check the metrics (top-right) for chat calls, tool calls, tokens, time, and **spans**.

   ![The Trajectory view visualizing the conversation trace with the concierge delegating to the flight, hotel, and car-rental agents](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-trajectory.png)

1. [] Click the **User View** tab, then **Play**. This is a time-based replay of
   which requests went to each agent, when, and how the final response was
   composed — giving you an intuitive sense of per-agent latency. Each agent's
   requests and responses stream in parallel before being merged into one reply.

   ![The User View tab showing a time-based replay of requests to each agent](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view.png)

>[!Knowledge] **Trajectory vs. User View** are two complementary lenses on the
> same trace. You can pause the trace in one view, and resume in the other to see how they correlate for debugging etc..

- The **Trajectory view** exposes the agent's internal orchestration how the concierge decomposed and delegated — so you can pinpoint *which* agent or tool call went wrong. Replays also give you an intuitive sense for latency by making you "see" delays between actions, or time spent in executing a tool call etc. 
- The **User View** replays the interaction on a timeline, showing *when* each request fired, so you can spot the step responsible for latency. It also makes it easier to see how agents are streaming responses in parallel.
- Together they let you debug correctness and diagnose performance from a single captured trace — no re-running required.

---

> ✅ **Success:** you've inspected a multi-agent conversation trace through both
> the Trajectory and User View lenses.

===

# Run Prompt 3

Finally, send an **out-of-scope** request and watch the agent's instructions
keep it on task.

1. [] In the playground, send this prompt and read the concierge's description
   of its role as a travel concierge:

   +++what can you do?+++

1. [] Now send an out-of-scope prompt and watch the agent keep on task:

   +++Can you help me write a Python script?+++

1. [] Confirm the concierge **politely declines** and redirects to travel
   topics instead of answering. If it doesn't, that's another area for agent
   optimization.

   ![The concierge politely declining the out-of-scope request and redirecting to travel topics](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-05-prompt3.png)

>[!Knowledge] The concierge's **agent instructions** define its scope. Because
> the instructions tell it to handle travel only, it refuses unrelated requests
> — exactly the behavior you'll measure and protect with evaluations.

>[!Knowledge] These initial checks across prompts 1–3 give a baseline read on
> where the agent can be **optimized** — across **cost**, **latency**, and
> **quality**. The gaps they surface are the issues you'll fix iteratively in
> the next stage.

---

> ✅ **Success:** the agent correctly refused an out-of-scope request.
>
> 🏁 **Stage 2 complete.** You've validated that the infrastructure and hosted
> agent work, and you understand Foundry's built-in observability — metrics,
> traces, evaluations, and replays. Next, you'll improve the agent from code.

===

# Open Codespace

Your Codespace should be ready now. Switch to its tab (Tab 3) and let's move to code-first observabilty.

1. [] Switch to the **Codespace** tab. Wait until VS Code has fully loaded.
1. [] If the **Codespace** has stopped after being idle, select **Restart** and wait for the **Codespace** to start. 
1. [] Wait until **VS Code** has fully loaded. 
1. [] If the **Do you trust the authors of the files in this folder?** prompt appears, select **Trust Folder** & **Continue** to proceed. 

1. [] Open a terminal (**Terminal → New Terminal**).
1. [] Confirm the core CLIs are present:

   +++az version+++

   +++azd version+++

   +++python --version+++


## Reset to the clean baseline

Clear any stale **.foundry** state and restore the baseline concierge prompt. This ensures every run starts from the same intentionally under-optimized prompt as everyone else:

1. [] Type this command in the terminal to execute it:  +++rm -rf zava/src/zava-travel-concierge/.foundry+++
1. [] Type this command to run script: +++bash zava/src/zava-travel-concierge/scripts/reset-instructions.sh+++

## What **main.py** does

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

===

# Sign in to Azure

The optimize loop talks to your Foundry project from code, so sign in with both
the Azure CLI (**az**) and the Azure Developer CLI (**azd**). You'll use **device
code** sign-in to keep things simple inside the Codespace.

## Sign in with **az**

1. [] In the terminal, run:

   +++az login --use-device-code+++

1. [] Open the verification URL, enter the code shown, and sign in with your lab
   credentials:

   **Username:** +++@lab.CloudPortalCredential(User1).Username+++
   **Password (TAP):** +++@lab.CloudPortalCredential(User1).AccessToken+++

1. [] When prompted, select the default subscription.

## Sign in with **azd**

1. [] In the terminal, run:

   +++azd auth login --use-device-code+++

1. [] Complete the same device-code sign-in flow.

<!-- TODO screenshot: device code sign-in prompt -->

## Setup **.env** in Codespaces

Run the script to automatically have your **.env** created from the deployed infrastructure.

1. [] Type this command in the terminal to execute it:  +++bash scripts/discover-env.sh+++
1. [] You will be prompted for the name of the resource group to use. Enter the resource group name you see in the Azure portal tab. It should start with **rg-lab540-**.

>[!Alert] If you try to copy-paste the value into the terminal, you will get a pop-up asking permission to **read from and write to the clipboard**. Select **Allow** — you will need this for future copy-paste actions.

1. Wait till the script is complete. Verify that a **.env** was setup with all required parameters filled in.

>[!Knowledge] This *.env* will be used by GitHub Copilot in a subsequent step to establish our *.azure* configuration for the Azure Developer CLI tooling.

---

> ✅ **Success:** you're signed in to Azure with both **az** and **azd**.

===

# Activate Copilot

You'll drive the optimize loop by talking to **GitHub Copilot**, which uses the
**Foundry MCP** and the **microsoft-foundry** skill to do the work.

1. [] Open **Copilot Chat** (Ctrl+Alt+I) and switch to **Agent** mode.
1. [] Say hello to confirm it's responding - wait till it's ready:

   +++Hello!+++

## Enable Foundry MCP Server

1. [] Make sure the **Foundry MCP server** is enabled (check the tools/MCP
   picker in Copilot Chat).

   When you say hello, the chat will prompt you to **activate the Foundry MCP
   server** — choose **Yes**. This starts an authentication flow; **sign in with
   the same credential you used for Azure**.

   ![The Foundry MCP server activation prompt and sign-in flow](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-mcp-activation.png)

## Select Chat Model

>[!Alert] You may see Copilot try to enforce a different model (e.g., **Codestral** or **Fable**) as the default model
> and show an error related to downloads. Just dismiss these — **start a new chat session** and explicitly
> pick **Claude Sonnet 5.5** as the model.

1. [] Set the chat **model** to **Claude Sonnet 5.5**.

   ![Copilot Chat in Agent mode with the Foundry MCP enabled](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-open-copilot-chat.png)

1. [] **Speed things up.** Below the Copilot Chat input box, select **Default permissions.**
1. [] Select **Allow all** and then **Enable** to allow Copilot to run tool calls without asking for confirmation.
  
   **Default Approvals** control and switch it to **Bypass Approvals**. The Observe skill runs many steps, and this lets Copilot run tools without asking you to confirm each one. *If you start a new Copilot session, you will need to repeat this action to change the default*.

   ![Switching from Default Approvals to Bypass Approvals in Copilot Chat](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-bypass-approvals.png)


## Use Copilot To Recreate **.azure**

Our infrastructure was _pre-provisioned_ by the Azure Developer CLI (azd) using the code under the **zava/** folder. We will need to _redeploy_ this during the optimize loop — but we lack the default **.azure** folder with the default configuration information.

Let's ask Copilot to help us recreate it before we begin optimization.

- [] Click to **copy and paste** this prompt into Copilot Chat: ++I just recreated the .env file for this project. I previously deployed my agent to this resource group from the zava/ folder Use "azd init" and "azd ai agent init --project-id" to refresh the "zava/.azure/" folder from my azd provisioned project. Set ENABLE_CAPABILITY_HOST="false" and ENABLE_HOSTED_AGENTS="true". Make sure these variables are also defined: AZURE_SUBSCRIPTION_ID, AZURE_TENANT_ID,  AZURE_AI_PROJECT_NAME, AZURE_AI_PROJECT_ID, AZURE_AI_PROJECT_ENDPOINT, AZURE_AI_PROJECT_ACR_CONNECTION_NAME,  AZURE_AI_FOUNDRY_PROJECT_ID, FOUNDRY_PROJECT_ENDPOINT, AZURE_ENV_NAME, AZURE_LOCATION, AZURE_OPENAI_ENDPOINT, and AZURE_RESOURCE_GROUP++
- [] Verify that the **zava/.azure** folder is created and that a subfolder exists for the **rg-lab540-XXX** environment for your deployed project.

>[!Hint] The **azd** tool is evolving rapidly which means we may still encounter errors or undocumented behaviors. That's okay. GitHub Copilot is equipped with the right context (via MCP servers) to figure out alternative ways to get the task completed. Just give it time to finish.


>[!Alert] If GitHub Copilot execution itself fails for any reason, raise your hand and ask a proctor for help.

---

> ✅ **Success:** Copilot is in Agent mode, the Foundry MCP is enabled, the model
> is set, and approvals are bypassed.

===

# Meet the Skill

Before you run it, take a moment to understand what the **Observe skill** does.

1. [] Ask Copilot to explain the skill:

   +++Tell me about the microsoft-foundry skill and what the observe sub-skill does in this context.+++

1. [] Read the summary it gives you. It may look like this:

   ![Copilot Chat listing the microsoft-foundry skills and sub-skills](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-04-skills-summary.png)

1. [] In this workshop you'll focus on the **observe** skill. If time permits, you can use the same deployed agent to explore the other skills with Copilot.

>[!Knowledge] The **microsoft-foundry Observe skill** automates the evaluation
> lifecycle for your hosted agent. In one workflow it:
>
> 1. **Generates** a test dataset tailored to your agent's capabilities.
> 2. **Evaluates** the deployed agent against that dataset with built-in
>    evaluators.
> 3. **Analyzes** the failures and patterns in the results.
> 4. **Recommends** specific optimizations to improve quality.

---

> ✅ **Success:** you understand what the Observe skill will do before you run it.

===

# Run the Skill

Now kick off the Observe skill and let it work.

1. [] In Copilot Chat, send the activation prompt:

   +++Use the observe subskill of the microsoft-foundry skill to evaluate my deployed zava-concierge agent+++

1. [] Confirm Copilot starts the Observe workflow (you'll see it begin creating
   files and calling Foundry tools).

   ![Copilot Chat kicking off the Observe workflow with tool calls and files](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-05-start-observe.png)

---

> ✅ **Success:** the Observe skill is running against your hosted agent.

===

# Watch Baseline

Watch the Observe skill work. This is **code-first optimization** — the same
loop you saw in the portal, now driven from your editor.

As it runs, you'll see Copilot:

1. [] Create a **.foundry** folder with the generated evaluators and test
   dataset.

>[!Hint] Once the **.foundry** folder appears, open **zava/src/zava-travel-concierge/.foundry/agent-metadata.yaml**
> in the editor. Leave it open — it updates as the loop runs and gives you a
> live view of the observe loop's progress.
1. [] Run a **baseline evaluation** of your deployed agent against that dataset.
1. [] Produce a set of **recommendations** based on the failures it found.

It creates a plan of action and starts executing tasks to establish the baseline
evaluation results, as shown below.

![Copilot Chat creating tasks and running the baseline evaluation](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-init-tasks.png)

>[!Alert] **Let it finish.** The baseline run and analysis take a few minutes.
> Watch the updates stream in and **wait until the recommendations appear**
> before moving on.

---

> ✅ **Success:** you just saw **code-first optimization** — a baseline
> evaluation and recommendations generated from your own editor.

===

# Pick Top Fix

The skill has handed you a ranked list of recommendations. Now choose the one to
apply.

1. [] Review the recommendations Copilot produced.
1. [] Ask for the leading fix if you want it called out:

   +++What's the top recommendation, and what change does it propose?+++

1. [] Tell Copilot to apply that fix:

   +++Apply the top recommendation and optimize the agent's instructions.+++

<!-- TODO screenshot: recommendations list with top fix selected -->

>[!Knowledge] The recommendations are a **hypothesis generator**, not an oracle.
> Picking the top fix and measuring the result is exactly how the optimize loop
> is meant to work.

---

> ✅ **Success:** you've selected a recommendation and asked Copilot to apply it.

===

# Optimize & Redeploy

Watch Copilot apply the fix and push a new version of your agent — the loop
closing itself.

As it runs, you'll see Copilot:

1. [] Update the agent's **instructions** with the optimized version.
1. [] **Redeploy** the hosted agent (rebuild + push, then publish a new
   revision).
1. [] Optionally **re-evaluate** against the same dataset to compare before and
   after.

<!-- TODO screenshot: redeploy + comparison output in chat -->

>[!Knowledge] Improvement isn't guaranteed on every pass — a regression is
> **data**, telling you which axis you traded off. The value is the feedback
> signal that makes your next change more informed.

---

> ✅ **Success:** you just saw **continuous optimization** in action — the agent
> was fixed and redeployed from your editor.
>
> 🏁 **Stage 3 complete.** You ran one full **eval → fix → redeploy** loop with
> Foundry Skills. You've now observed, evaluated, and optimized your hosted
> agent end to end. 🎉
