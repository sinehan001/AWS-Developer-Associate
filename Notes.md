# AWS Important Key Notes

## IAM(Identity & Access Management)

- **Users**: Individuals or entities with unique credentials to access AWS resources, such as servers or databases, enabling them to perform actions within defined permissions.

- **Group**: Collections of users sharing similar roles or responsibilities, facilitating centralized management of permissions by assigning policies to the group rather than individual users.

- **Policy**: Sets of permissions defining what actions users, groups, or roles can perform on AWS resources, ensuring security and control over resource access.

- **Permissions**: Granular rules within policies that dictate the actions allowed or denied for users, groups, or roles when interacting with AWS resources, managing access levels effectively.

- **Roles**: Temporary sets of permissions assigned to AWS resources or services, enabling them to perform specific actions on behalf of other users or services, enhancing security and flexibility in resource management.

## Cognito

- **User Pool** - Authentication purpose, example signup & signin
- **Identity Pool** - Authorization purpose example storing user data to s3 bucket (or) Kinesis Data Stream.

## DynamoDB

#### Start up
- 4KB read request per second for an item
- 1KB write request per second for an item
- Maximum item size is 400KB.
- On-Demand & Provisioned(40K), Reserved Capacity(1 Million) & also increase quota limit by contacting AWS Support.
- GSI(Global Secondary Index)

#### Tables
- initial quota of 2,500 tables per AWS Region.
- Maximum of 10,000 tables per AWS Account.
- **Global Table** - available for multiple regions.
- **local Table** - available in single AZ(Availability Zone).


## ECS(Elastic Container Service) & EKS(Elastic Kubernetes Service) & ECR(Elastic Container Registry)

#### Start up
- Application deployment service

#### ECR
- ECR - Docker Registry, upload your image to the ECR.
- Pre-Defined AMI also available to build the image.

#### ECS
- ECS Cluster - logical group of tasks within same region(multiple AZ)
- Container Instance - EC2 Instance running the ECS agent.
- Task Definition to create & run the Docker container
- ECS Services to maintain the desired count of Tasks
- Major two type of ECS are available
- **AWS Fargate** - Serverless container(Don't need to manage EC2 Instance, fully automated), Elastic load balancer, Auto Scaling Group
- **AWS EC2 Instance** - Manually need to deploy, maintain & patch up the application
- **ECS Task Placement Strategies**
    - **binpack** - place tasks on least amount of CPU & Memory. Reduces number of instances used.
    - **random** - place tasks randomly 
    - **spread** - place tasks based on specific values like cpu usage > 90%.
![ECS](https://platform9.com/wp-content/uploads/2017/07/ecs-architecture-1800x1288.png)

#### EKS
![EKS](https://cio.ucop.edu/wp-content/uploads/2020/08/AWS-Kubernetes-diagram-757x1024.png)

## Elastic Beanstalk(EB)

- Elastic Beanstalk is a pre-configured EC2 server that can directly take up your application code and environment configurations and use it to automatically provision and deploy the required resources within AWS to run the web application.
- Unlike EC2 Instance as Infrastructure as a service(Iaas), Elastic Beanstalk is a **Platform as a Service(Paas)**.
- There are two types of Environments are available.
    - **Web Server Environment** - Directly upload & Deploy your web application from pref-defined Servers such as Node js, Python, Java, PHP, Ruby, .NET, Docker, Tomcat etc.,
    - **Worker Environment** - Run worker Applications such as Data Streams & Analytics for handling Big Data, can setup ASG ELB MinMax Instance Limit, etc.,
- **Update, Monitoring & Logging** - There are five types of Deployment policies are there to rollover the app updates.
    - **All at Once**: Deploys the new version to all instances simultaneously, resulting in minimal downtime but potentially impacting availability if issues arise.

    - **Rolling**: Gradually replaces instances in batches, minimizing downtime and ensuring availability by maintaining a certain number of healthy instances throughout the deployment process.

    - **Rolling with Additional Batch**: Similar to rolling, but launches additional instances to handle the new version alongside the existing ones, further reducing downtime and increasing capacity during deployment.

    - **Immutable**: Creates a new set of instances with the new version and swaps them with the existing ones after successful deployment, ensuring a clean and predictable environment but requiring more resources and time.

    - **Traffic Splitting (or) Blue/Green**: Sets up a separate environment ("green") with the new version alongside the existing one ("blue"), allowing for testing and validation before routing traffic to the green environment, ensuring zero downtime and easy rollback if issues occur.

![EB](https://webmobilez.com/wp-content/uploads/2020/04/image-50-1024x484.png)

## AppSync
- **Usage**: Exclusively for Mobile & Web apps with real-time dashboard, offline Sync, etc., & Uses Schema to pre-defined the API Output.
- **GraphQL API**: AppSync facilitates easy development of GraphQL APIs, enabling flexible querying and manipulation of data.
- **Real-time Data**: It supports real-time subscriptions, allowing applications to receive instant updates as data changes.
- **Data Source Integration**: Integrates seamlessly with various data sources like DynamoDB, Lambda, and HTTP endpoints, providing unified access to diverse data.
- **Managed Service**: AppSync is a fully managed service, handling scalability, security, and performance aspects of API operations.
- **Connected Services** - DynamoDB or any other Federal Identity Provider.

## AWS Amplify:

- **Backend Services**: Amplify simplifies integration with AWS backend services such as authentication (Cognito), storage (S3), and APIs (AppSync, API Gateway).
- **Client Libraries**: It offers easy-to-use client libraries for popular frontend frameworks, streamlining integration with backend services.
- **Authentication & Authorization**: Provides built-in authentication and authorization features powered by Cognito, including user management and access control.
- **UI Components**: Amplify offers pre-built UI components(Templates) for common application features, accelerating frontend development and enhancing user experience.

## AWS CloudFormation

AWS CloudFormation is a powerful service for managing AWS infrastructure resources through code. Here's a quick overview of its key concepts:

- **Infrastructure as Code (IaC)** - CloudFormation allows you to define and manage AWS infrastructure resources using JSON or YAML templates, enabling automated provisioning and updates.

- **Declarative Templates** - Templates specify the desired state of your AWS infrastructure in a declarative manner, defining resources, configurations, and dependencies.

- **Design Custom Template** - We can view the template structure in Design Viewer & also create our custom template in the Designer.

- **Resource Provisioning** - CloudFormation automatically provisions and configures resources based on the template, handling dependencies and ensuring consistent deployment.

- **Stack Management** - Resources provisioned by CloudFormation are organized into stacks, representing a collection of related resources managed as a single unit.

- **Change Sets** - Before modifying a stack, CloudFormation generates a change set, providing a preview of proposed modifications and their potential impact.

- **Version Control & Rollback** - Templates can be version-controlled using Git or other VCS tools, and CloudFormation supports rollback capabilities for easy recovery from failed deployments.

- **Integration with AWS Services** - CloudFormation integrates seamlessly with various AWS services, enabling the provisioning of a wide range of resources such as EC2 instances, RDS databases, S3 buckets, Lambda functions, and more.

- **Infrastructure Management** - CloudFormation offers a centralized approach to managing and updating infrastructure, ensuring consistency, scalability, and repeatability across environments.

- **Automation & Orchestration** - CloudFormation facilitates automation and orchestration of complex AWS deployments, streamlining the deployment process and reducing manual intervention.

- **Cost Management** - By defining infrastructure as code, CloudFormation helps optimize resource utilization and cost management, providing visibility into resource dependencies and configurations.

