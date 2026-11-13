# Watch Skill In Action

Watch the Observe skill work. This is **code-first optimization** — the same
loop you saw in the portal, now driven from your editor.

>[!Note] The Copilot run may occasionally **stop and ask for your input**. Pick the option that feels reasonable — there are no wrong answers. If you prefer, ask Copilot to explain the options or make a recommendation. This reflects a realistic skill run.

## GitHub Copilot Session

As it runs, you'll see Copilot:

1. [] Create a **.foundry** folder with the generated evaluators and test dataset.

>[!Hint] Once the **.foundry** folder appears, open **zava/src/zava-travel-concierge/.foundry/agent-metadata.yaml**
> in the editor. Leave it open — it updates as the loop runs and gives you a
> live view of the observe loop's progress.

![The .foundry folder in the Explorer with agent-metadata.yaml open in the editor, showing the baseline evaluation suite, while Copilot runs the Observe workflow in the chat panel](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-agent-metadata.png)


1. [] Run a **baseline evaluation** of your deployed agent against that dataset.

   ![agent-metadata.yaml showing the completed baseline evaluation with a pass/fail summary per evaluator, and Copilot Chat summarizing the baseline results](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-baseline-complete.png)

1. [] Produce a set of **recommendations** based on the failures it found.

   ![Copilot Chat showing the baseline evaluator pass/fail table, failure clusters with root causes, and ranked next-step recommendations](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-recommendations.png)

It creates a plan of action and starts executing tasks to establish the baseline evaluation results. Just watch the Copilot session to see it create and execute a plan.

## Foundry Portal Assets (Optional)

Want to see the artifacts of this run? Switch to the Foundry Portal tab.

   1. [] Verify you are in the Build tab. 

   1. Click on **Data** in the sidebar. You should see an _eval-data-xxx_ dataset uploaded by the skill.

      ![The Foundry Data page listing the eval-data dataset uploaded by the skill](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-data.png)

   1. Click on **Evaluations** in the sidebar. You should see a _dev-zava-xxx_ evaluation run in progress, initiated by the skill. _Note: You can also get to this directly from the Agent's Evaluations tab as well_.

      ![The Foundry Evaluations page showing the dev-zava-concierge-baseline-smoke run in progress](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-evaluations.png)

   1. Click through to the details view of that run. You should be able to monitor progress and see the overall metrics and detailed metrics results (once run completes). 

      ![The completed baseline evaluation run details with overall metrics for latency, tokens, task completion, coherence, and indirect attack, and per-query results below](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-06-portal-run-details.png)


>[!Alert] **Let the skill run finish.** The baseline run and analysis take a few minutes.

> Watch the updates stream in and **wait until the recommendations appear**
> before moving on.

---

> ✅ **Success:** you just saw **code-first optimization** — a baseline
> evaluation and recommendations generated from your own editor.
