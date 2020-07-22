
This project is designed to meet the requirements set out for the AWS DevOps test.

# AWS DevOps Test

This project contains a Cloudformation template that can be used to define an application stack in the AWS ap-southeast-2 region. The stack:
- Applies AWS best practices in solution architecture and security. The stack is deployed on all availability zones in the region. It uses a load balancer to accept incoming traffic, and then routes the traffic to an auto-scaled group of EC2 instances, that have an Apache Web Server installed an running.
- Uses the following AMI: [https://aws.amazon.com/marketplace/pp/Amazon-Web-Services-Amazon-Linux-AMI-HVM-64-bit/B00CIYTQTC](https://aws.amazon.com/marketplace/pp/Amazon-Web-Services-Amazon-Linux-AMI-HVM-64-bit/B00CIYTQTC)
- Serves a basic "Hello, World" webpage.
- Scales capacity to meed demand, measuring CPU and Network usage. The minimum number of nodes in the scaling group is set to 1, with the current maximum number of nodes set to 2.
- Manages unhealthy instances, through the use of an auto-scaling group.

The stack also includes notifications sent to the nominated email address on scaling events.

The template is based on the AutoScalingMultiAZWithNotifications template provided by Amazon. Documentation at the [AWS  CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) was used for syntax checking for modifications made to the template.

## Usage
To use the CloudFormation template, use the AWS CloudFormation tool, select the **Create stack** button, and choosing the **With new resources (standard)** option. Check the **Template is ready button**, and then upload the template. Click through to enter in the required parameters. This will create the stack, and also provide the URL as the output.

## Parameters
The following parameters need to be set for the creation of the stack. These should be entered when using the CloudFormation tool.

 - **InstanceType** - the type of EC2 instances that the auto-scaling group will generate. This defaults to t2.small.
 - **KeyName** - the name of an existing key pair that will be used to SSH to the instances if required.
 - **OperatorEMail** - a valid email address where the notifications about scaling events will be sent.
 - **SSHLocation** - the IP address range that can be used to SSH to the EC2 instances. This defaults to being completely open, but can be set to a specific IP range to limit it to a specific computer/server.
 - **Subnets** - the list of subnets that will be used.
 - **VpcId** - the existing VPC that will be used.