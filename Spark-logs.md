If you run into issues with your job, you will want to dig into the job logs to determine the cause. In this tutorial you will learn how.

# Steps to follow

- You can manage your jobs using the 'Jobs' page on the Data Accelerator portal. Here you will see all the jobs that are running, or not.<br />
 ![Jobs](./tutorials/images/jobs.PNG)

- To start or stop the job, you can use the play and stop buttons.

- To access the logs for any job, click on the logs link. you will then be prompted for username and password for HDInisghts cluster, which is stored in KeyVault.

- To get the username and password:

_If you are admin of the subscription where Data Accelerator is deployed:_
- Sign-in to the [Azure portal](https://portal.azure.com), go to the resources of the subscription where Data Accelerator has been deployed and open the KeyVault resource called kvSpark*, and click on Secrets. If you get a message saying 'You are unauthorized to view the contents' then you need to give yourself access to the Keyvault.  <br />
 ![Jobs](./tutorials/images/secrets.PNG)

- To give access to the KeyVault, click on Access Policies<br />
 ![Jobs](./tutorials/images/accesspolicies.PNG)

- Click on '+Add new'<br />
 ![Jobs](./tutorials/images/addnew.PNG)

- Fill in yourself as the Access Principal and select Get and List for Secret permissions. <br />
 ![Jobs](./tutorials/images/adduser.PNG)

- Now, Save your changes and click on the Secrets for the Keyvault. This time you should be able to see all the secrets. Click on secret called configgen-livyconnectionstring-*

- Click on current version and then on 'Show secret value', which will show you the endpoint, username and password. Use the username and password and login to the HDInisghts cluster.

_If you do not have access to the subscription where Data Accelerator is deployed:_

- Ask you admin for the username and password of the HDInisghts cluster (your admin will need to follow the steps above), or ask the admin to give you permission to the subscription (or the Keyvault) and you can follow the steps above.



