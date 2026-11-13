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



1. **Optional:** Want to see the artifacts of this run? Switch to the Foundry Portal tab.

   1. [] Verify you are in the Build tab. 
   1. Click on **Data** in the sidebar. You should see ann _eval-data-xxx_ dataset uploaded by the skill.
   1. Click on **Evaluations** in the sidebar. You should see a _dev-zava-xxx_ evaluation run in progress, initiated by the skill. _Note: You can also get to this directly from the Agent's Evaluations tab as well_.
   1. Click through to the details view of that run. You should be able to monitor progress and see the overall metrics and detailed metrics results (once run completes). 


>[!Alert] **Let it finish.** The baseline run and analysis take a few minutes.
> Watch the updates stream in and **wait until the recommendations appear**
> before moving on.

---

> ✅ **Success:** you just saw **code-first optimization** — a baseline
> evaluation and recommendations generated from your own editor.
