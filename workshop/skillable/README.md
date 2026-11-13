@lab.Title

# Get Started

Welcome to **LAB540**! You're about to take the **Zava Travel Concierge** — a multi-agent travel planner running as a **Hosted Agent** on **Microsoft Foundry** — and make it observable, measurable, and better.

>[!Knowledge] **Meet the agent.** Zava Travel's concierge coordinates three specialist sub-agents — *flights*, *hotels*, and *car rentals* — each grounded in its own data. The concierge never answers from its own knowledge; it delegates to the specialists and composes the itinerary.

<br/>

## What you'll do

This lab runs in three short stages:

1. **Setup** - Get the infrastructure and your Codespace ready.
2. **Observe** - Explore the hosted agent in the playground. Learn Foundry's built-in observability features.
3. **Optimize** - Run the eval → fix → redeploy loop with Microsoft Foundry Skills and GitHub Copilot.

>[!Note] **Level:** 200–300 &nbsp;•&nbsp; **Duration:** 60 minutes

<br/>

## Before you start

Check that your lab environment loaded correctly as shown in the image:

1. [] You see the **Instructions** and  **Resources** tabs at right.
1. [] You see the **login screen** for the virtual machine at left.

   ![Lab interface with Instructions and Resources tabs and the VM login screen](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/00-intro-lab-tabs-vm-login.png)

1. [] Click the **Resources** tab. Verify it has **Subscription**, **Username**, and **TAP** values filled in.
1. [] Switch back to the **Instructions** tab to continue.

>[!Alert] If you don't see these values filled in, raise your hand and ask a proctor for help before continuing.

===

# Log Into VM, Launch Browser

This lab uses the **Azure Portal**, the **Foundry Portal**, and **GitHub Codespace** in the browser. Lets get these setup first.

Some useful hints for doing this lab:

>[!Hint] Text shown +++like this+++ is **type text**. Click to have it entered into the VM  _automatically_ into the VM at the location in focus.

>[!Hint] Text shown ++like this++ is **copy text**. Click to copy it to the clipboard. You will then paste into VM location manually.

>[!Hint] Each step has a **checkbox** to track progress. You can check multiple steps at once by checking just the last box in the sequence. _You will be prompted to verify this was intentional the first time. Confirm it._

<br/>

## Sign in to the lab VM

1. [] Click in the **password input** field in VM to give it focus. Then click the password item below to complete login.

   **Password:** +++@lab.VirtualMachine(Win11-Pro-Base).Password+++

<!-- TODO screenshot: Windows 11 desktop after sign-in -->

<br/>

## Open the browser

1. [] Click the **Microsoft Edge** icon on the VM deskstop to launch a new browser window.

Keep the browser open. We'll setup three browser tabs over the next three steps.

<br/>

---

> ✅ **Success:** You signed into the VM and launched the browser for next steps.

===

# Setup Tab 1: Azure Portal

The **Azure Portal** is where you see the details of the pre-provisioned resources for this lab.

1. Open a new browser tab and navigate to +++https://portal.azure.com+++

1. [] Sign in with these lab credentials:

   - **Username:** +++@lab.CloudPortalCredential(User1).Username+++
   - **TAP:** +++@lab.CloudPortalCredential(User1).AccessToken+++

1. [] If prompted to save the password, **dismiss** it.
1. [] If prompted to stay signed in, check **Don't show this again** and select **Yes**.
1. [] Dismiss any other Edge popups you see.

You should see an Azure portal page like this:

   ![Azure portal home](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-02-azure-portal-home.png)

1. [] Select **Resource groups** in the portal to view the list of resource
   groups.  Maximize **Edge** if you do not see the **Resource groups**
1. [] Confirm you see **two** resource groups, one of which starts with
   **rg-lab540**.

   ![The Resource groups page listing ResourceGroup1 and an rg-lab540 resource group](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-02-resource-groups.png)

<br/>

>[!Alert] If you do **not** see the resource group starting with **rg-lab540**, raise your hand and ask a proctor for help. This is likely a cold-start problem where provisioning hasn't finished yet.

---

> ✅ **Success:** Your Azure portal tab is ready and resource group was provisioned.

===

# Setup Tab 2: Foundry Portal

The **Microsoft Foundry Portal** is where you view your hosted agent and related project details.

1. Open a new browser tab and navigate to  +++https://ai.azure.com+++ 

