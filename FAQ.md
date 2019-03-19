#  Local experience FAQ

# How do I install docker? 
	0. HyperV on Windows (Docker will enable this)
	1. Install the client
		a. Windows: https://hub.docker.com/editions/community/docker-ce-desktop-windows 
		b. Linux: https://docs.docker.com/install/linux/docker-ce/ubuntu/  
		c. Mac: https://docs.docker.com/docker-for-mac/install/
	2. Go to hub.docker.com to sign up if you have not done so already.
	3. Your machine will reboot. There will be a prompt to enable HyperV since docker installer enables HyperV for you. In order for the docker container to run successfully, HyperV is a prerequisite. You need to allow the HyperV to be enabled. You machine will reboot after this
	4. Go to the system tray, you will see a ship icon (if you do not see the docker icon in the system tray, go to startà type "docker"à and click on it to start the docker desktop) and on hovering it will show that docker is starting post reboot. 
	5. Once the docker icon is stable, you will be required to login. Do the below steps only after the docker icon is stable i.e. the docker has started successfully.
	6. Docker Settings: 
	Right click on Docker in the system trayàSettings->Advanced ->CPU: 4 cores; Memory: at least 4 GB (4096 MB).

Other useful commands
	1. Give the below commands to look at the query and service telemetry:
	You can look at the logs by querying the container that is running
		a. docker ps
			i. An example output
				1) CONTAINER ID        IMAGE                                         COMMAND             CREATED             STATUS              PORTS                                                    NAMES
				2) 051b1617a877        datax.azurecr.io/datax/dataxlocal   "finalrun.sh"       4 minutes ago       Up 4 minutes        0.0.0.0:2020->2020/tcp, 80/tcp, 0.0.0.0:5000->5000/tcp   dreamy_rubin
		b. docker logs --tail 1000 <<containerID for example: 051b1617a877>
		c. For seeing continuous logs, 
			i. Docker logs -f <containerId>
	2. In case metrics are not showing you may need to scale up your docker image:
		a. Docker Settings: 
		Right click on Docker in the system trayàSettings->Advanced ->CPU: 4 cores; Memory: at least 4 GB (4096 MB).

# Cleaning up:
 - Commands to give to stop and remove the container and volume on the host machine that is mapped to the container:
		Notice that for metrics to refresh we need -v parameter above. It is recommended that the way to use this is: Once you stop the container, you need to explicitly remove the volume as well:
   - docker ps (returns a list of all available containers)
   - docker stop <ContainerId>
   - docker rm <ContainerId>
   - docker volume rm path -f
			…  path is the volume that you give in the run command above. eg. /app/aspnetcore
			
 - You can search for any existing / dangling volumes inside the container
   - Docker volume ls
   - Docker volume prune -f (for removing all unused volumes)
   - Docker volume rm <<volumeName> as result(s) for "docker volume ls" command above>
	
 - If you wish to delete all images from your machine
   - Docker system prune -a
		
# SSH into docker container
Running the below cmd will take you to the container's bash shell
	docker exec -it <containerId>  /bin/bash
	
# How to Install ps 

RUN below cmd from bash shell
apt-get update && apt-get install -y procps

How to list Java VMs (spark job runs as a Java VM)
Run from bash shell
jps

e.g output  from jps (SparkSubmit is spark job)

root@39e3ea3ed861:/app/aspnetcore# jps
1985 SparkSubmit
2451 Jps


#  ARM Deployment FAQ

# Trouble shooting
 - If Scripts are not enabled and you get an error running deploy.bat, you can update the policy with "Set-ExecutionPolicy" in a Powershell prompt, i.e. by running the following: Set-ExecutionPolicy Unrestricted
 - If you are not an admin of the subscription, please ask your subscription admin to complete these steps manually post deployment 
 - If you see an error related to AAD app admin consent policies (i.e. Unexpected End of JSON), please see step above  Please ask your subscription admin to run these steps
 - If you see an error related to Azure login, your deployment may occur on a different account. Please make sure you log in Azure with the right information

# FAQ
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




