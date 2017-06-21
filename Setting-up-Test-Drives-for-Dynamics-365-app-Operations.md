# Setting up Test Drives for Dynamics 365 for Operations app

1. Deploy [this](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fsmpresourcesprodwus.blob.core.windows.net%2Fsolutiontemplate%2FARMtemplate_Dynamics365_Ops.json) ARM template to a new resource group in your Azure subscription. 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive1.png)

2. While the ARM deployment is in progress, you need to setup your subscription by following the steps mentioned [here](https://github.com/Microsoft/AppSource/blob/master/Setup-your-Azure-subscription-for-Dynamics365-Operations-Test-Drives.md). 

3. Once your ARM deployment is completed you’ll see a resource group that will look like the one shown below:

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive2.png)

4. There are three main components in the resource group, the azure function (app service) and the workflows described by the two logic apps:
      * The Azure function in this example (“appsourcesite3qrmnus4beqie“), is a server less function with two key methods as can be seen below:
      * The method “ProvisionUserToOperations” as the name suggests provisions a user to the Dynamics 365 for Operations instance by
           * Adding the user to the Operations.
           * Assigns a user to an organization.
           * Assigns a user to a pre-selected role in the operations instance”
      * The method “DeprovisionUserFromOperations” as the name suggests de-provisions a user from the Dynamics 365 instance with the same set of steps being performed in the reverse order.
      * Both functions, have a set of configuration settings which can be found under ProvisionUserToAx (for provision) and DeprovisionUser (for deprovision). These are as below (with comments for individual setting). For instructions on setting up the AAD application refer to the document found here: https://github.com/Microsoft/AppSource/blob/master/Setup-your-Azure-subscription-for-Dynamics365-Operations-Test-Drives.md.  

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365_Ops_Function1.PNG)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365_Ops_Function2.PNG)

5.	Once these functions are configured by the appropriate configuration settings, the settings can be tested by using the “Test” tab on the far right of the Azure functions blade.
 
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Dynamics365TestDrive5.jpg)

6.	Be careful to not run de-provision using the admin user (if there’s only one admin), as the only admin user would de-provisioned from the Dynamics 365 instance essentially locking you out.
7.	The logic apps from “Assign” (a workflow that assigns a user to a Dynamicss instance) and “Deprovsion” (a workflow that de-provisions a user at the end of a test-drive) are a wrapper over the Azure function and just call into the respective methods. In case of a Dynamics 365 for Operations only app, the Azure function deployed out of box should just work, although you are more than welcome to customize it.

