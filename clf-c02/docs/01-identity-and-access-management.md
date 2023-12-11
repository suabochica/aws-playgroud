(IAM) Identity and Access Management
====================================

The identity and access manage is a global service in AWS to define user and groups. A root account is created by default and should not be user or shared. The users are people withing your organization, and can be grouped. Groups only contain users, not other groups. Users do not have to belong to a group, and user can belong to multiple groups. The next images is an example of definition for user and groups in your enterprise under AWS:

![User and Groups](../assets/images/01A-user-and-groups.png)

The users or groups are assigned in JSON documents called policies. Below we have an example of a policy.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:Describe",
            "Resource": "*",
        },
        {
            "Effect": "Allow",
            "Action": "elasticloadbalancing:Describe",
            "Resource": "*",
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricsStatistics",
                "cloudwatch:Describe",
            ],
            "Resource": "*",
        },
    ]
}
```

These policies define the permissions of the user on the AWS ecosystem. In AWS is recommended apply the **least privilege principle**: do not give more permissions that a user needs.

So it is time to hands on to create a user and assigned it to a group. Keep in mind the it is not a good practice work with the root user of AWS. So let's create and user called "sergio" with the option _I want to create an IAM user_ and assigned it a password. Next add permission to this user via a group that it will called "admin-group" and it will use the policy name _Administrator Access_. Once the user "sergio" is associated to the group "admin-group" you can add some tags. Tags are used in AWS resources to help to identify, organize or search these resources. In short it is metadata in key-value pairs. For this case we can add the key "Department" with the value "Engineering" to identify that the user "sergio" is part of the Engineering Department.

Once created the user and associated to the board lets create an alias to the AWS account. Navigate to the **Dashboard** section and edit the Account Alias in the AWS Account card, to use a legible alias like "aws-sergio-v0" instead of an account id like "165331541142" as shown the next image":

![AWS Account Alias](../assets/images/01B-aws-account-alias.png)

Then copy the URL in the "Sign-in URL for IAM user in this account", open the browser in private mode, paste this URL an access to IAM with the user and the password created previously. Now, you should see in your windows with the browser, the access as a root account and the access as an IAM user.
