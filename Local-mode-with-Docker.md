To unleash the full power Data Accelerator, [deploy to Azure](Cloud-deployment) and check the tutorials for [cloud mode](https://github.com/Microsoft/data-accelerator/wiki/Tutorials#cloud-mode). We have also enabled a "hello world" experience that you try out locally by running docker container. When running locally there are no dependencies on Azure, however, note that the functionality in local mode is very limited and only there to give you a very cursory overview of Data Accelerator. To run Data Accelerator locally, check out the instructions below and then check out the tutorials of [local mode](https://github.com/Microsoft/data-accelerator/wiki/Tutorials#local-mode).

# Prerequisites:
 - Docker (To get more info on this, see the [FAQ](FAQ)). 
 - PowerShell (Windows has this by default, Linux/Mac users will have to install this)

# Deployment
  - Run via Powershell: (Refer cleaning up section in FAQ if you had given docker run command earlier)
    - docker run -d -p 5000:5000 -p 49080:2020 -v path:/app/aspnetcore <path>
    - Click 'Yes" when prompted to allow admin access.  

  - On your machine, go to: http://localhost:49080/home to start Data Accelerator and create your first Flow.

# FAQ and troubleshooting:
 - Please refer to the [FAQ](FAQ).  