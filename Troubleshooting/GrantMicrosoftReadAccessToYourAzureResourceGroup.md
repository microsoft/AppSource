If your Dynamics 365 Test Drive is deployed to your Azure subscription, but not working correctly, you may need to engage Microsoft Test Drive developer team for assistance. 

Since the Azure Functions and Azure Logic Apps used for Test Drive are hosted in your own Azure Subscription, Microsoft Test Drive developers do not have access to review how your Test Drive resources are configured, or view the logs from your Logic App or Function.

Rather than having to manually retrieve the logs and Azure Function / Azure Logic App configuration yourself to send to Microsoft, or having to schedule a call with Microsoft Test Drive developers to troubleshoot the issue, you can leverage Azure RBAC (Role Based Access Control) to grant Microsoft Test Drive developer team read-only access to your Azure Resource Group that contains your Test Drive resources. This allows Microsoft Test Drive developer team to easily view the configuration of your Test Drive resources (Azure Function and Azure Logic App) and review execution logs to help understand and provide guidance on how to mitigate the issue.

**How to grant Microsoft Test Drive developers read access to your Azure Resource Group:**

1) Log into the Azure Portal (https://portal.azure.com) with an account that is the owner of the Azure Subscription the Test Drive Resources are deployed to.

**Invite the Microsoft Support user to your Azure AD with Azure B2B**

2) Navigate to 'Azure Active Directory' -> 'Users and groups' -> 'All users' 
3) Click the 'new guest user' button in the command bar
4) Enter the email of the following user: support@dynamicstestdrive.onmicrosoft.com
5) Click the 'Invite' button

**Grant the Microsoft Support user read-only access to your Azure Resource Group**

6) Navigate to 'Resource Groups'
7) Click on the Resource Group your Test Drive resources (Azure Function and Azure Logic Apps) are deployed into.
8) Click on 'Access control (IAM)'
9) Click on the 'Add' button on the command bar
10) Set 'Role' to 'Reader'
11) Set 'Assign access to' to 'Azure AD user, group, or application'
12) In the 'select' field, search for 'support@dynamicstestdrive.onmicrosoft.com' and select the AD User
13) Click the 'Save' button

These steps will grant Microsoft Test Drive developer team read-only access to all the Azure Resources you have deployed in the selected Resource Group. 

If you want to remove the read-only access from Microsoft Test Drive developer team, you can remove the RBAC read permission granted to the user, or remove the support@dynamicstestdrive.onmicrosoft.com guest user from your tenant. 

Additional information on RBAC: 
 - https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-create-custom-roles-for-internal-external-users
 - https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-what-is
