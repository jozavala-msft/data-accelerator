### Data Accelerator for Apache Spark - Open Source
Data Accelerator for Apache Spark simplifies on-boarding to Streaming of Big Data.  It offers a rich, easy to use experience to help with creation, editing and management of Spark jobs on Azure HDInsights while enabling the full power of the Spark engine. 
<p align="center"><img style="float: center;" src="https://github.com/Microsoft/data-accelerator/wiki/tutorials/images/readme2.png"></p>

Data Accelerator offers three level of experience
 - The first requires no code at all, using rules to create alerts on data content.  
 - The second allows to write SQL-like query with additions like time window, accumulator and more
 - The third enables integrating custom code either in Scala or via Azure functions

Data Accelerator is used in production at Microsoft to serve terabytes of streamed data every day. This project will be updated regularly with new features, fixes and documentation updates.  You can get started locally for Windows, macOs and Linux on the [[Local-mode-with-Docker]].  To deploy to Azure, you can use the ARM template; see instructions here [[Cloud-deployment]].

The [`data-accelerator`](https://github.com/Microsoft/data-accelerator/) repository contains everything needed to set up an end-to-end data pipeline.  There are many ways you can participate in the project:
 - [Submit bugs and requests](https://github.com/Microsoft/data-accelerator/issues)
 - [Review code changes](https://github.com/microsoft/data-accelerator/pulls)
 - [Review documentation](wiki) and make updates ranging from typos to new content.

# Getting Started

You can get started with Data Accelerator for Spark in 5 minutes by using a Docker image.  Please see the [[Local-mode-with-Docker]] to obtain the image then, follow the following steps to create your first data pipeline or Flow.<br/>

Once you are ready to deploy to Azure, you can use the deployment scripts and ARM template to instantiate the infrastructure and apply the right settings.  See the [[Cloud-deployment]].  Data Accelerator for Spark runs on the following:
 - HDInsights with Spark 2.3
 - Service Fabric running DotNet Core 2.1
 - App Service with Node 10.6

See the [wiki](https://github.com/Microsoft/data-accelerator/wiki) pages for further information on how to build, diagnose and maintain your data pipelines built using Data Accelerator for Spark.

# How to Engage, Contribute and Give Feedback
Some of the best ways to contribute are to try things out, file issues, join in design conversations, and make pull-requests.

* [Download the latest stable or in-development releases](download)
* [Build Data Accelerator source code](CONTRIBUTING.md#build-and-run)
* Check out the [contributing page](CONTRIBUTING.md) to see the best places to log issues and start discussions.

Please also see our [Code of Conduct](CODE_OF_CONDUCT.md).

# Feedback

 - Ask a question on [Stack Overflow](https://stackoverflow.com/questions/tagged/data-accelerator)
 - Request new features on [GitHub](CONTRIBUTING.md)
 - Open a new issue on [GitHub](https://github.com/Microsoft/data-accelerator/issues)
Reporting security issues and bugs

# Security issues
Security issues and bugs should be reported privately, via email, to the Microsoft Security Response Center (MSRC) secure@microsoft.com. You should receive a response within 24 hours. If for some reason you do not, please follow up via email to ensure we received your original message. Further information, including the MSRC PGP key, can be found in the Security TechCenter.

# License
This repository is licensed with the [MIT](LICENSE) license.