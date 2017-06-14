# Setting up Test Drives for Dynamics 365 app

1. Deploy [this](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fsmpresourcesprodwus.blob.core.windows.net%2Fsolutiontemplate%2Ftemplate.json) ARM template to a new resource group in your Azure subscription. 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive1.png)

2. While the ARM deployment is in progress, you need to setup your subscription by following the steps mentioned [here](https://github.com/Azure/AzureTestDrive/wiki/Setup-your-Azure-subscription-for-Test-Drives). 

3. Once your ARM deployment is completed you’ll see a resource group that will look like the one shown below:

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive2.png)

4. There are three main components in the resource group, the azure function (app service) and the workflows described by the two logic apps:
      * The Azure function in this example (“appsourcesite3qrmnus4beqie“), is a server less function with two key methods as can be seen below:
 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive3.png)

      * The method “ProvisionUserToCRM” as the name suggests provisions a user to a CRM instance by
           * Adding the user to the AAD tenant.
           * Assigns a user a “DYN365_ENTERPRISE_PLAN1” license if it exists.
           * Assigns a user to a pre-selected role in the CRM instance”
      * The method “DeprovisionUser” as the name suggests de-provisions a user from the Dynamics 365 instance with the same set of steps being performed in the reverse order.
      * Both functions, have a set of configuration settings which can be found under SendInvitationAndAddUserToCRM (for provision) and CleanupUserFromCRM (for deprovision). These are as below (with comments for individual setting). For instructions on setting up the AAD application refer to the document found here: https://github.com/Azure/AzureTestDrive/wiki/Setup-your-Azure-subscription-for-Test-Drives.  

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive4.png)

5.	Once these functions are configured by the appropriate configuration settings, the settings can be tested by using the “Test” tab on the far right of the Azure functions blade.
 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive5.jpg)

5.	Be careful to not run de-provision using the admin user (if there’s only one admin), as the only admin user would de-provisioned from the CRM instance essentially locking you out.
7.	The logic apps from “Assign” (a workflow that assigns a user to a CRM instance and license) and “Deprovsion” (a workflow that de-provisions a user at the end of a test-drive) are a wrapper over the Azure function and just call into the respective methods. In case of a CRM only app, the Azure function deployed out of box should just work, although you are more than welcome to customize it.

