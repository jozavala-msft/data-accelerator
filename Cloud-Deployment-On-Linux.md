Currently The ARM deployment for DataX doesn't support multiplatforms (Linux and Mac). We have a plan to release it in the next release.

# Prerequisite
* Install Powershell Core
https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-6

* Install Azure CLI
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

# Deployment Steps
The following is a list steps that need to be done to set up a DataX environment.
* Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide TenantId and SubscriptionId.
* Open a shell / command prompt
* Run Powershell Core

## Resources Deployment
* Run deployResources.ps1

## App Deployment
* Run deployApps.ps1

## Sample Deployment
* Run deploySample.ps1