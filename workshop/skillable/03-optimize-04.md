# Meet the Skill

Before you run it, take a moment to understand what the **Observe skill** does.

1. [] First check that Copilot Chat has the _microsoft-foundry_ skill. Type "/microsoft-" in the chat and see if it finds the skill in that list.

   ![Typing /microsoft- in Copilot Chat lists the microsoft-foundry skill in the autocomplete menu](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-04-skill-picker.png)

1. [] Ask Copilot to explain the observe skill:

   +++/microsoft-foundry Tell me about what the observe sub-skill does for agents.+++

1. [] Read the summary it gives you. It may look like this:

   ![Copilot Chat summarizing the observe sub-skill as an eval-driven optimization loop for Foundry agents](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-04-skills-summary.png)


>[!Alert] Note that these skills are constantly updated. If a missing dependency is detected (as shown above) Copilot will automatically debug and resolve it for you. _Just wait for it to complete the step_.

>[!Knowledge] The **microsoft-foundry Observe skill** automates the evaluation
> lifecycle for your hosted agent. In one workflow it:
>
> 1. **Generates** a test dataset tailored to your agent's capabilities.
> 2. **Evaluates** the deployed agent against that dataset with built-in
>    evaluators.
> 3. **Analyzes** the failures and patterns in the results.
> 4. **Recommends** specific optimizations to improve quality.

>[!Hint] **Foundry and azd are evolving rapidly**, so Copilot may detect dependency or version issues as it works. If it offers you options to fix them, ask:
>
> +++What do you recommend?+++
>
> Then tell it to take that action. This way Copilot reasons about the latest changes and adapts automatically, keeping the lab working as the tools evolve.

---

> ✅ **Success:** you understand what the Observe skill will do before you run it.
