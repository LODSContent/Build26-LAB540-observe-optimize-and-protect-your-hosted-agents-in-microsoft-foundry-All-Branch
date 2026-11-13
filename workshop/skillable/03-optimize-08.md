# Optimize & Redeploy

Watch Copilot apply the fix and push a new version of your agent — the loop
closing itself.

As it runs, you'll see Copilot:

1. [] Update the agent's **instructions** with the optimized version.
1. [] **Redeploy** the hosted agent (rebuild + push, then publish a new
   revision).

   ![Copilot Chat redeploying the hosted agent with azd deploy to create a new version, with agent-metadata.yaml open in the editor](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-08-redeploy.png)

1. [] Optionally **re-evaluate** against the same dataset to compare before and
   after.

When the loop finishes, Copilot summarizes what changed, what it fixed along the way, and offers **next steps** (e.g., roll back, fix the prompt and re-evaluate, or keep the new version). Pick one to keep iterating.

![Copilot Chat summarizing the optimize run, including deployment fixes and a decision with options to roll back, fix the prompt and re-evaluate, or keep the new version](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-08-next-steps.png)

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
