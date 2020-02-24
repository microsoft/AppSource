**How to grant access to Microsoft Support account to your Azure Active Directory Application**

As part of onboarding process, you must have created an Azure Active Directory Application in your subscription to allow Test Drive to provision and deprovision users in your tenant. 

Since Microsoft Test drive team do not have access to review how your Azure AD application is configured and a wrong configuration could be a possible reason for a failure in Test Drive execution. Rather than scheduling a call to troublshoot issue and review the configuration, you can leverage Azure RBAC (Role Based Access Control) to grant Microsoft Test Drive developer team access to your Azure Active Directory application. This allow Microsoft Test Drive team to review the configuration and help you to understand and provide guidance on how to mitigate the issue. 

**How to grant Microsoft Test Drive developers access to your Azure Active Directory:**

1) Log into the Azure Portal (https://portal.azure.com) with an account that is the owner of the Azure Subscription the Test Drive Resources are deployed to.

**Invite the Microsoft Support user to your Azure AD with Azure B2B**

2) Navigate to 'Azure Active Directory' -> 'Users and groups' -> 'All users' 
3) Click the 'new guest user' button in the command bar
4) Enter the user email
5) Click the 'Invite' button

**Grant the Microsoft Support user access to your Azure Active Directory**

6) Navigate back to 'Azure Active Directory'
7) Click on 'App Registration' and select your Azure AD application that you have used for Test Drive.
8) Click on 'Setting' gear icon
9) Click on the 'Owner' tab under setting
10) Click on 'Add Owner' and search for the Microsoft Support user account
11) Choose the account and click on 'select' button.

These steps will allow Microsoft support user account to review your Azure Active Directory application configuration.

If you want to remove the access from Microsoft Test Drive developer team, you can remove the RBAC contributor permission granted to the user, or remove the guest user from your tenant. 

Additional information on RBAC: 
 - https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-create-custom-roles-for-internal-external-users
 - https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-what-is
