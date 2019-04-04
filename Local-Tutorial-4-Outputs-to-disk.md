The output tab let's you configure outputs to route data to.

In this tutorial, you'll learn to:
 - Add an output location
 - Write data to this output location

# Setting up an output
 - Open your Flow
 - Open the Output Tab to configure an output and select Add 'Local' <br/>
 ![New output](./tutorials/images/outputaddlocal.PNG)
   - For Alias, input "myOutput"; this is how the output will be referred to throughout the Flow, 
   - For folder, you can input 'file:///c:/output'; this is the folder data will go to
   - Format will be JSON
   - You can decide to use GZIP compression or none as well <br/>
 ![New output](./tutorials/images/outputaddlocalinfo.PNG)
 - Go back to the Query tab and input a new OUTPUT statement at the end: <br/>
    - OUTPUT extendedTemperature TO myOutput;
 ![New output](./tutorials/images/outputquery.PNG)
 - Click Deploy.  

You have connected the Flow to a new output.  You can view the output data in the location you have setup.

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 