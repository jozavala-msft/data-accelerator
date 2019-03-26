Data Accelerator is an end to end data pipeline used internally at Microsoft for collecting, processing and reporting telemetry data for several products, operating at Microsoft scale. It's capabilities of processing data without writing any code and simple SQL interface for complex processing has made big data processing accessible to people from different roles and backgrounds (data engineers, data scientists, developers, program managers, etc.), enabling them to customize the processing and create insights, alerts and reports to meet their needs. 

Data Accelerator is built on Spark and supports streaming and batch processing. We are happy to open source all of the tooling and services we have built and can't wait to see how you put it to use for your scenarios! As Data Accelerator continues to be a critical pipeline for us, we will continue to develop in the open and welcome partnering with you and looking forward to your contributions and feedback. 

**Data Accelerator enables 3 levels of processing:**
- **No code experience** to set up end to end pipelines with alerting, tagging and data processing
- When that is not enough, you can do more complex processing in **SQL**, without having to worry about Java or Scala, etc.
- You can of course break the glass and go down to Scala if you so wish, by creating **user defined functions** and extensions.

**Data Accelerator supports features you would come to expect, and more, for your scenarios such as **
- Referencing data
- Windowing functions (interval for processing, look back window, etc.)
- Accumulator (to maintain state over stream processing)
- Writing UDFs, UDAFs
- Calling Azure functions and integrating with ML
- and more.

Data Accelerator also enables **Live Query**, a feature that allows you to validate your queries in seconds by running against a sample of the incoming streaming data. This feature alone helps save hours of tedious work otherwise required when standing up end to end big data pipelines. 

**Inferring schema** of the incoming data automatically is another feature that can save hours of tedious work involved in creating schema that encapsulates all of the data coming across all clients. 

As you [learn](tutorials) to use Data Accelerator, hopefully, you will find the tools we have found useful over time, useful too. 

Finally, to make it easy for you to try out Data Accelerator, without deploying anything to the cloud is to try it [locally](Local-mode-with-Docker). We have packaged the tools and service in a docker container so you can try out easily locally. While the local deployment does not have all of the features available in the full cloud deployment, it will give you a quick idea of the pipeline. 