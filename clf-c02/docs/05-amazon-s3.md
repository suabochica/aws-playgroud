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

S3 Security
-----------

We can define the access to the buckets that stored in S3. One way is use a **user based** condition with IAM policies stablish which API calls should be allowed for a specific user from IAM. Another way is the **resource based** condition where we can define the next 3 scenarios:

1. Bucket policies; bucket wide rule from the S3 console, allowing cross account.
2. Object access control list (ACL); finer grain because is an object level. It can be disabled.
3. Bucket access control list (ACL); less common because is an bucket level. It can be disabled.

Keep in mind that an IAM principal can access a S3 object if they have the permissions or the resource policy allows it. Bu default there is a no explicit deny with IAM.

Besides, you can also **encrypt** objects in S3 via encryption keys.

The bucket policies are the most popular and they are recorded in a JSON file like the next one:

```json
{
    "Version": "2020-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",          // Allow or Deny
            "Principal": "*",           // The account to apply the policy
            "Action": [
                "s3:GetObject"          // Set of API to allow or deny
            ],
            "Resource": [
                "arn:aws:s3:::bucket/*" // Buckets and object
            ]
        }
    ]
}
```

So you can use a bucket policy to grant public access to the bucket, force objects to be encrypted at upload or grand access to another account. Below an image to illustrate the use of a bucket policy;

![Bucket policy](../assets/images/05A-bucket-policy.png)

A last option are the bucket settings for block public access. These settings were created to prevent company data leaks, so, if you know your bucket should never be public leave these on. they can be set at account level.

S3 Static Website Hosting
-------------------------

S3 can host static web sites and have them accessible on the Internet. The website URL will be defined by the region and some example are:

- http://{{bucket_name}}.s3-website-{{aws_region}}.amazonaws.com
- http://{{bucket_name}}.s3-website.{{aws_region}}.amazonaws.com

If you get a **403 Forbidden error**, make sure the bucket policy allows public reads.

S3 Versioning
-------------

You can version your files in Amazon S3. This feature is enable at the _bucket level_. The same key will change the "version". It is a best practice to version your bucket because it allows you to protect against unintended delete; now you have the ability to restore versions. And also is easy roll back to previous version of the file.

Some notes are important to share; any file that is not versioned prior to enabling versioning will have the `null` values. Suspending versioning does not delete the previous version of the file.

S3 Replication
--------------

The idea behind replication is have a S3 bucket in one region and a target S3 bucket in another region via asynchronous replication between these two bucket. To do it we must enable versioning in the source and the destination bucket. We can apply the replication in two flavors:

- Cross-Region Replication (a.k.a CRR): for compliance, lower latency, access, replication across accounts.
- Same-Region Replication (a.k.a SRR): for log aggregation, live replication between production and test accounts.

Their names are self-explanatory, and also we share their use cases. Then it's possible to have these buckets in different AWS accounts and copying happens asynchronously. So the replication mechanism happens in the background. To make replication work, you must give proper IAM permissions to the S3 service.
