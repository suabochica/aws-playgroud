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
