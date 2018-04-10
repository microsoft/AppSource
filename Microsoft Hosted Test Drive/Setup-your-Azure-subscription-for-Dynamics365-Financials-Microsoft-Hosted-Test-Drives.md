# Setup your Azure subscription for Dynamics 365 for Financials Microsoft Hosted Test Drives

1.	Login to your Azure management portal - https://https://portal.azure.com
2.   Verify that you are logged in to correct Tenant by hovering on your account icon on upper right corner. If not, switch to the Tenant associated with D365 Financials instance from the list available after click on the account icon.
 
 ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/SelectDirectory.png)
    
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

4. Add Service Principal role to application to allow delete access during Deprovisioning.
    * Install-Module MSOnline  (run this command if MSOnline is not installed)
    * Connect-MsolService (Will show a popup window to login. Login with newly created org tenant)
    * $applicationId = "<YOUR_APPLICATION_ID>"
    * $sp = Get-MsolServicePrincipal -AppPrincipalId $applicationId
    * Add-MsolRoleMember -RoleObjectId fe930be7-5e62-47db-91af-98c3a49a38b1 -RoleMemberObjectId $sp.ObjectId -RoleMemberType servicePrincipal
 
 ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/Connect_MsolService.PNG)
 
 5. Publish your offer in Cloud Partner portal. Follow instruction in [link](https://github.com/Microsoft/AppSource/blob/patch-1/Microsoft%20Hosted%20Test%20Drive/Configure_TestDrive_CloudPartner_Portal.md). 
