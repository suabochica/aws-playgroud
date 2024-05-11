Global Infrastructure
=====================

A global application is an application deployed in multiple geographies. In AWS we have regions and edge location. This action offer us 3 benefits:

1. **Decreased latency:** Latency is the time it takes for a network packet to reach a server. It takes time for a packet from Asia to reach the US. Deploy your application closer to your users decrease latency offering a better experience.
2. **Disaster recovery:** If and AWS region goes down (earthquake, storms, power shutdown, etc.) you can fail over to another region and have your application still working. A disaster recovery plan is important to increases the availability of your application.
3. **Attack protection:** A distributed global infrastructure is harder to attack.

Index
-----

- **Route 53 (Global DNS)**: Great to route users to the closes deployment with least latency and disaster recovery strategies.
- **Cloud Front (Global CDN)**: Replicate part of your application to AWS edge locations and cache common request to decrease latency.
- **S3 Transfer Acceleration**: Accelerate global uploads and downloads into Amazon S3.
- **AWS Global Accelerator**: Improve global application availability and performance using AWS global network.

Route 53
--------

Route 53 is a managed domain name system (in short DNS). DNS is a collection of rules and records which helps clients understand how to reach a server through URLs. In AWS, te mos common records are:

- <www.google.com> -> 12.34.56.78 == A record in IPv4
- <www.google.com> -> 2001:0db8:85a3:0000:0000:8a2e:0370:7334 == A record in IPv6
- search.google.com -> <www.google.com> =- CNAME: hostname to hostname

The next diagram summarize how the DNS works.

![Diagram for a record](../assets/images/09A-diagram.png)

We have to keep in mind a high level of the routing policies explainend in the next 2 images.

![Simple and weighted policies](../assets/images/09B-simple-weighted.png)

![Latency and failover policies](../assets/images/09C-latency-failover.png)

Just a first one does not have a Health check. All the other ones have Health checks and they all serve different purposes. So, weighted routing policy is to distribute the traffic across multiple institute instances. Latency is to minimize latency and failover is to help with disaster recovery.

Cloud Front
-----------

Cloud front is a content delivery network (in short CDN). It improves read performance, because the content is cached at the edge location improving the user experience. It has 216 point of presence globally and offer us distributed denial of service (DDoS) protection because it is worldwide and works in combo with shield and AWS web application firewall.

Cloud front could have two origins; S3 bucket or custom HTTP origin. The S3 bucket origin is used for distributing files and caching them at the edge enhancing security with origin access control (OAC). Then we can use cloud front as an ingress to upload files to S3. The next image maps this description:

![Cloud Front S3](../assets/images/09D-cloudfront-s3.png)

For custom origin we can use cloud front as application load balancer, a copy of a EC2 instance or a S3 website enabling first the bucket as static.

![Cloud Front Custom Origin](../assets/images/09E-cfront-high-level.png)

With this description is common get confusions between cloud front and S3 cross origin replication. Below is a list with the difference between them.

Cloud front:

- Global edge network.
- Files are cached for a TTL.
- Great for static content that must be available everywhere.

S3 cross region replication:

- Must be set up for each region you want to replication happen.
- File are updated in near real-time.
- Read only.
- Great for dynamic content that needs to be available at low latency in few regions.

S3 Transfer Acceleration
------------------------

This service increase the transfer speed by moving the file to an AWS edge location which will forward the data to the S3 bucket in the target region. The next image map this behavior:

![Transfer Acceleration](../assets/images/09F-transfer-acceleration.png)

The cool thing is that there is a [S3 Transfer Accelerator tool](http://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html) to test.
