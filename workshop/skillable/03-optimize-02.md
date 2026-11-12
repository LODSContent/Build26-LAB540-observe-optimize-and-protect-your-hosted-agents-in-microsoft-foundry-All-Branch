# Sign in to Azure

The optimize loop talks to your Foundry project from code, so sign in with both
the Azure CLI (**az**) and the Azure Developer CLI (**azd**). You'll use **device
code** sign-in to keep things simple inside the Codespace.

## Sign in with **az**

1. [] Copy this command and run it in the terminal to clear it:

   ++clear++

1. [] Now copy this command and run it:

   ++az login --use-device-code++

1. [] Open the verification URL, enter the code shown. You will be taken to a screen to authenticate with your subscription.

1. [] Select the subscription you logged into earlier. (If needed sign in again with these credentials)
   **Username:** +++@lab.CloudPortalCredential(User1).Username+++
   **Password (TAP):** +++@lab.CloudPortalCredential(User1).AccessToken+++

1. [] Click "Approve" in the pop-up dialog, then close the dialog window when prompted.

1. [] Return to the Codespaces terminal. When prompted, select the default subscription.

## Sign in with **azd**

1. [] In the terminal, copy and run this command:

   ++azd auth login --use-device-code++

1. [] Press enter to complete the same device-code sign-in flow.

<!-- TODO screenshot: device code sign-in prompt -->

## Setup **.env** in Codespaces

Run the script to automatically have your **.env** created from the deployed infrastructure.

1. [] Copy this command and run it to clear the terminal:

   ++clear++

1. [] Copy this command to the terminal to execute it:  

   +++bash scripts/discover-env.sh+++

1. [] You will be prompted for the name of the resource group to use. 

   - Visit the Azure portal tab and copy the resource group name. It should start with **rg-lab540-**.
   - Return to the Codespaces tab and paste this where prompted.

>[!Alert] If you try to copy-paste the value into the terminal, you will get a pop-up asking permission to **read from and write to the clipboard**. Select **Allow** — you will need this for future copy-paste actions.

1. Wait till the script is complete. Verify that a **.env** was setup with all required parameters filled in.

>[!Knowledge] This *.env* will be used by GitHub Copilot in a subsequent step to establish our *.azure* configuration for the Azure Developer CLI tooling.

---

> ✅ **Success:** you're signed in to Azure with both **az** and **azd**.
