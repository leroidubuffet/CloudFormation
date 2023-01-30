# AWS CloudFormation Templates and tutorials in yaml

- **cloudformation_notes.yaml** contains notes about the structure and syntax of CloudFormation templates with applied examples.

Overview
This CloudFormation template provides a sample architecture for creating a VPC with DNS and public IPs enabled. It includes information on the different sections of a CloudFormation template, CLI commands for launching and deleting a stack, and additional sources for further learning.

Template Structure
A CloudFormation template is composed of the following sections:

- Template version
- Description (optional)
- Metadata (optional)
- Parameters (optional)
- Mappings (optional)
- Conditions (optional)
- Transform (optional)
- Resources (required)
- Outputs (optional)

### CLI Commands

To launch the CloudFormation stack:
```aws cloudformation create-stack --stack-name <demo-stack> --template-body file://demo.yaml```

To delete the CloudFormation stack:

```aws cloudformation delete-stack --stack-name <demo-stack>```
Additional Resources
AWS CloudFormation 101: Introduction
AMI Mappings in CloudFormation
Creating an Auto Scaling Group in AWS CloudFormation
AWS CloudFormation User Guide: Walkthrough: Cross-Stack References
How to Create a VPC and Auto Scaling Group in CloudFormation


- **temp1.yaml** contains a template that includes a VPC with 2 public subnets in different Availability Zones, an Auto Scaling Group with a minimum
  of 2 and a maximum of 4 Amazon Linux 2 instances (t2.micro). The EC2 instances have Nginx installed using a User Data script and a public IP assigned. There instances belong to a Security Group with an inbound rule allowing access through port 80 from any IP. 
- **temp1a.yaml** is a template that only deploys the network resources of temp1.
