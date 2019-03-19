The output tab let's you configure outputs to route data to.

In this tutorial, you'll learn to:
 - Add an output location
 - Write data to this output location

# Setting up an output
 - Click the Open Tab to open it and select Add an Azure blob from the drop down

 - For Alias, write "myBlob"; this is how the blob will be referred to throughout the Flow, 
   - The following information will come from the Azure Portal:
   - The connection string will come from the Portal
   - Container name will be where the data will be going
   - Blob prefix and partition format will set up how to file the files in the blob

   - You can decide to use GZIP compression or none as well
   - Go back to the Rules tab and select "myBlob" from the alert drop down of the rules you have created

Saving, deploying and executing
 - Click Deploy.  

You have connected Flow to a new output.  You can view the output data in the location you have setup.