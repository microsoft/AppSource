# Custom configurations using Azure functions #

Detailed below is how to use Azure function to make a custom configuration like adding a reply URL to AAD: 

* Navigate to the Azure portal and login.
* Click on “+”, search for “Function App”, provide a name (an existing or new Resource group) and hit create.
* Choose Webhook + API and language as C# for this example and click on Create this function.

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/LA1.jpg)

* This will take you through the wizard to familiarize you with the editor.
* You could just hit run to experience the sample code that is provided out of box to familiarize with the IDE.
* Alternatively, paste the code below into the editor (replace tenantId, clientId and clientSecret as appropriate). The application must be a global admin in the tenant to be able to update Reply URLs in AAD app.
* You can also reference nuget packages with Azure functions. To do this: Click on View Files in the right pane, click on ‘+ Add’, and name the file project.json . The example requires the ADAL nuget package and can be referenced by putting this in the project.json (as below)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/LA2.jpg)

* There’s a test pane on the right (right next to View Files), where you can provide inputs. A sample input: {"app Uri":"https://myapp.azurewebsites.net/"}
*    Clicking on save and run should run [this](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/Project.json) function.
