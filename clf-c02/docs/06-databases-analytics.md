Databases & Analytics
=====================

Storing data on disk (e.g., EFS, EBS, EC2 instance store or S3) have their limits. Sometimes you will need to have a structure in the data to build **indexes** and enable **queries** or **search** through the data. For this use case, it is better store the data in a database. Here you can define relationships between your datasets.

Database are optimized for a purpose and come with different feature, shapes and constraints.

You will find to types of databases:

- SQL (i.e., Structured Query Language) databases.
- No-SQL databases.

SQL databases (a.k.a relational databases) looks like excel spreadsheets with links between them. They have a key feature and is that you can use the SQL language to preform queries or lookups over the database. The next image is an example of a relational database:

![SQL Database](../assets/images/06A-sql-databases.png)

No-SQL databases (a.k.a non-relational databases) have a purpose build specific data models with flexible schemas for building modern applications. An schema is the shape of the data. They offer benefits like flexibility, scalability, high-performance and highly functional. As example we have a JSON model as shown below:

![No-SQL Database](../assets/images/06B-no-sql-database.png)

They can be key-value pairs, documents, graphs, in-memory or search databases.

AWS offers use to manage different databases with the next benefits:

- Quick provisioning.
- High availability.
- Vertical and horizontal scaling
- Automated backup and restore.
- Operations and upgrades
- Operating system patching
- Monitoring and alerting.

> Note: many database technologies could run on EC2, but you must handle yourself the resiliency, backup, patching, availability, and other features of your database.

Amazon RDS
----------

RDS stands for Relational Database Service. So this is a managed database service for databases that use SQL as query language. It supports: Postgres, MySQL, MariaDB, Oracle, Microsoft SQL Server, IBM DB2 and Aurora. Aurora is proprietary of AWS and we will review more about it later. So, with this service we can:

- Automated provisioning.
- OS patching.
- Continuos backups and restore to specific timestamp (i.e., point in time restore).
- Monitoring dashboards.
- Read replicas for improved read performance.
- Multi AZ setup for disaster recovery.
- Maintenance windows for upgrades.
- Scaling capability.
- Storage backed by EBS.

> Note: You cannot use SSH (Secure Shell Protocol) into your RDS instances.

The next image summarizes the RDS solution architecture:

![RDS Solution Architecture](../assets/images/06C-rds-architecture.png)

Now, let's talk about **Aurora**, that is a proprietary not open sourced technology from AWS that only supports Postgres and MySQL for offer a AWS cloud optimized service and claims 5x performance improvement over MySQL on RDS and 3x of performance on RDS. Aurora is not in the free tier and storage automatically grows in increment of 10GB, up to 128TB. It cost 20% more than RDS, but it is mor efficient.

There is also **Aurora Serverless** that is and automated database instantiation and auto-scaling based on actual usage. No capacity planning is needed and it is least management overhead. You can pay per second to be more cost effective.

The use cases are: good for infrequent, intermittent or unpredictable workloads

RDS Deployment
--------------

We have three types of deployments in RDS:

1. Read replicas.
2. Multi-AZ.
3. Multi-Region.

**Read replicas** help us to scale the read workload of the database. You can create up to 15 read replicas of the main RDS. Keep in mind that the data is only written to the main database. The next image illustrates the distribution of a read replicas deployment:

![Read Replicas](../assets/images/06D-read-replicas.png)

**Multi-AZ** is used to _failover- in case of availability zone outage, guarantee high availability in the database. The data is only read/written to the main database and you can only have 1 other AZ as failover. Below an example of a multi-AZ deployment:

![Multi-AZ](../assets/images/06E-multi-az.png)

Finally, we have the **multi-region** deployment. His use case is for _disaster recovery_ in case of a region issue. Due to his distribution you will have _local performance_ for global reads, but, you will pay with replication cost. The following image show a map of a multi-region deployment.

![Multi-Region](../assets/images/06F-multi-region.png)
