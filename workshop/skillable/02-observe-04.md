# Run Complex Prompt

Now send a multi-part request that makes the concierge coordinate all three
specialists.

1. [] Return to the Playground tab. Use the "+" icon (next to Metrics) to start a new chat.

1. [] Click the "→" on Logstream pane to close it. You should see just the playground panel in focus.

1. [] Copy this prompt into the chat and submit the request:

   ++Plan a trip from Chicago to Rome for the first two weeks of November. I need flights, a hotel, and a car rental.++

1. [] Wait for the concierge to compose the full itinerary. Note that the response now includes flight, hotel, and car results! All three specialists were called before composing the final answer.

   ![The prompt 2 itinerary response combining flights, hotel, and car rental](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-prompt2.png)

<br/>

## Explore Trace Viewer

What happened when you made the request? We can use traces to look under the hood and see how the request-response flow occurred,

1. [] Select **Traces**. Then switch to the **Conversation view** tab.

   ![The Traces tab in Conversation view listing recent conversation IDs with duration, tokens, and estimated cost](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-conversation-view.png)

1. [] Locate the recorded conversation and select the **Conversation ID.**. You should see this trace detail view with the **Trajectories** tab selected.   

   ![The trace detail view with the Trajectories tab selected, highlighting the Play controls and the span, chat call, tool call, time, and token metrics](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-trace-detail.png)

1. [] Check the metrics (top-right) for chat calls, tool calls, tokens, time, and **spans**. And note the Play button that gives you a time-lapse replay of traces. We'll try that next.

1. [] Switch to the **User View** tab. This shows you the chat conversation view of the traces. Click the **Span tree** button to expand that pane. You should now see both the user view and the trajectory view side by side. _Optional: Use the toggle on the other size to close the Metadata pane to focus on traces alone_.

   ![The User view tab during replay, with the Span tree expand toggle highlighted on the left and invoke_agent span metadata on the right](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view.png)

1. [] Click **Play**. You'll see a time-based replay showing which requests went to each agent, when, and how the final response was composed — giving you an intuitive sense of per-agent latency. Each agent's requests and responses stream in parallel before being merged into one reply. **Notice how the timeline color matches the step in the trajectory, and correlates to the state of the chat output**.

   ![The User view replaying the conversation with the Span tree expanded on the left, highlighting the active span as the agent responses stream in on the right](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-user-view-replay.png)

1. [] (Optional) Click the **Graph View** tab, then **Play**. This shows the trace as a node-and-edge graph. Each agent and tool is a node, and each edge is a call or handoff between them. As the replay runs, nodes light up in order, so you can see how the concierge connects to the flight, hotel, and car-rental agents and which paths ran during this turn.

   ![The Graph view replaying the trace, with the active span highlighted in the Span tree and as a node in the graph](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-04-graph-view.png)


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
