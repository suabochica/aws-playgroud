Databases & Analytics
=====================

Storing data on disk (e.g., EFS, EBS, EC2 instance store or S3) have their limits. Sometimes you will need to have a structure in the data to build **indexes** and enable **queries** or **search** through the data. For this use case, it is better store the data in a database. Here you can define relationships between your datasets.

Database are optimized for a purpose and come with different feature, shapes and constraints.

You will find to types of databases:

- SQL databases.
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
