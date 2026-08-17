***This solution will trigger a notification to Microsoft 365 via a Teams Message when your license consumption exceeds 80%. A notification will be received for each type of license.***


![Alt text](https://github.com/MSPFE2019/m365licensenotification/blob/main/M365License.png)

Requirements:
- Power Automate Per User License for account running the flow
- Ablitiy to create Azue App Registration

**Step-by-Step Guide to App Registration**

Here is a more detailed step-by-step guide to help you register an application on Azure AD.

**Step 1: Sign in to your Azure Account**

Sign in to your Azure account and go to the Azure portal.

**Step 2: Navigate to App Registrations**

Go to Microsoft Entra ID (formerly Azure Active Directory), then select App registrations.

**Step 3: Register a new application**

Click on the "+ New registration" button at the top. You'll need to provide the following details:

- **Name**: Enter a meaningful application name that will be displayed to users.
- **Supported account types**: Select which accounts you want your application to support.
- **Redirect URI (optional)**: If applicable, enter the redirect URI where Azure AD will send the app responses.

**Step 4: Set Permissions**

You will need to set the right permissions for the API you are using. In this case, go to "API permissions" -> "Add a permission" -> "Microsoft Graph" -> "Application permissions", and select Organization.Read.All. Don't forget to grant admin consent for these permissions.

**Step 5: Generate a New Client Secret**

Navigate to "Certificates & secrets" and click on "+ New client secret". Give it a name, choose an expiry period, and click "Add". Copy this secret to a secure location, as you'll need it later.

> ⚠️ **Secret rotation:** Client secrets expire. Set a calendar reminder to rotate the secret **before** expiry. When rotating, update the corresponding environment variable or flow connection with the new secret value before the old one expires to avoid flow failures. Use the shortest expiry period your operations allow. For production scenarios, prefer **certificate credentials** over client secrets. See [Add a client secret – Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#add-a-client-secret).

**Step 6: Gather Important Information**

Make sure to note down the following important details:

- **Application (client) ID**: You can find this on the "Overview" page of your app registration.
- **Directory (tenant) ID**: This can also be found on the "Overview" page.

**Step 7: Get Group ID of Office365 Group**

For the Microsoft 365 group list of people who will get the notification, you'll need the Group ID. This can be found in the Microsoft Entra ID portal (formerly Azure Active Directory) at [https://entra.microsoft.com](https://entra.microsoft.com) under **Groups**. Select the group and find the **Object ID** field.

**Step 8: Download and Import M365 License Solution to Power Apps**



[Download Solution](https://github.com/MSPFE2019/m365licensenotification/blob/main/M365LicenseNotification_1_0_0_3.zip)

Follow these steps to import the M365 License Solution:

1. Sign into Power Apps.
2. Select "Solutions" from the left navigation. If you can't find it, select "…More" and then find the item.
3. Click on "Import" at the top.
4. Click on "Browse" and locate the compressed (.zip or .cab) file that contains the solution you want to import.
5. Click on "Next".
6. If prompted, select the connections you want. If a connection does not already exist, create a new one. Click on "Next".
7. If prompted, enter the environment variables. You will not see this screen if value(s) are already present in your solution or the target environment.
8. Click on "Import".

That's it! You've successfully registered an application in Microsoft Entra ID and imported a solution into Power Apps.

---

> **Supported Cloud:** Commercial (GCC environments — verify the HTTP connector and Graph API availability at [Power Platform for US Government](https://learn.microsoft.com/en-us/power-platform/admin/powerapps-us-government)).  
> **Last validated:** 2026-08-17. Confirm current Microsoft Entra ID app registration steps in [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).
