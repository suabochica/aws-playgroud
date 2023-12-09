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
