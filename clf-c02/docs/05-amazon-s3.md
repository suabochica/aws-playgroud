Amazon S3
=========

Amazon S3 is one of the main building block of AWS, and it is advertised as _infinitely scaling_ storage. Many websites use it as a backbone and a lot of AWS services use it for integration, so it is important have a step by step approach to S3.

There are several use cases for Amazon S3:

- backup and storage.
- disaster recovery.
- archive.
- hybrid cloud storage.
- application hosting.
- media hosting.
- data lakes.
- software delivery.
- static website.

To mention some specific cases, Nasdaq stores 7 years of data in S3 glacier and Sysco runs analytics on its data and gain business insights.

The key elements of Amazon S3 allows to store **objects/files** in **buckets/directories**. The buckets must have a _globally unique name_  across all regions and all accounts and they are defined at the region level. S3 looks like a global service but buckets are created in a regions using a specific naming convention.

In the other hand, we have objects. They have a key that is the full path (e.g., `s3://my-bucket/my_file.txt`). The key is composed of a prefix (directory path) and an object name (file name). There is no concept of directories within buckets but the UI will trick you to think otherwise. The object values are the content of the body, they have a maximum size of 5000 GB. So, if you pass this limit you must use a _multi-part upload_. They also are compose of metadata, tags and if you enable it versioning.

