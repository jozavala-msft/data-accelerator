If you run into issues with your job, you will want to dig into the job logs to determine the cause. The Spark jobs has detailed logs; you can access them via the docker logs command.

In this tutorial, you'll learn to:
 - View docker logs

# Docker logs
 - You can look at the logs by querying the container that is running via Powershell
   - Launch Powershell then run the following command:
     ```
     docker logs --tail 1000 dataxlocal
     ```
   - If you want to see the logs continuously be updated, you can use the '-f' flag:  
     ```
     docker logs -f --tail 1000 dataxlocal
     ```

This will help diagnose issues, see exceptions and callstacks and confirm jobs are running properly.

* [Next tutorial : Reference Data](https://github.com/Microsoft/data-accelerator/wiki/Local-Tutorial-Reference-data)

# Other Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 