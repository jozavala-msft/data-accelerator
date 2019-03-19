Functions can extend query code by adding either Azure function or UDF/UDAF via Scala code in jars files.

In this tutorial, you'll learn to:
 - Add an Azure Function
 - Add a Jar file to use as a UDF or UDAF


# Adding an Azure function
To set up an Azure function:
 - Open your Flow and go to the Functions Tab
 - Select add Azure Function from the Function tab<br/>
	<image>
 - The Alias will be how to reference the function in the Query tab
 - The Service Endpoint, API, Function key and Method type can be obtained from the Azure portal<br/>
	<images>
	
You can now use the Azure Function in your query using the Alias as such, passing parameters such as values or column names as parameters
	T2 = Select myAlias(param1, param2, …) FROM DataXProcessedInput;

# Adding a Scala User Defined Function
Similarly, to set up a user-defined function or UDF:
 - Open your Flow and go to the Functions Tab
 - Select UDF from the drop down in the Function tab.
 - You will need to provide 
    - an alias, 
    - Path to the jar file that implement the jUDF interface.  See an example in the Spark project here <>.  Note this jar file needs to be uploaded under the default container of the default blob of the Spark cluster.
    - The class name is the fully qualified path and classname, i.e. datax.sample.udf.UdfHelloWorld
	
Once you have done so, you can use the UDF in your query, using a similar pattern as an Azure function.<br/>
<images>

# Adding a Scala User-Defined Aggregated Function
To set up a user-defined aggregated function:
 - Open your Flow and go to the Functions Tab
 - Select UDAF from the drop down.  
 - Similar settings as with UDF need to be provided.  The jar file also needs to be updated under the default container of the default blob of the Spark cluster

To use the UDAF, you can pass in a table to the UDAF alias:
	T3 = Select myUDAF(T1);

You can test your query using the Run button after selecting your query.  Once you are satisfied with the changes, make sure to press 'Save' to store the changes and deploy. 

