# Setup your Azure subscription and Dynamics 365 for Operations environment for Microsoft Hostes Test Drives

1.	Login to Azure Portal with Admin account - https://portal.azure.com
2. Verify you are in the tenant associated with your Dynamics 365 Test Drive instance by hovering your mouse over your account icon in the upper right corner. If you are not in the correct tenant, click on the account icon to switch into the correct tenant.
 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub4.jpg)

3. 	Create an Azure AD App in Azure. AppSource will use this App to provision and deprovision the Test Drive user in your tenant.
      *    Select Azure Active Directory in the filter pane
      *    Select “App registrations” <br /> ![](https://github.com/Microsoft/AppSource/blob/master/Images/App%20Registration%20home.JPG)
      *    Click on the 'New registration' button
      *    Provide an appropriate application name <br /> ![](https://github.com/Microsoft/AppSource/blob/master/Images/Register%20App.png)
      *    Select radio button - "Account in any organization directory and personal microsoft account" under Supported account types.
      *    Click Create and wait for your app to be created.
      *    Once App created successfully. Take note of your 'Application ID' displayed from overview screen. You will need this value later when configuring your Test Drive. 
      *    Navigate to API permissions under Manage Application.
      *    Click on Add a permission button and select Microsoft Graph API. 
      *    Click on Applicatoin permission category and select Directory.Read.All and Directory.ReadWrite.All permissions. <br /> ![](https://github.com/Microsoft/AppSource/blob/master/Images/Add%20Permission.png)
      *    Click on Add permission button.
      *    Once the permission is added successfully, click on "Grant admin consent for microsoft" button under Grant consent followed by click on "Yes" button on the prompt message alert. <br /> ![](https://github.com/Microsoft/AppSource/blob/master/Images/Grant%20Permission.png)
      *    Generate a secret for the Azure AD App. Navigate to 'Certificate and secrets' under Manage Application. 
      *    Click on New client secret button under Client secrets.
      *    Provide a valid description (example - "Test Drive") and select an appropriate duration. Be aware that your Test Drive will break once this Key expires and you will need to generate and provide to AppSource a new key when this happens. 
      *    Click on Add. This should generate the Azure App Secret. Copy this value as it will be hidden as soon as you navigate away from this blade. You will need this value later when configuring your Test Drive. <br /> ![](https://github.com/Microsoft/AppSource/blob/master/Images/Add%20Secret%20Key.png)

4. Add Service Principal role to application to allow the Azure AD App to remove users from your Azure tenant. 
    * Open an Administrative-level PowerShell commmand prompt.
    * Install-Module MSOnline  (run this command if MSOnline is not installed)
    * Connect-MsolService (Will show a popup window to login. Login with newly created org tenant)
    * $applicationId = "<YOUR_APPLICATION_ID>"
    * $sp = Get-MsolServicePrincipal -AppPrincipalId $applicationId
    * Add-MsolRoleMember -RoleObjectId fe930be7-5e62-47db-91af-98c3a49a38b1 -RoleMemberObjectId $sp.ObjectId -RoleMemberType servicePrincipal <br /> ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/Connect_MsolService.PNG)
    
5. Now we need to add the above app to Dynamics 365 for operations in order to enable the app to manage users
      *    Navigate to your Dynamics 365 for Operations instance.
      *    Click on the Hamburger menu at the left top corner.
      *    Click on System Administration.
      *    Click on Azure Active Directory applications.
      *    Click on + New
      *    Enter in the Client Id of the Azure AD app that is going to perform the on-behalf-of actions.
      *    The user Id on whose behalf the actions will be performed (typically the System Admin of the instance or a user who has privileges to add other users).<br /> ![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365OperationsAddApp.png)

