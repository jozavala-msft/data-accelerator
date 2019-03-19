# Prerequisites:
 - Docker (To get more info on this, see the [FAQ](FAQ)). 
 - PowerShell (Windows has this by default, Linux/Mac users will have to install this)

# Deployment
  - Run via Powershell: (Refer cleaning up section in FAQ if you had given docker run command earlier)
    - docker run -d -p 5000:5000 -p 49080:2020 -v path:/app/aspnetcore <path>
    - Click 'Yes" when prompted to allow admin access.  

  - On your machine, go to: http://localhost:49080/home to start DataX

# FAQ and troubleshooting:
 - Please refer to the [FAQ](FAQ).  