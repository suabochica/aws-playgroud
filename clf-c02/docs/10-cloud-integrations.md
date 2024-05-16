Cloud Integrations
==================

When we start to deploying multiple applications, they will inevitably need to communicate with one another. There are two patterns of application communication:

1. Synchronous communication, application to application.
2. Asynchronous / event based communication, application to queue to application.

The synchronous communication can be problematic if there are sudden spikes of traffic. In that case, it is better to decouple applications using some of the next 3 services:

1. SQS for queue model.
2. SNS for public/subscription model.
3. Kinesis for real time data streaming model.

These services can scale independently from the application.

Simple Queue Service
--------------------

Simple Queue Service is probably the oldest service of AWS. It is a fully managed service use to **decouple** applications. It scales from 1 message per second to 10,000s per second. It has a default retention of 4 days with a maximum of 14. There is no limit to how many messages can be in the queue and the message are deleted after they are read by consumers. It has a low latency with a publish and receiver rate below to the 10 milliseconds and  the consumers share the work to read messages for scaling horizontally.

The next image show how SQS works in a nutshell:

![SQS](../assets/images/10A-sqs.png)

This queue can be a first in firs out where the message are ordering in the queue to be processed in order by the consumer.
