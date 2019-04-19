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
* Follow the steps below to set up a DataX environment

## Resource Deployment
* Run deployResources.ps1
* After the script is finished, the following steps should be done
  * Setup secrets in KVs: Automated
  * Run script actions for HDInsights
    1. Upload all files in DeploymentCloud/Deployment.Common/scripts to a storage account
    2. Add Script Actions
        Azure Portal > Resource Group > Select DataX resource group > Select HDInsight cluster > Script Actions > Submit New > Custom > Bash Script URL > Provide the URI of the script you uploaded in step 1
  * Setup CosmosDB
    * Create Production database and add the following set of collections
        * commons
        * configgenConfigs
        * flows
        * sparkClusters
        * sparkJobs
    * Upload the documents from DeploymentCloud/Deployment.Common/CosmosDB to each collection
  * Setup KVAccess
    * To each KV, Make sure the following principals are added to the access policies
        * The Webapp app
        * The service AAD app
        * SparkManagedIdentity
        * Virtual Machine Scale Set
  * Setup ServiceFabric
        * Install SSL certificate on cluster nodes. Please refer to https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-tutorial-dotnet-app-enable-https-endpoint#install-certificate-on-cluster-nodes
        * Open port 443 in the Azure load balancer. Please refer to https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-tutorial-dotnet-app-enable-https-endpoint#open-port-443-in-the-azure-load-balancer 

## App Deployment
* Run deployApps.ps1

## Sample Deployment
* Run deploySample.ps1