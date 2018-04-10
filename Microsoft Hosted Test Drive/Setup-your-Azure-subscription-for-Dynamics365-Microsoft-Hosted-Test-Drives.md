# Setup your Azure subscription for Dynamics 365 for Customer Engagement Microsoft Hosted Test Drives

1.	Login to Azure Portal - https://portal.azure.com
2. Verify you are in the tenant associated with your Dynamics 365 Test Drive instance by hovering your mouse over your account icon in the upper right corner. If you are not in the correct tenant, click on the account icon to switch into the correct tenant.
 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub4.jpg)

3. 	Create an Azure AD App in Azure. AppSource will use this App to provision and deprovision the Test Drive user in your tenant.
      *    Select Azure Active Directory in the filter pane
      *    Select “App registrations” ![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub5.jpg)
      *    Click on the 'New application registration' button
      *    Provide an application name
      *    Select the Type of as “Web app/ API”
      *    Provide any sign-on URL - Ex- https://www.bing.com (This URL is not used for Test Drive and can be updated later if needed)
      *    Click Create and wait for your app to be created.
      *    Click on "Settings" to configure the application.
      *    Go to  Properties -> Set the 'multi-tenanted' field to 'Yes' and click save. For more information about Multi-Tenant applicaton see [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application). 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub6.jpg)
      *    Take note of your 'Application ID' displayed in the properties section. You will need this value later when configuring your Test Drive.
      *    Generate a secret for the Azure AD App. Navigate to 'Keys' in the settings menu. In the 'Passwords' section, enter a Key Description (Example "Test Drive") and set the duration to two years or as appropriate. Be aware that your Test Drive will break once this Key expires and you will need to generate and provide to AppSource a new key when this happens. 
      *    Click Save. This should generate the Azure App Secret. Copy this value as it will be hidden as soon as you navigate away from this page. You will need this value later when configuring your Test Drive.
      *    Navigate to 'Required permissions' in the settings menu. 
      *    By default the App will already have "Windows Azure Active Directory" permissions. Do not modify this. 
      *    Click 'Add' button and then 'Select an API'
      *    Select 'Microsoft Graph' from the list and click 'Select'
      *    Select "Read and write directory data" and "Read directory data" from the list and click 'select' 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/TestDrive_GrantPermission.png) 
      *    Click the 'done' button.
      *    Click the **"Grant Permissions"** button and click 'yes'. 

![](https://github.com/Azure/AzureTestDrive/raw/master/AzureTestDriveImages/TestDriveGrantPermissions.PNG)

4. Add Service Principal role to application to allow the Azure AD App to remove users from your Azure tenant. 
    * Install-Module MSOnline  (run this command if MSOnline is not installed)
    * Connect-MsolService (Will show a popup window to login. Login with newly created org tenant)
    * $applicationId = "<YOUR_APPLICATION_ID>"
    * $sp = Get-MsolServicePrincipal -AppPrincipalId $applicationId
    * Add-MsolRoleMember -RoleObjectId fe930be7-5e62-47db-91af-98c3a49a38b1 -RoleMemberObjectId $sp.ObjectId -RoleMemberType servicePrincipal
 
 ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/Connect_MsolService.PNG)

5. Add the above created Azure App as an application user to your Test Drive CRM instance. 
     * Add a new user or take an existing user from Azure AD. Copy the username value
     * Login to CRM instance and navigate to Setting -> Security -> Users
     * Change the view to Application Users
     * Add a new User (Ensure the form is Application user form)
     * Enter the same username in Primary Email and User Name fields. Add the Azure ApplicationId in Application ID field. 
     * Give any full name.
     * Hit Save. 
     * Click on Manage roles
     * Assign custom security role which contains assign role and delete role privileges. 
     * Also assign the application user the custom security role you have created for your Test Drive
     
![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/ApplicationUser_form_CRM.PNG)

6. Publish your offer in Cloud Partner portal. Follow instruction in [link](https://github.com/Microsoft/AppSource/blob/patch-1/Microsoft%20Hosted%20Test%20Drive/Configure_TestDrive_CloudPartner_Portal.md). 
