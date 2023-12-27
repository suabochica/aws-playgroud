Instance Storage
================

An Elastic Book Store Volume (EBS) is a network drive you can attach to your EC2 instances while they run. It allows your instances to persist data, even after their termination. They can only be mounted to one instance at a time at the Certified Cloud Practitioner level; one EBS can be only mounted to one EC2 instance associate level.

A good analogy is associate an EBS Volume as a network of USB stick. The free tier enable us 30 GB of storage for general purpose per month.

Keep in mind that an EBS Volume is a network drive(i.e., not a physical drive). It uses the network to communicate the instance, which means there might be a bit of latency. Also it can be detached from EC2 instance and attached to another one quicklu.

For other side, the EBS Volume is locked to an Availability Zone (AZ), so an EBS Volume in `us-east-1a` cannot be attached to `us-east-1b`. To move a volume across, you first need to snapshot it.

Lastly, you have a provisioned capacity. You get billed for all the provisioned capacity and you can increase the capacity of the drive over time.

The next diagram is and example of EBS Volume distribution:

![EBS Volume example](../assets/images/03A-ebs-volume-example.png)