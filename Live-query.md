It can be very frustrating when one writes some queries, deploys the Spark job to only later find out that there was a type or a missing semi-colon. This can easily take up 10 to 15 minutes for each change requiring deployment, waiting for job to run, going through logs to determine why job failed, etc. To tighten this development loop, and reduce the time from minutes to seconds, Data Accelerator supports "Live Query".

Imagine, what if you could run your query against a sample of the incoming streaming data and validate the output in seconds? Now you can! In this tutorials