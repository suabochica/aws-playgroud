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

![Diagram for a record](../assets/images/09A-diagram.png)

![Simple and weighted policies](../assets/images/09B-simple-weighted.png)

![Latency and failover policies](../assets/images/09C-latency-failover.png)
