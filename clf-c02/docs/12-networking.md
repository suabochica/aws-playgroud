Networking
==========

Virtual Private Networks (in short VPC) is something you should know in depth for the AWS certified solution architect associate and AWS certified sysops administrator. At AWS certified cloud practitioner level you should know about:

- VPC, subnets, internet gateways and NAT gateways.
- Security groups, network ACL, VPC flow logs.
- VPC peering, VPC endpoints.
- Site to site VPN and direct connect.
- Transit gateway.

It is important look at the _default VPC_ created by AWS.

IP Addresses in AWS
-------------------

The internet protocol (in short IP) has two versions: 4 and 6. The version 4 enables 4.3 billion addresses and it can be public and private. Public means that can be used on the internet. By default, an EC2 instance gets a new public IP address every time you stop then start it. Private is used on private network (Local Area Network) such as AWS networking (e.g., 192.168.1.1).

There is Elastic IP that allows you to attach a fixed public IPv4 address to EC2 instance. However, all public IPv4 on AWS will be charged **$0.005** per hour including elastic IP. The free tier is about 750 hours usage per month.

The version 6 enables 3.4 x 10^38 addresses. Every IP address is public in AWS, this means that the is no a private range. It is free in AWS (e.g., 2001:db8:3333:4444:cccc:dddd:eeee:ffff).
