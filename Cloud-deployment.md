Unleash the full power of [Data Accelerator](Data-accelerator) by deploying it into your subscription in Azure by following the instructions below and get started setting up end to end data pipelines! 

# Prerequisites
 - Install Azure CLI from https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest
 - Download the scripts and templates locally via this link: https://github.com/Microsoft/data-accelerator/DeploymentCloud/

# Deployment
1. In common.parameters.txt under DeploymentCloud/Deployment.DataX, you only need to provide **TenantId** and **SubscriptionId**.  
1. For Windows OS, open a command prompt as an admin under the downloaded folder DeploymentCloud/Deployment.DataX:
```
 deploy.bat 
```

Once the deployment finishes, open the Data Accelerator Portal via http://_name_.azurewebsites.net (Url available from the command prompt or via the Azure Portal under the deployed App Service. To find this, go to App Services in http://portal.azure.com, click on the app service called "dx*", and open the URL)
   
# Troubleshooting and FAQ
 - For advanced scenarios, see [See Configuring the ARM template for details and options](https://github.com/Microsoft/data-accelerator/wiki/Arm-Parameters)
 - Please refer to the [FAQ](FAQ)
	
