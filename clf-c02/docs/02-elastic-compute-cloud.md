Elastic Compute Cloud (E2C)
===========================

A good idea is to set up a billing budget to know when we go over spending money on AWS and get alerted in case of we are near to overpass our budget. To achieve that please activate the **IAM user and role access to Billing information** from your account user to enable that the IAM users can access to billing information. Then, log in as IAM user with admin permission and click in the **Billing and Cost Management** option of the dropdown of you AWS account. The next image illustrate this step:

![Billing and Cost Management](../assets/images/02A-ec2-budget.png)

In the Bills section you will have a dashboard with the summary of the cost that you have from the use of AWS. In the other hand, you can define a budget from a template to set the criteria about the expected cost to spend using AWS monthly. For example I expect to spend 10 USD monthly for the use of E2C. When you define a budget, you should share an email, and when the budget be near to the limit, AWS will alert you that you are near to exceed the cost limit.

EC2 Basics
----------

Elastic Compute Cloud (a.k.a EC2) is a way to do Infrastructure as a Service on AWS and is one of the most popular tools offering by AWS. It is not just one service, it is compose of the next things a high level:

- Renting virtual machines (EC2).
- Storing data on virtual drives (Elastic Bucket Storage).
- Distributing load across machines (Elastic Load Balances).
- Scaling the services (Auto Scaling Group).

Knowing how to use EC2 in AWS is fundamental to understand how the cloud works. In that order, below are the specifications that we can define over the EC2 instances:

- Operating System e.g., Linux.
- CPU; Compute power and cores e.g., 4 cores.
- RAM; Random Access Memory e.g., 8 Gigabytes.
- Storage space e.g., 120 Gigabytes.
- Network card e.g., speed and public IP address.
- Firewall rules e.g., security group.
- Bootstrap script e.g., configure at first launch via EC2 user data.

Here is important highlight the bootstrap script. Bootstraping means launching commands when a machine start, and this command only run once at the instance first start. Is use to automate boot task such as; installing updates, installing software, download common files from Internet, etc. It runs with the root user and keep in mind that the more you add into your EC2 user data script the more your instance has to do at boot time.

The next image shows different types of EC2 instances:

![EC2 Types](../assets/images/02B-ec2-instances.png)

As you can see the `t2.tier` is part of the free tier, so it is a good option to start to play with EC2.