1. [] Click the **Sign in** button. It should login automatically with the previous Azure credentials.
1. [] You should see the **All Resources** page shown below with the **New Foundry** tab enabled. _If not enabled, toggle it on_.

   ![The All resources page with the New Foundry toggle enabled](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-03-new-foundry-toggle.png)

1. [] You should see a single **ai-project-lab540-...** project listed. Click to view its details page. _If you see any additional popups, dismiss them._

   ![The Foundry project home page with the "Your project is set up" dialog and its Skip button](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-03-project-home.png)

1. [] Now click the **Agents** option in the menu sidebar. You should see a single **zava-concierge** agent displayed as shown.

   ![The Agents page in the Foundry portal listing the running zava-concierge hosted agent](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-03-agents-list.png)

<br/>

---

> ✅ **Success:** Your Foundry portal tab is ready with the zava-concierge agent deployed.

===

# Setup Tab 3: GitHub Codespaces

We will use **GitHub Codespace** as the development environment for this lab. It takes a few minutes to load - so we will start the process in this step and let it complete in the background.


## Sign in to the Skillable GitHub org

1. [] Open a new browser tab and navigate to +++https://github.com/enterprises/skillable-events/sso+++

   ![The Single sign-on to Skillable Events page with the green Continue button](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-04-github-sso.png)

1. [] Click **Continue**. You’ll be authenticated with the same Azure lab credentials. 

>[!Alert] If you receive a **404** error, wait for several minutes and then try again. This is likely because the GitHub Enterprise license is still being activated.
 
<br/>

## Launch the Codespace

1. [] Copy the repository link below to the address bar in this tab, and click to navigate to the lab repo page: ++https://aka.ms/build26/lab540/skillable++

