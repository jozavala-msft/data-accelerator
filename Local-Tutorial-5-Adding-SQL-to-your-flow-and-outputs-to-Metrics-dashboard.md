The Query tab is where you can add customized transformation and logic.  

In this tutorial, you'll learn to:
 - Add a Metric and an Alert
 - Use the Editor features including Live Query to speed up your development

# Validating the query

 - Open the Query tab of your flow<br/>
![QueryTab](./tutorials/images/querytab.PNG) 

# Adding a Metric and an Alert output

 - In the default query, T1 will contain all the columns and data from each batch.  DataXProcessedInput is the DataX Raw input
 - To add a graph on the Metrics dashboard, the data has to be in a specific format.  
   - metricExample will be the name of the graph on the dashboard:
   - EventTime will be the timestamp for the metric.  You can use current_timestamp() as the EventTime
   - MetricName will be the title of the metric within the graph
   - Metric will be the number to be plotted at the given EventTime
   - Product is the flowname, Use the name you input from the Info tab
 - OUTPUT TO enables to send data from a table (or comma-separated list of table names) to a given output.  Metrics will send data to the Metrics dashboard.  Multiple lines will be drawn in the same graph if multiple names are used.  Similarly, you can output tables to multiple outputs in one line by using a comma-separated list.  <br/>
![QueryTab](./tutorials/images/querytabquery.PNG) 
 - Click 'Deploy' 
 - Open the metric tab and click on your Flow name
 - You should see your 2 default metrics which exists for all flows by default.  In addition, you should also see the custom metrics you have created.<br/>
![QueryTab](./tutorials/images/querytabmetrics.PNG) 

# Exploring the Query Editor features
 - You can set the theme to the dark theme, or see the code preview to debug issues<br/>
![QueryTab](./tutorials/images/querytheme.PNG) 
 - The Run button lets you query incoming data in line and get results instantly.  (This functionality is only available in a Azure deployment.  See the Cloud SQL Tutorial to learn more.)

You can now continue to iterate on your query to add more logic and validate the changes on the Metrics dashboard.
