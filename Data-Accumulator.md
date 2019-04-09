In streaming jobs you may have scenarios that require accumulating data over time. Example: in the home automation sample, say, we wanted to determine how many minutes is the garage door open every hour. While we may be processing the data every minute, we will want to accumulate the total minutes garage door has been open in the hour. Data Accelerator makes doing such accumulations very easy, in line in SQL! In this tutorial you will learn how.

# Step to follow
We will walk through the example described above: determining how long the garage door has been open in an hour for each home. 

- First, you want to create a table where the data will be accumulated. This table will be persisted throughout streaming. Use SQL's CREATE command to do so. Notice that comment above the query needs to be **--DataXStates--** as we are creating a stateful table.

```sql
--DataXStates--
CREATE TABLE iotdevicesample_GarageDoor_accumulated_tutorial
    (deviceId long, deviceType string, homeId long, eventTime Timestamp, status long);
``` 

- Next, create a temp table that accumulates current data with the already accumulated data. Note the last WHERE clause in the query below. This restricts the accumulation of the data to the current hour only, and thus prevents the accumulated table to grow unbounded. 

```sql
--DataXQuery--
GarageDoorAccumalator = SELECT 
                            deviceDetails.deviceId,
                            deviceDetails.deviceType,
                            deviceDetails.homeId,
                            deviceDetails.eventTime,
                            deviceDetails.status
                        FROM DataXProcessedInput
                        WHERE deviceDetails.deviceType = 'GarageDoorLock'
                        UNION ALL
                        SELECT 
                            deviceId,
                            deviceType,
                            homeId,
                            eventTime,
                            status
                        FROM iotdevicesample_GarageDoor_accumulated_tutorial
                        WHERE hour(eventTime) = hour(current_timestamp());
```

- Next, save this temp table above which has the accumulated data back to our persistent accumulator table as shown below.

```sql
--DataXQuery--
  iotdevicesample_GarageDoor_accumulated_tutorial = SELECT
        deviceId,
        deviceType,
        homeId,
        eventTime,
        status  
    FROM
        GarageDoorAccumalator;
```

- That's it! You have now created an accumulator which tracks the device status over time. Now, let's plot this data for house #150. 

```sql
--DataXQuery--
 House150Data = SELECT COUNT(DISTINCT eventTime) AS totalTime                   
                FROM iotdevicesample_GarageDoor_accumulated_tutorial
                WHERE homeId = 150 AND status=0;

House150GarageTotalTimeOpen = CreateMetric(House150Data, totalTime);

OUTPUT House150GarageTotalTimeOpen TO Metrics;
```

- Click "Deploy" button. <br/>
 ![Deploy](./tutorials/images/Deploy.PNG)

# View Metrics
Now, switch over to the Metrics tab and check chart for House150GarageTotalTimeOpen, which shows the total time the garage door has been open in the hour. Also notice, that it will reset to 0 at the start of the hour. <br/>
 ![Alert](./tutorials/images/accumulatorchart.PNG)

# Persistence
Accumulator tables are persisted in memory, and on disk of the HDInsight cluster.  They exists as singletons for the cluster, so it is possible to run into conflicts if two jobs use the same name.  Few things to follow:
  - Make sure to use unique names for the Accumulator tables between Flows. 
  - Once you have set a schema for an Accumulator table, you can no longer change it. You'll have to change name or delete the table.  See below.

To remove an existing Accumulator table, you must connect to the head node of the HDInsight Spark Cluster from the command line:
 - SSH into the head node of the HDInsight cluster ( Use either putty or other SSH utility tools. Instructions on how to SSH is at https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-linux-ambari-ssh-tunnel)
 - View files
```
	>hdfs dfs -ls hdfs://mycluster/datax/<flowName>/<accumulationTableName>/
```
 - Download files
```
	>hdfs dfs -get hdfs://mycluster/<path>   <local path>
```
 - Upload file
```
	>hdfs dfs -put <local path>   <remote path>
```

 - Delete hdfs folder
```
	>hdfs dfs -rm -r <hdfs folder path>
``` 

Example:
```
	>hdfs dfs -rm -r hdfs://mycluster/datax/myFlow/myAccmulationTable
```

For more details on hdfs refer to https://hortonworks.com/hadoop-tutorial/using-commandline-manage-files-hdfs/

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 