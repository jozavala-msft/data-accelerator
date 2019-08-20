Data Accelerator environment can now be set up to run jobs on either Databricks or HDInsight. During the time of setting up the Data Accelerator environment, you can choose the platform on which you would want to run the spark jobs – Databricks or HDInsight. 

In this tutorial we will go over:
* How to setup Data Accelerator environment that uses Databricks
* How to run Data Accelerator flows on Databricks

# Data Accelerator with Databricks Environment Setup

### Prerequisites
* Install Azure CLI from [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
* Install Databricks CLI from [here](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#install-the-cli)
* Download the scripts and templates locally via this link: [template](https://github.com/Microsoft/data-accelerator/tree/stable/DeploymentCloud)

### ARM Deployment
1. Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide **TenantId** and **SubscriptionId**. Also set **useDatabricks** = y 
2. For Windows OS, open a command prompt as an admin under the downloaded folder DeploymentCloud/Deployment.DataX and run :
```
 deploy.bat 
```
3. If you are not the admin of the tenant (typically when using AAD account), then please copy over the DeploymentCloud folder to your admin's machine and ask your admin to run the following command:
```
runAdminSteps.bat
```
The above steps will setup the azure resources required by Data Accelerator. A Databricks resource will also be created. To finish setting up databricks resource you will further need to generate databricks token, create a secret scope, upload jars to DBFS which are required to run spark jobs and finally create a databricks cluster for live query.

### Generate Databricks Token
The following steps will instruct you through the steps required to create a Databricks token. This databricks token will be required to run Databricks CLI commands which we will go over later in the setup process and for running flows on databricks. 
1. On https://portal.azure.com, go to the ‘Azure Databricks Service’ resource created by the ARM deployment step and click on ‘Launch Workspace’.

