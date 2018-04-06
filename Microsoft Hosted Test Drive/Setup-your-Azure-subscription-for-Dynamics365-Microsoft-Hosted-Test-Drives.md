# Setup your Azure subscription for Dynamics 365 for Customer Engagement Test Drives

1.	Login to your Azure management portal
2.	Create a new tenant in AAD (if not available already)
      *    Navigate to https://portal.azure.com
      *    Click on + New ->  (Search for Azure Active Directory)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub1.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub2.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub3.jpg)

3. 	Register an application in azure. We will use this application to perform operations on your Dynamics 365 instance including adding and removing users etc. 

      *    Navigate to the newly created directory or already existing directory and select Azure Active directory in the filter pane.
      *    Search “App registrations” and click on “Add”
      *    Provide an application name.
      *    Provide an application name.
      *    Select the Type of as “Web app/ API”
      *    Provide any sign-on URL - Ex- http://localhost (It can be changed or updated as per need later on)
      *    Click Create. It will take a while to create the application. Wait for sometime.
      *    Click on "Settings" to configure the application.
      *    Go to  Properties -> Set the application as multi-tenant and hit Save. Get more details about Multi-Tenant applicaton using [link](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application).
      *    Generate a client secret to access the application. Under keys, add a Key Description, set the duration to two years or as appropriate. Do remember to update this before the key expires, else your test drives will be broken. 
      *    Click Save. This should generate the ClientSecret. Copy this value as it will be hidden afterwards. Generate a new one in case you lost the current one. 
      *    Update the Required Permissions for the application. By default the application will have "Windows Azure Active Directory".
      *    Click Add followed by Select an API
      *    Find Microsoft Graph from the available list of API's and press Select
      *    Select permissions for: "Read and write directory data", "Read directory data" under Application Permission and press Done.
      *    Click on **"Grant Permissions"** to sync the added/updated permission.
      *    Hit Save.

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub4.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub5.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub6.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/TestDrive_GrantPermission.png)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/TestDriveGrantPermissions.PNG)

4. Make the newly created app a “Company Administrator”.
    *	Install AzureAD powershell extension from [here](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)
    *	Type below commands in AzureAD Powershell to make app company administrator
        *	" Connect-MsolService "  (login screen comes up with this command and use administrator credentials of tenant)
        *	" Get-MsolServicePrincipal " (Search for the newly created app name and copy the ObjectId)
        *	" Add-MsolRoleMember -RoleName 'Company Administrator' -RoleMemberType ServicePrincipal -RoleMemberObjectId ‘ObjectId’ " (Replace ‘ObjectId’ with ObjectId copied in above step)
        
![](https://github.com/Microsoft/AppSource/blob/master/Images/Financials/SetupAzureFinancialsAADPowerShell.png)
        
![](https://github.com/Microsoft/AppSource/blob/master/Images/Financials/SetupAzureFinancialsAADPowerShell2.PNG)

5. Add the above created application as an application user to CRM instance
     * Add a new user or take an existing user from Azure AD. Copy the username value
     * Login to CRM instance and navigate to Setting -> Security -> Users
     * Change the view to Application Users
     * Add a new User (Ensure the form is Application user form)
     * Enter the same username in Primary Email and User Name fields. Add the Azure ApplicationId in Application ID field. 
     * Give any full name.
     * Hit Save. 
     * Other values like Azure AD Object Id and Application ID URI will get populated automatically as sync process.
     * Click on Manage roles
     * Assign appropriate role which should have assign and delete role privileges. 

![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/ApplicationUser_form_CRM.PNG)

6. Follow the instructions found [here](https://cloudpartner.azure.com/#documentation/logic-app-test-drive) to publish the app in AppSource. If you are not able to access the above link, you need to submit a request [here](https://appsource.microsoft.com/en-us/partners/list-an-app) to publish your application. Once we review the request, you will be granted access to start the publish process. 
