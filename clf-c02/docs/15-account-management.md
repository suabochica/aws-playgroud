Account Management, Billing & Support
=====================================

AWS Organizations
-----------------

This is a global service that allows to manage multiple AWS accounts via a master account. Their purpose is get cost benefits likes consolidate billing across all accounts via a single payment method, pricing benefits from aggregates usage or pooling of reserver EC2 instances for optimal savings.

There is an API available to automate AWS account creation and you can restrict the account privileges using Service Control Policies (SCP in short).

For big uses of AWS, you should think about the multi-account strategies. You can create accounts per department, per cost center, per dev/test/prod environment, based on regulatory restrictions using SCP, for better resource isolation (e.g., VPC), to have separate per-account service limits, isolated account for logging.

The range of options is extensive so you should decide between a multi account versus one account with multi VPC. Use tagging standards for billing purposes. Enable CloudTrail on all accounts, send logs to central S3 account send CloudWatch logs to central logging account.

Below, a image with 3 option to set the organization unit:

![Organization Units](../assets/images/15A-organization-units.png)

A possible distribution on these boxes is represented in the next diagram.

![Root OU](../assets/images/15B-root-ou.png)

With service control policies you can whitelist or blacklist IAM actions applied at the organization unit or account level but not to the master account. The SCP is applied to all the users and roles of the account, including root and does not affect service linked roles (service linked roles enable other aWS service to integrate with aWS organizations). It must have an explicit allow that by default does not allow anything and some use cases are:

- Restrict access to certain service (e.g., cannot use EMR).
- Enforce PCI compliance by explicitly disabling services.

Consolidated Billing
--------------------

This feature when is enabled provides 2  benefits:

1. Combine usage.
2. One bill.

You can combine the usage across all AWS accounts in the AWS Organization to share the volume pricing, reserved instances and savings plans discounts. In the next image we have an example where an account B has 5 reserved EC2 instances but only have 3 available. The remaining 2 instances are taken from the account A that has 6 available instances:

![Consolidated Billing](../assets/images/15C-consolidated-billing.png)

One bill is grouped for all the aWS accounts in the aWS organization.

Control Tower
-------------

Control Tower is an easy way to set up and govern secure and compliant multi account aWS environment based on best practices. It runs on top of aWS organizations to organize accounts and implement service control polices. Below, the benefits of control tower:

- automate the set up of your environment in a few clicks.
- Automate ongoing policy management using guardrails.
- Detect policy violations and remediate them.
- Monitor compliance through an interactive dashboards.

Resource Access Manager (RAM)
-----------------------------

RAM is used to share aWS resources that you own with other aWS accounts in the same organization to avoid resource duplication. It supports resources like Aurora, VPC  subnets, transit gateway, route 53, EC2, and more. The next image is an example of how the resources access manager works for 2 EC2 instance can access to the shared load balancer.

![RAM](../assets/images/15D-RAM.png)

Service Catalog
---------------

New users in AWs have too many options and may create stacks that are not compliant with the rest of the organizations. Some users just want a quick self-service portal to launch a set of authorized products pre-defined by admins. It includes virtual machines, databases, storage options and more. To handle this you can use the AWS Service Catalog as shown the next image:

![Service Catalog](../assets/images/15E-service-catalog.png)
