# Run Out-of-Scope Prompt

Finally, send an **out-of-scope** request and watch the agent's instructions
keep it on task.

1. [] Start a new chat session in the Playground and send this prompt to get a sense for the concierge's role and instructions.

   ++what can you do?++

1. [] Now make an out-of-scope request and see if the agent can stay on task.

   ++Can you help me write a Python script?++

1. [] Confirm the concierge **politely declines** and redirects to travel
   topics instead of answering. 

   ![The concierge politely declining the out-of-scope request and redirecting to travel topics](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/02-observe-05-prompt3.png)


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
