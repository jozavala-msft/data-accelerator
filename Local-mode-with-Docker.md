# Installation
To unleash the full power of Data Accelerator, [deploy to Azure](https://github.com/Microsoft/data-accelerator/wiki/Cloud-deployment). We have also enabled running Data Accelerator locally, without any cloud dependencies, however, the features are very limited (no [Live Query](live-query), Auto Schema inference, etc.). To run Data Accelerator locally, follow Local deployment steps below.
# Local Deployment
Run Data Accelerator locally by downloading and running docker container. Even though the features are very limited compared to cloud mode, it gives you a cursory feel of the overall experience quickly.
# Prerequisites:
 - [docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows) (To get more info on this, see the [FAQ](https://github.com/Microsoft/data-accelerator/wiki/FAQ#how-do-i-install-docker)).
  - Once docker is installed and running, update the docker Settings (Note if you run the docker with less resources, your experience may be degraded or processing may lag particularly around the sample Flow): <br/> 
**Right click on docker in the System Tray-->Settings-->Advanced-->CPU: 6 cores; Memory: at least 5 GB (5120 MB).**<br/>
**![docker Advanced Settings](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/AdvancedDockerSettings.PNG)**<br/>
 - PowerShell (Windows has this by default, Linux users will have to install from [this location](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-6)). Mac users can use Terminal which is available by default.
      ```
# Deployment
   - Run the below commands as admin in Powershell on Windows (and approve subsequent elevation request) or in Terminal on Mac

        ```
        docker run --rm --name dataxlocal -d -p 127.0.0.1:49080:2020 -p 127.0.0.1:4040:4040 mcr.microsoft.com/datax/dataxlocal:v1
        ```

   - If you want to get the latest docker image, delete the one you have downloaded previously and then run the above command. To delete already downloaded image, follow these steps:

       - Run this command:
            ```
            docker images -a
            ```
       - This will list all the images on your box. Note the **ImageId** for all images listed where the repository equals msint.azurecr.io/datax/dataxlocal and then run the following command for each of the **ImageId** to remove them from the machine:

            ````
            docker image rm <ImageId>  
            ````

* Open the portal at: http://localhost:49080/home to start Data Accelerator and create your first Flow and / or checkout the samples

* Check out step by [step tutorials]( https://github.com/Microsoft/data-accelerator/wiki/Tutorials) for local mode

# Running a job
 - To try out the sample:  Go to http://localhost:49080/config, select "BasicLocal" flow. 
 - Make an edit (for example, go to Query tab and enter a space in the editor), then Click ‘Deploy’
 - Open the Metric tab and click on your Flow name. You should see your 2 default metrics which exist for all flows by default.
**Note**: Currently running only 1 job at a time is supported for the local scenario. You can control which job to run, by clicking on “Jobs” tab and starting/stopping jobs to run.

# Logs
 - **To view Spark job logs for checking job execution or for diagnosing issues, run the following command**
    ```
    docker logs --tail 1000 dataxlocal
    ```
    ###### To learn more, see the [tutorial on logs](https://github.com/Microsoft/data-accelerator/wiki/Local-Tutorial-6-Debugging-using-Spark-logs)

# SSH into the docker container
   -  ```
      docker exec -it dataxlocal /bin/bash
      ```

# Stopping the docker container
 - When finished with the container, run the following stop the container to free up used resources.
    ```
    docker stop dataxlocal
    ```
    ###### See the [FAQ](https://github.com/Microsoft/data-accelerator/wiki/FAQ#cleaning-up) to learn more how to remove all the dangling images.

# FAQ and troubleshooting:
 - Please refer to the [FAQ](https://github.com/Microsoft/data-accelerator/wiki/FAQ).  
