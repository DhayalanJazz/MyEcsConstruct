
# Creating an AWS Fargate service using the AWS CDK

An AWS Fargate service running on an Amazon Elastic Container Service (Amazon ECS) cluster that's fronted by an internet-facing Application Load Balancer from an image on Amazon ECR.

Amazon ECS is a highly scalable, fast, container management service that makes it easy to run, stop, and manage Docker containers on a cluster. You can host your cluster on a serverless infrastructure that's managed by Amazon ECS by launching your services or tasks using the Fargate launch type.

The Amazon ECS construct used in this AWS CDK app helps you use AWS services by providing the following benefits:

* Automatically configures a load balancer.

* Automatically opens a security group for load balancers. This enables load balancers to communicate with instances without you explicitly creating a security group.

* Automatically orders dependency between the service and the load balancer attaching to a target group, where the AWS CDK enforces the correct order of creating the listener before an instance is created.

* Automatically configures user data on automatically scaling groups. This creates the correct configuration to associate a cluster to AMIs.

* Validates parameter combinations early. This exposes AWS CloudFormation issues earlier, thus saving you deployment time. For example, depending on the task, it's easy to misconfigure the memory settings. Previously, you would not encounter an error until you deployed your app. But now the AWS CDK can detect a misconfiguration and emit an error when you synthesize your app.

* Automatically adds permissions for Amazon Elastic Container Registry (Amazon ECR) if you use an image from Amazon ECR.

* Automatically scales. The AWS CDK supplies a method so you can autoscalinginstances when you use an Amazon EC2 cluster. This happens automatically when you use an instance in a Fargate cluster.
In addition, the AWS CDK prevents an instance from being deleted when automatic scaling tries to kill an instance, but either a task is running or is scheduled on that instance.Previously, you had to create a Lambda function to have this functionality.

* Provides asset support, so that you can deploy a source from your machine to Amazon ECS in one step. Previously, to use an application source you had to perform several manual steps, such as uploading to Amazon ECR and creating a Docker image.

Screenshots of AWS Console after Deployment:
![My Fargate Cluster.](.\Images\MyFargateCluster.png)

![Health and Metrics.](.\Images\HealthMetrics.png)

![Deployed PHP Application.](.\Images\DeployedPHPApplication.png)

![Fargate Running Tasks.](.\Images\Tasks.png)

![CPU and Memory Utilization.](.\Images\CPU_Utilization.png)

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `npx cdk deploy`  deploy this stack to your default AWS account/region
* `npx cdk diff`    compare deployed stack with current state
* `npx cdk synth`   emits the synthesized CloudFormation template
