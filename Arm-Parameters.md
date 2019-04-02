# Basic Deployment
* Open common.parameters.txt under DeploymentCloud/Deployment.DataX, provide TenantId and SubscriptionId. See Configuring the ARM template for details and options.
* For Windows OS, open a command prompt as an admin and run deploy.bat under DeploymentCloud/Deployment.DataX

# Advanced Options
* If you want to use your existing AAD apps, please provide the names of serviceAppName and clientAppName.
* If you want to use any specific deployment name, please provide productName and set randomizeProductName to n.
* If you want to use your existing certificates, 
 1. please make sure all three certs-primary, reverseProxy and SSL are available.
 2. update mainCert, reverseProxyCert and sslCert with the full path of each one.
 3. set generateNewSelfSignedCerts to n. Please also provide the password to import those certs.
* If your certs are real signed, please set useSelfSignedCerts to n.
