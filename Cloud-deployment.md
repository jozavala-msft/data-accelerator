Unleash the full power of [Data Accelerator](Data-accelerator) by deploying it into your subscription in Azure by following the instructions below and get started setting up end to end data pipelines! 

# Prerequisites
 - Install Azure CLI from [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
 - Download the scripts and templates locally via this link: [template](https://github.com/Microsoft/data-accelerator/tree/stable/DeploymentCloud)
 - (For databricks environment only; this is not required for HDInsight environments), Install Databricks CLI from [here](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#install-the-cli).

# Deployment
1. Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide **TenantId** and **SubscriptionId**. In order to setup Data Accelerator with Databricks environment, also set **useDatabricks** = y (See FAQ section below on how to use other parameters.)

1. For Windows OS, open a command prompt as an admin under the downloaded folder DeploymentCloud/Deployment.DataX and run :

```
 deploy.bat 
```

3. If you are not the admin of the tenant (typically when using AAD account), then please copy over the DeploymentCloud folder to your admin's machine and ask your admin to run the following command:

```
runAdminSteps.bat
```

For 
* Data Accelerator with **HDInsight** environment - Once the deployment finishes, open the Data Accelerator Portal via http://_name_.azurewebsites.net (Url available from the command prompt or via the Azure Portal under the deployed App Service. To find this, go to App Services in http://portal.azure.com, click on the app service called "dx*", and open the URL)

* Data Accelerator with **Databricks** environment - If useDatabricks was set to y in common.parameters.txt file before running deploy.bat then the above steps will setup the azure resources required by Data Accelerator including a Databricks resource. To finish setting up databricks resource you will further need to generate databricks token, create a secret scope, upload jars to DBFS which are required to run spark jobs and finally create a databricks cluster for live query. Please refer [Data Accelerator with Databricks Environment Setup](./Data-Accelerator-with-Databricks#data-accelerator-with-databricks-environment-setup) for complete instructions. 

 ### Cloud deployment on Linux and Mac
* The ARM deployment for DataX currently support only Windows. If you are looking for multiplatform support (Linux and Mac) please reach out to discuss options.

For details, please see [Cloud Deployment On Linux](https://github.com/Microsoft/data-accelerator/wiki/Cloud-Deployment-On-Linux)
   
# Troubleshooting and FAQ
 - For any issue,please refer to the [FAQ](https://github.com/Microsoft/data-accelerator/wiki/FAQ#arm-deployment-faq)
 - For advanced scenarios, see [See Configuring the ARM template for details and options](https://github.com/Microsoft/data-accelerator/wiki/Arm-Parameters)
	
