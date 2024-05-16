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
