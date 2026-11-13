# Setup Tab 3: GitHub Codespaces

We will use **GitHub Codespace** as the development environment for this lab. It takes a few minutes to load - so we will start the process in this step and let it complete in the background.


## Sign in to the Skillable GitHub org

1. Open a new browser tab and navigate to  
   +++https://github.com/enterprises/skillable-events/sso+++

   ![The Single sign-on to Skillable Events page with the green Continue button](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-04-github-sso.png)

1. [] Click **Continue**. You’ll be authenticated with the same lab credentials. 

>[!Alert] If you receive a **404** error, wait for several minutes and then try again. This is likely because the GitHub Enterprise license is still being activated.
 
## Launch the Codespace

1. [] In the same tab, copy-paste this lab repo link and click to navigate to it: ++https://aka.ms/build26/lab540/skillable++
1. [] Click the green **Code** button, select the **Codespaces** tab, and click the **Create codespace on main** button as shown.

   ![The Code button's Codespaces tab showing the Creating codespace button after it is selected](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-04-create-codespace.png)

A new browser tab should open with a VS Code session loading. This is your GitHub Codespaces tab - your browser should now have four tabs as shown in the image.

![A new browser tab with VS Code in the browser showing Opening Remote and Building codespace while the Codespace starts](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-04-codespace-opening.png)

>[!Alert] **Don't wait for the page to load.** GitHub Codespaces can take several minutes to build. Leave this tab open and move to the next step. We'll come back here later in the lab to check if it is ready.

<br/>

---

> ✅ **Success:**  Your GitHub Codespaces environment is loading.
>
> 🏁 **Stage 1 complete.** You have browser tabs open to three locations — Azure Portal, Foundry Portal, and GitHub Codespaces. While it builds, let's explore the hosted agent and Foundry's built-in observability.
