In a [previous tutorial](Set-up-new-outputs) we had seen how to set up a new output sink and direct alerts to that output sink. In this tutorial you will learn how to direct any dataset defined in code to a Azure SQL Database sink using the OUTPUT keyword. 

# Steps to follow
* Open the flow created in the [Tagging tutorial](Tagging-simple-rules)

* Open the Output tab and add a new output sink. Select Azure SQL Database<br/>
![New Rule](./tutorials/images/sqlOuputSelection.png)<br/>
* Configure the Azure SQL Database, by specifying the alias, JDBC connection string and write mode. In this example we choose Append mode <br/>
![New Rule](./tutorials/images/sqlOutputConfig.png)<br/>
* Switch to the Query tab and at the end add following line using the OUTPUT keyword.<br/>
OUTPUT T1 TO mySqlOutput; <br/>
![New Output](./tutorials/images/simpleruleSqlOut.png)<br/>
* Click "Deploy" button. That's it! <br/>
 ![Deploy](./tutorials/images/Deploy.PNG)

**Notes**
- You can optionally use bulk insert to insert data to SQL database. Writes will be faster, however there are few restrictions that you need to be aware off
  - The data types of the data being written need to exactly match that in SQL table
  - The order (ordinal) of columns in data being written need to exactly match that in SQL table

- Apart from Azure SQL Database, you can also output to Azure SQL Data Warehouse by specifying its connection information in the same way in the Azure SQL Database output settings page. 

# View Data
Now, switch over to the output sink, and notice the data flowing to Azure SQL Database. 

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 