1. [] Click the green **Code** button for a drop down menu. Select the **Codespaces** tab and click the **Create codespace on main** button shown.

   ![The Code button's Codespaces tab showing the Creating codespace button after it is selected](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-04-create-codespace.png)

> **A new browser tab should open with a VS Code session loading.** This is your GitHub Codespaces tab. 

![A new browser tab with VS Code in the browser showing Opening Remote and Building codespace while the Codespace starts](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-04-codespace-opening.png)

>[!Alert] **Don't wait for the page to load.** GitHub Codespaces can take several minutes to build. Leave this tab open and move to the next step. We'll come back here later in the lab to check if it is ready.

<br/>

---

> ✅ **Success:**  Your GitHub Codespaces environment is loading.
>

> 🏁 **Stage 1 (Setup) is complete.** 
Your browser should now have four open tabs - Azure Portal, Foundry Portal, GitHub Repository, GitHub Codespaces - as shown in the image above.

===

# Open Agent Playground

While GitHub Codespaces loads, let's use the time to explore our hosted agent. Switch to the **Foundry Portal** tab (Tab 2) you had setup previously.

1. [] You should be on the **Agents** page with the **zava-concierge** agent listed. _If not, just click the Build menu option and select Agents from the sidebar to see this view_.

   ![The Agents page in the Foundry portal listing the running zava-concierge hosted agent](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/01-setup-03-agents-list.png)

1. [] Click on **zava-concierge** to open its agent playground. You will see three panels: **Setup** on the left, the chat in the middle, and **Log stream** on the right as shown below.

1. [] Click the highlighted toggle to close the left **Setup** panel.

   ![The zava-concierge agent playground with the Setup panel toggle highlighted](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-01-playground.png)

1. [] Leave the right **Log stream** panel open for now so we can view the logs. (We can use the highlighted toggle to close it later).

   ![The playground with the Setup panel closed and the Log stream panel toggle highlighted](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-01-playground-logs.png)

>[!Knowledge] The **playground** is a live chat against your deployed hosted
> agent. Every message you send runs through the real concierge and its
> specialist sub-agents — and is captured for observability.

---

> ✅ **Success:** the Zava Travel Concierge playground is open and ready.

===

# Activate Evaluation Metrics

Before you send the first prompt, let's turn on the **evaluators** so Foundry scores each response as it happens.

1. [] In the playground, click the **metrics** button to
   expose the selections as shown.
1. [] Enable all the built-in evaluators for the agent, then
   click to close.

   ![The playground Metrics dropdown listing the built-in evaluators to enable](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-02-metrics.png)

<br/>

>[!Knowledge] **Evaluators** are automatic graders. Foundry's built-in evaluators score each response on dimensions like **task completion**, **coherence**, and safety (such as **indirect attack** resistance) — no test code required. These are then displayed in aggregate as _AI Quality_ and _AI Safety_ metrics on each response as we will see later.

---

> ✅ **Success:** evaluators are on and the playground is ready for your first
> prompt.

===

# Run Simple Prompt

Send a simple, single-specialist request and watch the metrics light up.

1. [] Copy the text below and paste it into the "Message the agent" text area. Then click the arrow to submit the request as shown. 

   ++What flights are available from Chicago to Rome?++

   ![The first prompt pasted into the Message the agent box in the zava-concierge playground](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-prompt1-input.png)

1. [] Wait for the concierge to reply with flight options (this takes a few  seconds). You should see the **log stream** of agent actions - and **evaluated metrics**  for response

   ![The concierge reply listing Chicago to Rome flights, with the Log stream and the AI Quality and Safety metrics highlighted](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-prompt1-reply.png)


>[!Knowledge] If agent responds by asking you to clarify dates, say "my dates are flexible" and see what happens. Agent responses are non-deterministic so your exact text and evaluation metrics may vary.

## View Evaluation Metrics

1. [] Hover over the **AI Quality** metric. You should see the evaluation score components behind it as shown above.

   ![Hovering the AI Quality metric shows Coherence, Fluency, and Relevance passing and Task adherence failing](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-prompt1.png)

1. [] Click on one of the metrics in the green box. It should open up a trace view as shown below. Note how the trace visualizes the sequence of actions within the flow along with token costs and latency per response.

1. [] Note the **evaluations attached to the trace** — the actual scores for the selected quality metrics plus latency, token costs, and the events that produced this response. This lets you correlate metrics with the actions taken, for more effective debugging when needed.

   ![The conversation trace with the flight_agent tool call and the Evaluations tab showing per-metric scores and reasoning, including a failing Task adherence score](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-trace.png)

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

   ![The Monitor tab showing aggregated agent metrics and evaluations](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-monitor.png)

1. [] Scroll down to view the Token usage panel. It should show you the tokens used by this agent so far. Click on the **Open cost dashboard** to see cost details for that period. _This will switch you to the Cost (Preview) tab under Monitoring. After review, click the Overview tab to return to the original pane._

   ![The Cost (Preview) dashboard for the agent under Monitoring](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-cost.png)

1. [] Scroll up to view the Agent runs panel. It should show you the agent requests made during a given period. Click the **View agent traces** button to dive into agent traces for that period. _This will switch you to the Traces pane for the Agent. After review, click the Monitor tab to return to the original pane._

   ![The Traces pane listing the agent's recent traces for the selected period](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-03-agent-traces.png)


>[!Knowledge] The **Monitor** tab is your single pane of glass in production. It
> aggregates calls, token usage, tool invocations, and failures across the
> agent's lifetime, with AI-generated analysis to surface insights.
> **Your specific pane may show different metrics based on your usage**.

---

> ✅ **Success:** you've seen a response scored live, opened its trace with
> evaluations, and explored production monitoring.

===

# Run Complex Prompt

Now send a multi-part request that makes the concierge coordinate all three
specialists.

1. [] Return to the Playground tab. Use the "+" icon (next to Metrics) to start a new chat.

1. [] Click the "→" on Logstream pane to close it. You should see just the playground panel in focus.

1. [] Copy this prompt into the chat and submit the request:

   ++Plan a trip from Chicago to Rome for the first two weeks of November. I need flights, a hotel, and a car rental.++

1. [] Wait for the concierge to compose the full itinerary. Note that the response now includes flight, hotel, and car results! All three specialists were called before composing the final answer.

   ![The prompt 2 itinerary response combining flights, hotel, and car rental](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-prompt2.png)

<br/>

## Explore Trace Viewer

What happened when you made the request? We can use traces to look under the hood and see how the request-response flow occurred,

1. [] Select **Traces**. Then switch to the **Conversation view** tab.

   ![The Traces tab in Conversation view listing recent conversation IDs with duration, tokens, and estimated cost](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-conversation-view.png)

1. [] Locate the recorded conversation and select the **Conversation ID.**. You should see this trace detail view with the **Trajectories** tab selected.   

   ![The trace detail view with the Trajectories tab selected, highlighting the Play controls and the span, chat call, tool call, time, and token metrics](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-trace-detail.png)

1. [] Check the metrics (top-right) for chat calls, tool calls, tokens, time, and **spans**. And note the Play button that gives you a time-lapse replay of traces. We'll try that next.

1. [] Switch to the **User View** tab. This shows you the chat conversation view of the traces. Click the **Span tree** button to expand that pane. You should now see both the user view and the trajectory view side by side. _Optional: Use the toggle on the other size to close the Metadata pane to focus on traces alone_.

   ![The User view tab during replay, with the Span tree expand toggle highlighted on the left and invoke_agent span metadata on the right](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view.png)

1. [] Click **Play**. You'll see a time-based replay showing which requests went to each agent, when, and how the final response was composed — giving you an intuitive sense of per-agent latency. Each agent's requests and responses stream in parallel before being merged into one reply. **Notice how the timeline color matches the step in the trajectory, and correlates to the state of the chat output**.

   ![The User view replaying the conversation with the Span tree expanded on the left, highlighting the active span as the agent responses stream in on the right](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view-replay.png)

1. [] (Optional) Click the **Graph View** tab, then **Play**. This shows the trace as a node-and-edge graph. Each agent and tool is a node, and each edge is a call or handoff between them. As the replay runs, nodes light up in order, so you can see how the concierge connects to the flight, hotel, and car-rental agents and which paths ran during this turn.

   ![The Graph view replaying the trace, with the active span highlighted in the Span tree and as a node in the graph](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-04-graph-view.png)


1. [] Close the trace view dialog and return to the "Playground" tab for the next step.

<br/>

>[!Knowledge] **Trajectory, User and Graph Views** are complementary lenses on the same trace. You can switch views in the middle of a replay (or pause, switch, resume if preferred) to see how a specific moment appears in each for debugging etc..

- The **Trajectory view** exposes the agent's internal orchestration how the concierge decomposed and delegated — so you can pinpoint *which* agent or tool call went wrong. Replays also give you an intuitive sense for latency by making you "see" delays between actions, or time spent in executing a tool call etc. 
- The **User View** replays the interaction on a timeline, showing *when* each request fired, so you can spot the step responsible for latency. It also makes it easier to see how agents are streaming responses in parallel.
- The **Graph View** maps the trace as a topology of agents and tools connected by calls and handoffs, so you can quickly see *who talked to whom* and spot unexpected, missing, or repeated paths in the orchestration.
- Together they let you debug correctness and diagnose performance from a single captured trace — no re-running required.

---

> ✅ **Success:** you've inspected a multi-agent conversation trace through both
> the Trajectory and User View lenses.

===

# Run Out-of-Scope Prompt

Finally, send an **out-of-scope** request and watch the agent's instructions
keep it on task.

1. [] Start a new chat session in the Playground and send this prompt to get a sense for the concierge's role and instructions.

   ++what can you do?++

1. [] Now make an out-of-scope request and see if the agent can stay on task.

   ++Can you help me write a Python script?++

1. [] Confirm the concierge **politely declines** and redirects to travel
   topics instead of answering. 

   ![The concierge politely declining the out-of-scope request and redirecting to travel topics](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/02-observe-05-prompt3.png)


>[!Hint] **What if the agent responds by doing the task?** This can be a signal for prompt optimization to tighten the guardrails. You can try a simple exercise to see if you can reinforce the rule and see what happens. 

1. Paste this prompt into the chat. The agent should respond by acknowledging its mistake.

   ++Should you not be declining all requests outside travel topics?++

1. Then try the prompt again. The agent should now decline to do the task.

      ++Can you help me write a Python script?++

   - [] Now, send the same prompt again. You should see the request declined.


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

# Return to Codespace

Your Github Codespace should be ready by now. Switch back to that tab and let's move to **code-first observabilty.**

1. [] Verify that you see something like this. This shows the Codespaces is loaded and ready. Click **Trust Folder & Continue** to dismiss the dialog. 

   ![The VS Code dialog asking whether you trust the authors of the files in this folder, with the Trust Folder & Continue button](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-01-trust-folder.png)

1. [] Verify that the Foundry Toolkit (FTK) extension is installed by checking the VS Code sidebar. This is required to use the **Foundry MCP Server**. _Note: As shown, the FTK icon may sometimes not be rendered correctly - hover over the spot to see if the extension exists_.

   ![The VS Code sidebar with the Foundry Toolkit icon highlighted and its tooltip shown](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-01-foundry-toolkit.png)

>[!Hint] If the Codespace had stopped (idle timeout), select restart or reload the tab and wait till it loads completely. It should take just a minute or so this time.

>[!Hint] If the FTK extension is not installed, call a proctor to ask for help installing it manually.

<br/>

## Validate Environment

1. [] Open a terminal (**Terminal → New Terminal**).

1. [] Copy and paste each command below in the terminal to verify commandline tools are installed:

   ++az version++

   ++azd version++

   ++python --version++


## Reset the baseline

The _.foundry/_ folder contains state from previous Foundry skills runs. Run these commands to clear any stale state so you start at the same intentionally under-optimized prompt as everyone else:

1. [] Run this command in the terminal to remove stale folders. 

   +++rm -rf zava/src/zava-travel-concierge/.foundry+++

1. [] Run this command to reset instructions.

   ++bash zava/src/zava-travel-concierge/scripts/reset-instructions.sh++

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

===

# Setup Codespaces Environment

We will be using a **code-first** approach to run the observability loop for agent optimization. To do this, we need to authenticate with Azure (to access our Foundry project) and setup our local environment variables (for code-first access).

>[!Hint] If you see a popup anytime asking "Would you like to install Azure skills?" - go ahead and click the Install button.

## Sign in with **az**

The Azure CLI is used to authenticate with Azure and provide the default credentials needed for code-first development.

1. [] Open a new terminal in VS Code. _You can also type "clear" to clear output in the existing terminal_.

1. [] Copy this command and run it.

   ++az login --use-device-code++

1. [] Follow the instructions shown by opening the verification URL and entering the code provided. Complete the authentication flow with existing login. (_If you need to sign in again, use the credentials from the **Resources** tab in your instructions panel_)

1. [] Close the auth window and return to the VS Code terminal. Select the default subscription to complete the flow.

1. [] Return to the Codespaces terminal. When prompted, select the default subscription. You are now logged in.

## Sign in with **azd**

The Azure Developer CLI was used to provision our infrastructure. We will need it to retrieve and refresh our environment variables.

1. [] Return to the VS Code terminal.

1. [] Copy this command and run it.

   ++azd auth login --use-device-code++

1. [] Follow instructions to complete the authentication flow.


## Setup **.env** in Codespaces

We can now use _azd_ to setup our local environment variables.


1. [] Return to the VS Code terminal. _Use "clear" to clear terminal output before you begin_.

1. [] Copy this command and run it.

   +++bash scripts/discover-env.sh+++

1. [] You will be prompted for the resource group name. Switch to the Azure portal tab and copy the name you see 

   ![The Azure portal resource group overview with the rg-lab540 resource group name highlighted for copying](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-02-resource-group.png)

1. [] Return to the VS Code terminal and paste that as response and wait for script to finish.

>[!Alert] If you try to copy-paste the value into the terminal, you will get a pop-up asking permission to **read from and write to the clipboard**. Select **Allow** — you will need this for future copy-paste actions.

1. [] Verify that a **.env** was setup with all required parameters filled in.

   ![The .env file open in VS Code with AZURE_RESOURCE_GROUP filled in, and the terminal showing discover-env.sh reporting that all environment variables are set](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-02-env.png)

>[!Knowledge] This *.env* will be used by GitHub Copilot in a subsequent step to establish our *.azure* configuration for the Azure Developer CLI tooling.

---

> ✅ **Success:** you're signed in to Azure with both **az** and **azd**.

===

# Activate Copilot

You'll drive the optimize loop by talking to **GitHub Copilot**, which uses the
**Foundry MCP** and the **microsoft-foundry** skill to do the work.

1. [] Open **Copilot Chat** (Ctrl+Alt+I). This opens a side panel in your VS Code view.

1. [] Click the "+" button and select **Agent** mode (should be default)
1. [] Say hello to confirm it's responding - wait till it's ready:

   +++Hello!+++

   ![Copilot Chat after saying hello, showing the MCP authentication required prompt for the Foundry MCP server with an Authenticate button](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-copilot-hello.png)


>[!Alert] If GitHub Copilot execution itself fails for any reason, raise your hand and ask a proctor for help.



## Enable Foundry MCP Server

1. [] When you say hello, you will be prompted to authenticate with the Foundry MCP server as shown above.

1. [] Click the button to complete the flow using the same Azure credential as before. Close that dialog when prompted and return to GitHub Codespaces to continue.

Your Copilot chat will look like this:

   ![Copilot Chat after authenticating, replying to hello with a summary of how it can help with the repository](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-mcp-activation.png)

>[!Hint] If you did not see the Authenticate button, or missed responding to it, you can do so manually:
> First, ensure the Foundry Toolkit Extension is installed. Then, use the Command Palette and search for "MCP: List Servers". It should show the _microsoft foundry_ server option listed with status (Running or Stopped). If "Stopped" just click on it and select the "Start Server" option to trigger the auth flow.


## Select Chat Model

Pick a good model to use with GitHub Copilot to ensure the skills run correctly.

1. [] Set the chat **model** to **Claude Sonnet 5.5**.

   ![The Copilot Chat model picker open with the cursor on Claude Sonnet 5.5](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-open-copilot-chat.png)

1. [] **Speed things up.** Below the Copilot Chat input box, select **Default permissions.** Set it to **Allow all**. Click **Enable** in the pop-up dialog. This allows Copilot to run tool calls without asking for confirmation each time. *If you start a new Copilot session, you will need to repeat this action to change the default*.

   ![The Copilot Chat permissions menu open below the input box, showing Manual, Assisted, and Allow all options](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-bypass-approvals.png)


## Use Copilot To Recreate **.azure**

Our infrastructure was _pre-provisioned_ by the Azure Developer CLI (azd) outside codespaces. We need to restore the _.azure_ environment information that would have existed if we had provisioned it manually. GitHub Copilot can help us restore it.

- [] Copy the prompt below into the Copilot chat window

++I just recreated the .env file for this project. I previously deployed my agent to this resource group from the zava/ folder Use "azd init" and "azd ai agent init --project-id" to refresh the "zava/.azure/" folder from my azd provisioned project. Set ENABLE_CAPABILITY_HOST="false" and ENABLE_HOSTED_AGENTS="true". Make sure these variables are also defined: AZURE_SUBSCRIPTION_ID, AZURE_TENANT_ID,  AZURE_AI_PROJECT_NAME, AZURE_AI_PROJECT_ID, AZURE_AI_PROJECT_ENDPOINT, AZURE_AI_PROJECT_ACR_CONNECTION_NAME,  AZURE_AI_FOUNDRY_PROJECT_ID, FOUNDRY_PROJECT_ENDPOINT, AZURE_ENV_NAME, AZURE_LOCATION, AZURE_OPENAI_ENDPOINT, and AZURE_RESOURCE_GROUP++


![The .azure recreation prompt pasted into the Copilot Chat input box with Claude Sonnet 5.5 and Allow all selected](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-azure-prompt.png)

- [] Verify that the **zava/.azure** folder is created and that a subfolder exists for the **rg-lab540-XXX** environment for your deployed project.

   ![The VS Code Explorer showing the new zava/.azure folder with an lab540 environment subfolder containing .env and config.json, while Copilot runs azd ai agent init](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-03-azure-created.png)

>[!Hint] If you run into any issues at any time, start by asking GitHub Copilot to debug for you. Because it has access to the Foundry MCP server and Microsoft Learn docs, it can take advantage of the latest informtion and best practices to resolve it for you.

---

> ✅ **Success:** Copilot is in Agent mode, the Foundry MCP is enabled, the model is set, and approvals are bypassed.

===

# Meet the Skill

Before you run it, take a moment to understand what the **Observe skill** does.

1. [] First check that copilot chat has the _microsoft-foundry_ skill. Type "/microsoft-" in the chat and see if it finds the skill in that list.

   ![Typing /microsoft- in Copilot Chat lists the microsoft-foundry skill in the autocomplete menu](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-04-skill-picker.png)

1. [] Ask Copilot to explain the observe skill:

   +++/microsoft-foundry Tell me about what the observe sub-skill does for agents.+++

1. [] Read the summary it gives you. It may look like this:

   ![Copilot Chat summarizing the observe sub-skill as an eval-driven optimization loop for Foundry agents](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-04-skills-summary.png)


>[!Alert] Note that these skills are constantly updated. If a missing dependency is detected (as shown above) Copilot will automatically debug and resolve it for you. _Just wait for it to complete the step_.

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

# Run the Observe Skill

Now kick off the Observe skill and let it work.

1. [] In Copilot Chat, send the activation prompt:

   ++/microsoft-foundry Use the observe subskill to evaluate my deployed zava-concierge agent++

1. [] Confirm Copilot starts the Observe workflow (you'll see it begin creating
   files and calling Foundry tools).

   ![Copilot Chat starting the Observe workflow after the /microsoft-foundry prompt, running azd extension dependency checks in the chat](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-05-start-observe.png)

---

> ✅ **Success:** the Observe skill is running against your hosted agent.

===

# Watch Skill In Action

Watch the Observe skill work. This is **code-first optimization** — the same
loop you saw in the portal, now driven from your editor.


## GitHub Copilot Session

As it runs, you'll see Copilot:

1. [] Create a **.foundry** folder with the generated evaluators and test dataset.

>[!Hint] Once the **.foundry** folder appears, open **zava/src/zava-travel-concierge/.foundry/agent-metadata.yaml**
> in the editor. Leave it open — it updates as the loop runs and gives you a
> live view of the observe loop's progress.

![The .foundry folder in the Explorer with agent-metadata.yaml open in the editor, showing the baseline evaluation suite, while Copilot runs the Observe workflow in the chat panel](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-agent-metadata.png)


1. [] Run a **baseline evaluation** of your deployed agent against that dataset.

   ![agent-metadata.yaml showing the completed baseline evaluation with a pass/fail summary per evaluator, and Copilot Chat summarizing the baseline results](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-baseline-complete.png)

1. [] Produce a set of **recommendations** based on the failures it found.

   ![Copilot Chat showing the baseline evaluator pass/fail table, failure clusters with root causes, and ranked next-step recommendations](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-recommendations.png)

It creates a plan of action and starts executing tasks to establish the baseline
evaluation results, as shown below.

![Copilot Chat creating tasks and running the baseline evaluation](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-init-tasks.png)


## Foundry Portal Assets (Optional)

Want to see the artifacts of this run? Switch to the Foundry Portal tab.

   1. [] Verify you are in the Build tab. 

   1. Click on **Data** in the sidebar. You should see ann _eval-data-xxx_ dataset uploaded by the skill.

      ![The Foundry Data page listing the eval-data dataset uploaded by the skill](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-data.png)

   1. Click on **Evaluations** in the sidebar. You should see a _dev-zava-xxx_ evaluation run in progress, initiated by the skill. _Note: You can also get to this directly from the Agent's Evaluations tab as well_.

      ![The Foundry Evaluations page showing the dev-zava-concierge-baseline-smoke run in progress](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-evaluations.png)

   1. Click through to the details view of that run. You should be able to monitor progress and see the overall metrics and detailed metrics results (once run completes). 

      ![The completed baseline evaluation run details with overall metrics for latency, tokens, task completion, coherence, and indirect attack, and per-query results below](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-run-details.png)


>[!Alert] **Let the skill run finish.** The baseline run and analysis take a few minutes.

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

   ![Copilot Chat answering that the top recommendation is to fix the seed dataset before changing the agent, explaining why and which file it proposes to edit](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-07-top-recommendation.png)

1. [] Tell Copilot to apply that fix:

   +++Apply the top recommendation and optimize the agent's instructions.+++

   ![Copilot Chat starting to apply the top recommendation by reading the optimize references and the agent's current instructions](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-07-apply-fix.png)

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

   ![Copilot Chat redeploying the hosted agent with azd deploy to create a new version, with agent-metadata.yaml open in the editor](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-08-redeploy.png)

1. [] Optionally **re-evaluate** against the same dataset to compare before and
   after.

When the loop finishes, Copilot summarizes what changed, what it fixed along the way, and offers **next steps** (e.g., roll back, fix the prompt and re-evaluate, or keep the new version). Pick one to keep iterating.

![Copilot Chat summarizing the optimize run, including deployment fixes and a decision with options to roll back, fix the prompt and re-evaluate, or keep the new version](https://raw.githubusercontent.com/LODSContent/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry-All-Branch/aiewf26-refresh-test/workshop/skillable/images/03-optimize-08-next-steps.png)

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
