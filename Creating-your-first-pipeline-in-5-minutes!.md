One you have completed the deployment of Data Accelerator to your subscription, you are ready to create your first Flow! In this tutorial you will learn how to:
* Create a new Flow
* Configure input source of data, either Eventhub or IoTHub
* Inspect schema of incoming data
* Deploy and run the Flow

# Steps to follow
* Open Data Accelerator portal and go to the Flows tab

* Click on "New" on the Flows tab, this will create a new Flow:<br /><br />
 ![New Flow](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/Tutorial1-1.png)

* Switch to the Input tab and select input type. Data Accelerator supports Eventhub and IoThub

* Enter the Connection string for Eventhub, or Eventhub-Compatible Name and Endpoint for IotHub:<br /><br />
_Input type:Eventhub_<br/>
 ![Input](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/InputEventhub.PNG)<br /><br />
_Input type:IoThub_<br/>
 ![Input](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/InputIoT.PNG)<br/>

* Click "GetSchema" button. This will sample the data for the number of seconds specified and infer the schema of the incoming data: <br /><br />
 ![Schema](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/GetSchema.PNG)<br/>

* Click "Deploy" button to save and run the Flow. That's it! You have created your first end to end data streaming pipe!<br /><br />
 ![Deploy](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/Deploy.PNG)<br/>

# View Metrics
Now switch to the Metrics tab and you will see metrics for rate of events coming in and number of events ingested!<br /><br />
 ![Deploy](https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/newflowmetrics.PNG)<br/>