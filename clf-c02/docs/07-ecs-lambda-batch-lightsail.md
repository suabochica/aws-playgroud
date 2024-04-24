Other Compute Services
======================

What is Docker?
---------------

Docker is a software development platform to deploy application. The applications are package in **containers** thath can be run on any operating system. The application run the same, regardless of where ther are run:

- Any machine.
- No compatibility issues.
- Predictable behavior.
- Less work.
- Easier to maintain.
- Works with any language, any OS and on any technology.

A big win of docket is that you can scale containers up and dow very quickly (i.e., seconds). The next image is a example of a several docker containers with different technologies on a EC2 instance server.

![Docker on EC2](../assets/images/07A-docker-on-ec2.png)

The docker images are stored in docker repositories that can be:

- Public: Docker hub.
- Private: Amazon Elastic Container Registry.

Docker is a sort of a virtualization technology, but not exactly. The resources are shared with the host in the case of virtual machines, while with docker many container are on one server. The next image illustrates the difference between a virtual machine and docker.

![Virtual Machine vs Docker](../assets/images/07B-vm-vs-docker.png)

> Note: This is a light introduction to docker but is necessary to get into the amazon ECS.

Elastic Container Service
-------------------------

Elastic Container Service (ECS in short) launch docker containers on AWS. Here you must provision and maintain the infrastructure of only EC2 instances. AWS takes care of starting/stopping containers ad it has integrations with the Application Load Balancer. The next diagram shows a structure of ECS.

![ECS](../assets/images/07C-ecs.png)

Fargate
-------

Fargate also works to launch docker container on AWS but it is much simpler because you do not provision the infrastructure because ther is no EC2 instance to manage. It is serverless offering and AWS just runs containers based on the CPU/RAM you need. The next image show the distribution of docker containers with fargate.

![Fargate](../assets/images/07D-fargate.png)

Elastic Container Registry
--------------------------

Elastic Container Registry (ECR in short) is a private docker registry on AWS to store your docker image. So they can be run by ECS or Fargate as shown the next illustration:

![ECR](../assets/images/07E-ecr.png)
