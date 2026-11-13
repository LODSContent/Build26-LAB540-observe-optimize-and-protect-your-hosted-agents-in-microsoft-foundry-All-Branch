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

   ![The Azure portal resource group overview with the rg-lab540 resource group name highlighted for copying](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-02-resource-group.png)

1. [] Return to the VS Code terminal and paste that as response and wait for script to finish.

>[!Alert] If you try to copy-paste the value into the terminal, you will get a pop-up asking permission to **read from and write to the clipboard**. Select **Allow** — you will need this for future copy-paste actions.

1. [] Verify that a **.env** was setup with all required parameters filled in.

   ![The .env file open in VS Code with AZURE_RESOURCE_GROUP filled in, and the terminal showing discover-env.sh reporting that all environment variables are set](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/03-optimize-02-env.png)

>[!Knowledge] This *.env* will be used by GitHub Copilot in a subsequent step to establish our *.azure* configuration for the Azure Developer CLI tooling.

---

> ✅ **Success:** you're signed in to Azure with both **az** and **azd**.
