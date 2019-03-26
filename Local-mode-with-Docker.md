To make it easy for you to try out Data Accelerator, without deploying anything to the cloud, we have enabled running the pipeline [locally](Local-mode-with-Docker). The tools and services have been packaged in a docker container so you can try out easily locally. While the local deployment does not have all of the features available in the full cloud deployment, it will give you a quick idea of the pipeline. 

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