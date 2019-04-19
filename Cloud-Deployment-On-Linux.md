Currently The ARM deployment for DataX doesn't support multiplatforms (Linux and Mac). We have a plan to release it in the next release.

# Prerequisite
* Install Powershell Core
https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-6

* Install Azure CLI
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

# Deployment Steps
* Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide TenantId and SubscriptionId.
* Open a shell / command prompt
* Run Powershell Core
* Follow rest steps to set up a DataX environment

## Resource Deployment
* Run deployResources.ps1
* After the script is finished, the following steps should be done
  * Setup secrets in KVs
  * Run script actions for HDInsights
  * Setup CosmosDB
  * Setup KVAccess
  * Setup ServiceFabric

## App Deployment
* Run deployApps.ps1

## Sample Deployment
* Run deploySample.ps1