Cloud Monitoring
================

Let's get a better picture of the performance of our cloud deployments. The main tool to monitor our uses in AWS is cloud watch. This tool offer us features for metrics and alarms.

Cloud watch provides metrics for every service in AWS. A metrics is a variable to monitor, they are going through the time so, they will have timestamps and you can visualize all your metrics at once in a dashboard similar to the next image:

![Metrics Dashboard](../assets/images/11A-cw-metrics.png)

According the services there are some important metrics to monitor. For example for EC2 instances you can have metrics over CPU utilization, status checks, network consume, etc. There are default metrics every 5 minutes and you have an option to detailed monitoring but it is expensive. For EBS volumes you can check the disk read/writes. In S3 buckets is available the bucket size bytes, number of objects and all the request. Maybe the most important is billing, so you can define a total estimated charge (only on us-east-1). You can define service limits and also push your own metrics.

Complementary, we have the alarms that are used to trigger notifications for any metric. Below we list some action over specific services:

- Auto scaling, increase or decrease EC2 instance desired account.
- EC2 action, stop terminate reboot or recover an EC2 instance.
- SNS, send a notification into a SNS topic.

There are several options like sampling, percentages, ranges and more. You can chose the period on which to evaluate an alarm e.g., create a **billing alarm** on the cloud watch billing metric. The alarms have 3 states: Ok, insufficient data and alarm.

Cloud Watch Logs
----------------

When you have an application running on any server, usually you want the application to write some text about how it is doing e.g., execute clean ups when the data is not necessary. All these log are collected an when you needs to troubleshoot something you go through the log file to see what the application did.

In cloud watch logs you can collect log from:

- Elastic Beanstalk: collection of logs from application.
- ECS: collection from containers.
- AWS Lambda: collection from function logs.
- Cloud Trail: based on filter,
- Cloud Watch log agents: on ec2 machines or on-premises servers.
- Route53: log DNS queries.

The key feature is that it enable real time monitoring of log and you can adjust the log retention.

Let's review in detail the cloud watch logs for EC2. By default, no logs from EC2 instances will go to cloud watch. You need to run a cloud watch agent on EC2 to push the log files you want. Make sure that IAM permissions are correct, and these log agent can be set up on-premises too. The next image summarizes this description.

![Logs](../assets/images/11B-cw-logs.png)
