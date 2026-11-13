# Setup Tab 1: Azure Portal

The **Azure Portal** is where you see the details of the pre-provisioned resources for this lab.

1. Open a new browser tab and navigate to +++https://portal.azure.com+++

1. [] Sign in with these lab credentials:

   - **Username:** +++@lab.CloudPortalCredential(User1).Username+++
   - **TAP:** +++@lab.CloudPortalCredential(User1).AccessToken+++

1. [] If prompted to save the password, **dismiss** it.
1. [] If prompted to stay signed in, check **Don't show this again** and select **Yes**.
1. [] Dismiss any other Edge popups you see.

You should see an Azure portal page like this:

   ![Azure portal home](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-02-azure-portal-home.png)

1. [] Select **Resource groups** in the portal to view the list of resource
   groups. Maximize **Edge** if you do not see the **Resource groups** option.
1. [] Confirm you see **two** resource groups, one of which starts with
   **rg-lab540**.

   ![The Resource groups page listing ResourceGroup1 and an rg-lab540 resource group](https://raw.githubusercontent.com/nitya/Build26-LAB540-observe-optimize-and-protect-your-hosted-agents-in-microsoft-foundry/lods-aiewf26-refresh-test/workshop/skillable/images/01-setup-02-resource-groups.png)

<br/>

>[!Alert] If you do **not** see the resource group starting with **rg-lab540**, raise your hand and ask a proctor for help. This is likely a cold-start problem where provisioning hasn't finished yet.

---

> ✅ **Success:** Your Azure portal tab is ready and the resource group was provisioned.
