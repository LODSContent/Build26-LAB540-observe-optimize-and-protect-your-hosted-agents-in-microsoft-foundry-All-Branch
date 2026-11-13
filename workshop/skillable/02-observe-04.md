# Run Complex Prompt

Now send a multi-part request that makes the concierge coordinate all three
specialists.

1. [] Click the Playground tab to return to playground.
   - Click "+" (next to Metrics) to start a new chat.
   - Click the "→" on Logstream pane to close it.
   - You now see just the playground panel in focus.

1. [] In the playground, send this prompt:

   ++Plan a trip from Chicago to Rome for the first two weeks of November. I need flights, a hotel, and a car rental.++

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
   requests and responses stream in parallel before being merged into one reply. (Click the → to expand the Span tree view to the left if you want to see replay across both user and trajectory views)

   ![The User View tab showing a time-based replay of requests to each agent](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view.png)


1. [] (Optional) Click the **Graph View** tab, then **Play**. This shows the
   trace as a node-and-edge graph. Each agent and tool is a node, and each edge
   is a call or handoff between them. As the replay runs, nodes light up in
   order, so you can see how the concierge connects to the flight, hotel, and
   car-rental agents and which paths ran during this turn.


1. [] Click the "X" to close the trace view dialog. Then click "Playground" to return to the playground view for the next step.

>[!Knowledge] **Trajectory, User and Graph Views** are complementary lenses on the
> same trace. You can switch views in the middle of a replay (or pause, switch, resume if preferred) to see how a specific moment appears in each for debugging etc..

- The **Trajectory view** exposes the agent's internal orchestration how the concierge decomposed and delegated — so you can pinpoint *which* agent or tool call went wrong. Replays also give you an intuitive sense for latency by making you "see" delays between actions, or time spent in executing a tool call etc. 
- The **User View** replays the interaction on a timeline, showing *when* each request fired, so you can spot the step responsible for latency. It also makes it easier to see how agents are streaming responses in parallel.
- The **Graph View** maps the trace as a topology of agents and tools connected by calls and handoffs, so you can quickly see *who talked to whom* and spot unexpected, missing, or repeated paths in the orchestration.
- Together they let you debug correctness and diagnose performance from a single captured trace — no re-running required.

---

> ✅ **Success:** you've inspected a multi-agent conversation trace through both
> the Trajectory and User View lenses.
