Deployments and Managing Infrastructure at Scale
================================================

Cloud Formation
---------------

Cloud formation is a declarative way of outlining your AWS infrastructure for any resources. So you can create templates like the next want:

- I want a security group;
- I want two EC2 instances using the security group;
- I want an S3 bucket;
- I want a ELB load balances in front to these machines.

Then, Cloud Formation create those for you in the **right order** with the exact configuration that you specify.

This offer us several benefits. The first one is **Infrastructure as Code** where no resources are manually created, which is excellent for control and the changes to the infrastructure are reviewed through code.

The second one is **cost**. Each resource within the stack is tagger with an identifier so you can easily see how much a stack cost you; You cans estimate the costs of your resources using the Cloud Formation template under a saving strategy. This means, you can specify that the development environment have an automated task to delete the templates at 5 PM and recreated at 8 AM safely.

The third one is **productivity**; the ability to destroy and re-create an infrastructure on the cloud on the fly, plus an automated generation of diagram for your templates! Also you approach is declarative so you no need to figure out ordering and orchestration.

The fourth is **don't re-invent the wheel** leverage existing template on the web in combo with their documentation.

Lastly, it **supports (almost) all AWS resources**; Everything we will see until now is supported and you can use custom resources for those that are not supported.

The next image groups a WordPress cloud formation stack with all the resources and the relations between the components.

![Stack Designer](../assets/images/08A-stack-designer.png)

Cloud Development Kit
---------------------

Cloud Development Kit (CDK in short) is a tool to define you cloud infrastructure using a familiar programming language. These code is compiled into a CloudFormation template in a JSON/YALM format. Therefore you can deploy infrastructure and application runtime code together, making this combination great for lambda function and docker containers in ECS/EKS.

The next diagram summarize how works the CDK:

![CDK Application](../assets/images/08B-CDK-app.png)

The next example is a code infrastructure definition in TypeScript:

```js
export class MyEcsConstructStack extends core.Stack {
  constructor(
    score: core.App,
    id: string,
    props: core.StackProps
  ) {
    super(scope, id, props)
  }

  const vpc = new ec2.Vpc(this, "MyVpc", {
    maxAzs: 3
  });

  const cluster = new ecs.Cluster(this, "MyCluster", {
    vpc: vpc
  });

  new ecs_patterns.ApplicationLoadBalancedFargateService(this, "MyAL", {
    cluster: cluster,
    cpu: 512,
    desiredCount: 6,
    taskImageOption: {}
    memoryLimitMiB: 2048,
    publicLoadBalance: true
  });
}
```
