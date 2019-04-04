# Basic Deployment
* Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide TenantId and SubscriptionId.
* For Windows OS, open a command prompt as an admin and run deploy.bat under DeploymentCloud/Deployment.DataX

# Advanced scenarios
###  Use signed certificates for a production environment
* The script will generate the self-signed certificates by default but this is not recommended for a production environment. For a production environment, please get the signed certificates from a CA ready before you run the scripts.
* For the certificate creation:
	* You will need three certificates: mainCert, reverseProxyCert and sslCert
	* For Subject/Common Name: This will be your Service Fabric cluster endpoint (e.g.: <SFclusterName>.westus2.cloudapp.azure.com). 
	* Make sure that the Service Fabric cluster name is available as it will be used when creating the cluster.
* In common.parameters.txt, update the following properties:
	* Set generateNewSelfSignedCerts to n
	* Set useSelfSignedCerts to n
	* Update mainCert, reverseProxyCert and sslCert with the path of each certificate.
		
### Use existing AAD apps
* For Data Accelerator processing, two AAD apps will be used: A clientApp for the web site and a serviceApp for the service fabric service apps. The script will create the two apps by default. And once the deployment's done, you might need to get an admin of your tenant to consent those apps. Please ask your tenant owner. If you already have the apps which are admin-consented, you can use them and no additional process will be needed. In order to use existing apps, please set the following properties as described.
	* Update serviceAppName and clientAppName with your app names
	* e.g.
		* serviceAppName=myServiceApp
		* clientAppName=myClientApp

### Recover an existing Data Accelerator environment
* If you need to recover an existing environment, there are two options. 
	* The first option which is recommended is to build a new environment
		* Delete the resource group of your environment 
		* Please make sure all parameter values in common.properties.txt are the same as what you used before
		* The script will generate a randomized product name by default so if you want to use the same product name
			* Use the product name to productName property
				* e.g. productName=dx2871224153
		 	* Set randomizeProductName=n
		* Run the deploy,bat to build a new one
	* And the other way is you can try to patch the environment but there is no guarantee that this will fix the problem in your environment.  
		* Delete the problematic resources is not working
		* Use the same product name
			* Use the product name to productName property
			* Set randomizeProductName=n
		* Run the deploy,bat to build a new one

### Install/update the app packages
* If you want to deploy the new packages such as the service fabric apps and the web site to your existing environment, please follow the steps below.
	* In common.parameters.txt,
		* Please make sure all parameter values are the same as to what you used before
		* Use the same product name
			* Use the product name to productName property
			* Set randomizeProductName=n
		* Set the package version to install a specific build, if not, just comment out the package version parameter
			* e.g. use a specific version for DataxFlow
				* DataxFlow=1.0.0-CI-20190201-231755
			
		* Set deployApps to y and n for deployResources and deploySample
			* deployApps=y
			* deploySample=n
		* Run the deploy.bat

### Scale up by using bigger / high performance resources
* For some resources such as Service Fabric, HDInsight and Redis, the default type and size are geared toward testing things out and is smaller.
	* The default values are as follows
	
		* VM size for Service Fabric resource
			* vmNodeTypeSize=Standard_D2_v2
		
		* VM size for Spark HeadNode
			* vmSizeSparkHeadnode=Standard_D3_V2
		
		* VM size for Spark WorkerNode
			* vmSizeSparkWorkernode=Standard_D3_V2
		
		* Redis Cache Size
			* redisCacheSize=Basic_C_0
		
	* And you can customize them like the following examples
	
	* e.g. 
		* For Service fabric
		  * vmNodeTypeSize=Standard_D3_v2
		  * For details, please refer to https://azure.microsoft.com/en-us/pricing/details/service-fabric/
	
		* For HDInsight
		  * vmSizeSparkHeadnode=Standard_D12_V2
		  * vmSizeSparkWorkernode=Standard_D14_V2
		  * For details, please refer to https://azure.microsoft.com/en-us/pricing/details/hdinsight/
	
		* For redis Cache, 
		  * redisCacheSize=Premium_P_3
		  * For details, please refer to https://azure.microsoft.com/en-us/pricing/details/cache/``