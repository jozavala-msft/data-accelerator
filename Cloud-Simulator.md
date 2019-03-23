The Cloud simulator provides data to an Event or IoT hub enabling developing rules and queries, emulating production data flowing into an environment.  In this tutorial you will learn how to:
* Update the schema of the generated data
* Create rules to generate special conditions such as drops/increases in data (future)

# Steps to follow
* Open Simulator Project
* Open data.json<br />
 ![Json](./tutorials/images/SimulatorJson.png)
* Notice the schema and ranges of values.  <br />
_Input type:json<br/>
 ![Input](./tutorials/images/SimluatorJson)<br />
* Update the schema to the data you need
* Deploy the file
* Go to your Flow, in the input tab
* Click "GetSchema" button. This will sample the data for the number of seconds specified and infer the schema of the incoming data. This will update your Flow's schema to match the generated data<br />
 ![Schema](./tutorials/images/GetSchema.PNG)<br/>

* Click "Deploy" button to save and run the Flow. <br />
 ![Deploy](./tutorials/images/Deploy.PNG)<br/>

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 