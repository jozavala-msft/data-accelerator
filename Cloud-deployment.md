Unleash the full power of [Data Accelerator](Data-accelerator) by deploying it into your subscription in Azure by following the instructions below and get started setting up end to end data pipelines! 

# Prerequisites
 - Install Azure CLI from https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest
 - Download the scripts and templates locally via this link: https://github.com/Microsoft/data-accelerator/DeploymentCloud/

# Deployment
 - Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide TenantId and SubscriptionId.  
 - For Windows OS, open a command prompt as an admin and run deploy.bat under DeploymentCloud/Deployment.DataX

Once the deployment finishes, go to http://<name>.azurewebsites.net to open the DataX portal (Url available from the deployed App Service. To find this, go to App Services in http://portal.azure.com, click on the app service called "dx*", and open the URL)
   
# Troubleshooting and FAQ
 - For advanced scenarios, see [See Configuring the ARM template for details and options](https://github.com/Microsoft/data-accelerator/wiki/Arm-Parameters)
 - Please refer to the [FAQ](FAQ)
	
