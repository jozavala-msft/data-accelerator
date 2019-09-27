# Index
* [Local deployment FAQs](https://github.com/microsoft/data-accelerator/wiki/FAQ#local-deployment-faq)
* [Cloud deployment FAQs](https://github.com/microsoft/data-accelerator/wiki/FAQ#cloud-deployment-faq)

# Local Deployment FAQ
### How do I install docker? 
 - Go to hub.docker.com to sign up and login if you have not done so already.
 - Install the docker client
	- Windows: https://hub.docker.com/editions/community/docker-ce-desktop-windows
	- Linux: https://docs.docker.com/install/linux/docker-ce/ubuntu/  
	- Mac: https://hub.docker.com/editions/community/docker-ce-desktop-mac
 - Your machine will reboot. On Windows, there will be a prompt to enable HyperV since docker installer enables HyperV for you. **In order for the docker container to run successfully, HyperV is a prerequisite.** You need to allow the HyperV to be enabled. You machine will reboot after this.
 - Go to the system tray, you will see a ship icon (if you do not see the docker icon in the system tray, go to start and type "docker" and click on it to start the docker desktop) and on hovering on the shop icon it will show that docker is starting post reboot. 
 - Once the docker icon is stable, you will be required to login. Do the below steps only after the docker icon is stable i.e. the docker has started successfully.
 - **docker Settings:** 
	**Right click on Docker in the system tray Settings-->Advanced -->CPU: 6 cores; Memory: at least 5 GB (5120 MB).**
   **![docker Advanced Settings](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/AdvancedDockerSettings.PNG)**
### Other useful commands
 - Visit the [docker documentation](https://docs.docker.com/engine/reference/commandline/docker/) for detailed commands
### Cleaning up:
 - If you wish to delete all dangling images from your machine and images that are not attached to any container
   ```
   docker image prune -af
   ```
### View output within a docker container
You can view files within a container by statrting a bash session inside the container.  This is useful to view output in case you have that specified in your flow. You can cd into the folder you specified when adding a local output location, say, Local Folder URI (e.g. /app/aspnetcore/output)
 - If you wish to view data from output
   ```
   docker exec -it dataxlocal /bin/bash
   ```
  - View the contents of a folder
    ```
    ls
    ```
  - Navigate to a particular folder
    ```
    cd <folder name>
    ```
  - View the contents of a file
    ```
    cat <filename>
    ```
### Copy files into or from a docker container
To copy files into the container, use the following
```
docker cp myfile.txt dataxlocal:/app/aspnetcore/myfile.txt
```
To copy files out of the container, use the following
```
docker cp dataxlocal:/app/aspnetcore/myfile.txt myfile.txt
```
### Look at Spark Logs
   - [Spark Logs](https://github.com/Microsoft/data-accelerator/wiki/Spark-logs)
   - [Spark logs local](https://github.com/Microsoft/data-accelerator/wiki/Local-Tutorial-Debugging-using-Spark-logs)

##  Cloud Deployment FAQ
### Trouble shooting
 - If Scripts are not enabled and you get an error running deploy.bat, you can update the policy with "Set-ExecutionPolicy" in a Powershell prompt, i.e. by running the following: Set-ExecutionPolicy Unrestricted
 - If you are not an admin of the subscription, please ask your subscription admin to complete these steps manually post deployment: 
```
adminSteps.ps1 
(along with the generated configuration file (copy the whole folder))
````
 - If you see an error related to AAD app admin consent policies (i.e. Unexpected End of JSON), please see step above  Please ask your tenant admin to run admin steps
 - If you see an error related to Azure login, your deployment may occur on a different account. Please make sure you log in Azure with the right information
 - I am a guest of a tenant, how can I deploy DataX?  You need to be a contributor of the tenant, please speak to your admin to gain access.
 - How many resources does the ARM template create?  We create 1 resource group for all 24 resources.
 - The same resource group can host 1 or more products but we recommend separate subscription for each instance for now

		e.g.
		If your product name is A and the resource  group name is RG_A, the ARM template will create them like below:
		In RG_A (resource group)
		        A_1
			A_2
			A_3
		 
		And later, if you deploy a new product named B in the same resource group,
		In RG_A
		        A_1
			A_2
			A_3
		        B_1
			B_2
			B_3
 
 - Will ARM reuse any resources across product if I deploy in the same group?  No, the ARM template will create another set of resources for your new product. We don’t re-use any resources from other products.
 
 - What if I run the ARM template a second time, will it create any duplicate resources?  Will it detect any broken/missing/deleted resources to fix bad states?
	
 - If you redeploy the same product, ARM template will just update existing resources. We don’t create any dups for the same product.
 
 - If you redeploy the same product and there are any missing resources, ARM template will create them. And for the ones in bad state, it depends on the type of the issue. E.g. for any missing secrets in keyvault or missing files in blob, The powershell scripts can fix them.




