We have seen no code experience provided by Data Accelerator to set up Rules and Alerts, and also seen how you can do more complex queries using SQL and other capabilities like Windowing functions, etc. At times, for even more advanced scenarios, you may want to create function that you can invoke from SQL. Functions can extend query code by adding either Azure function or UDF/UDAF via Scala code in jars files.

In this tutorial, you'll learn to:
 - Add an Azure Function
 - Add a Jar file to use as a UDF or UDAF


# Adding a Scala User Defined Function
To set up a user-defined function or UDF:
 - Open your Flow and go to the Functions Tab
 - Select UDF from the drop down in the Function tab.
 - You will need to provide 
    - an alias, For example 'myUDFFunction'
    - Path to the jar file that implement the jUDF interface. See an example below.  For example:  'file:///c:/myUDF.jar'
    - The class name is the fully qualified path and classname, i.e. datax.sample.udf.UdfHelloWorld

```scala
package datax.sample.udf

import org.apache.spark.sql.api.java.{UDF1 => jUDF}

class UdfHelloWorld extends jUDF[String, String]{
  override def call(p1: String): String = {
    "hello, " + p1
  }
}
```
Once you have done so, you can use the UDF in your query,  
```sql
--DataXQuery--
T3 = SELECT 
        *,
        myUDFFunction("myName") AS udfresult
     FROM T2
```

# Adding a Scala User-Defined Aggregated Function
To set up a user-defined aggregated function:
 - Open your Flow and go to the Functions Tab
 - Select UDAF from the drop down.  
 - Similar settings as with UDF need to be provided.  


To use the UDAF, you can pass in an array to the UDAF alias:

```sql
--DataXQuery--
T1 = SELECT myUDAF(myArray)
     FROM DataXProcessedInput;
```

 - Hit 'Deploy' to deploy your changes! 

* [Next Tutorial : Custom Schema](https://github.com/Microsoft/data-accelerator/wiki/Local-Tutorial-14-Custom-schema)

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 