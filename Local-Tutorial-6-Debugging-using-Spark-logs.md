The Spark jobs has detailled logs; you can access them via the docker logs command.

In this tutorial, you'll learn to:
 - View docker logs

# Docker logs
 - You can look at the logs by querying the container that is running via Powershell
   - Launch Powershell then run the following command:
```
docker ps
```

 - You will see something like this:</br>

```
1) CONTAINER ID        IMAGE                                         COMMAND             CREATED             STATUS              PORTS                                                    NAMES
2) 051b1617a877        datax.azurecr.io/datax/dataxlocal   "finalrun.sh"       4 minutes ago       Up 4 minutes        0.0.0.0:2020->2020/tcp, 80/tcp, 0.0.0.0:5000->5000/tcp   dreamy_rubin
```
  - Next, you can use the containerId from above to see the logs.  The following command gives the last 1000 entries in the log.  
```
docker logs --tail 1000 <<containerID for example: 051b1617a877>>
```

  - If you want to see the logs continuously be updated, you can use the '-f' flag:  
```
docker logs -f --tail 1000 <<containerID for example: 051b1617a877>>
```

This will help diagnose issues, see exceptions and callstacks and confirm jobs are running properly.