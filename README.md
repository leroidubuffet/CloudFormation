# AWS CloudFormation Templates and tutorials in yaml

### cloudformation_notes.yaml
Notes about the structure and syntax of CloudFormation templates with applied examples.

#### Description
This CloudFormation template provides a sample architecture for creating a VPC with DNS and public IPs enabled. It includes information on the different sections of a CloudFormation template, CLI commands for launching and deleting a stack, and additional sources for further learning.

#### Template Structure
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

#### CLI Commands

To launch the CloudFormation stack:

```aws cloudformation create-stack --stack-name <demo-stack> --template-body file://demo.yaml```

To delete the CloudFormation stack:

```aws cloudformation delete-stack --stack-name <demo-stack>```

#### Additional Resources

- [AWS CloudFormation 101: Introduction](https://www.observian.com/blog/aws-cloudformation-101-introduction)
- [AMI Mappings in CloudFormation](https://octopus.com/blog/ami-mappings-cloudformation)
- [Creating an Auto Scaling Group in AWS CloudFormation](https://towardsaws.com/creating-an-auto-scaling-group-in-aws-cloudformation-761b0f8c6364)
- [AWS CloudFormation User Guide: Walkthrough: Cross-Stack References](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/walkthrough-crossstackref.html)
- [How to Create a VPC and Auto Scaling Group in CloudFormation](https://blog.devgenius.io/how-to-create-a-vpc-and-auto-scaling-group-in-cloudformation-e3211b8ded5a)


### temp1.yaml 
#### Description
This CloudFormation template creates a VPC with 2 public subnets in different Availability Zones. It includes an Auto Scaling Group with a minimum of 2 and a maximum of 4 Amazon Linux 2 instances (t2.micro). The EC2 instances have Nginx installed using a User Data script and a public IP assigned. These instances belong to a Security Group with an inbound rule allowing access through port 80 from any IP.

#### Parameters
- `LaunchTemplateVersionNumber`: This parameter allows you to specify a version number for the launch template used in the Auto Scaling Group. The default value is 1.

#### Resources
The following AWS resources will be created:
- VPC
- Internet Gateway
- Public subnets
- Public route table
- Security group
- Launch template

#### Launch Template
The Launch Template used in the Auto Scaling Group includes the following:
- Network Interfaces: EC2 instances will be associated with a public IP and belong to the security group defined in this template.
- Placement: Tenancy is set to default.
- Image ID: Amazon Linux 2 AMI ID is used (ami-0b0dcb5067f052a63).
- Instance Type: t2.micro
- User Data: Nginx will be installed on the instances using a shell script.

#### Security Group
The security group allows inbound traffic on port 80 from any IP.

#### Requirements
To use this template, you will need the following:
- AWS account with necessary permissions to create CloudFormation stacks
- Access to Amazon Linux 2 AMI ID (ami-0b0dcb5067f052a63)

### temp1a.yaml
This AWS CloudFormation template creates a Virtual Private Cloud (VPC) with 2 public subnets in different Availability Zones. The following resources will be created:

- VPC
- Internet Gateway
- 2 Public Subnets
- Public Route Table

#### Parameters
- `LaunchTemplateVersionNumber`: A string that represents the version number of the launch template. Default value is 1.
- `VpcCidr`: The IP range (CIDR notation) for this VPC. Default value is 10.0.0.0/16.
- `PublicSubnet1CIDR`: The IP range (CIDR notation) for the public subnet 1. Default value is 10.0.0.0/24.
- `PublicSubnet2CIDR`: The IP range (CIDR notation) for the public subnet 2. Default value is 10.0.1.0/24.

#### Outputs
- `PublicSubnet1`: The ID of the subnet 1 to use for public web servers.
- `PublicSubnet2`: The ID of the subnet 2 to use for public web servers.
- `VPC`: The ID of the VPC.
