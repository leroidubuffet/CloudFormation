# AWS CloudFormation Templates and tutorials in yaml.

- **cloudformation_notes.yaml** contains notes about the structure and syntax of CloudFormation templates with applied examples.
- **temp1.yaml** contains a template that includes a VPC with 2 public subnets in different Availability Zones, an Auto Scaling Group with a minimum
  of 2 and a maximum of 4 Amazon Linux 2 instances (t2.micro). The EC2 instances have Nginx installed using a User Data script and a public IP assigned. There instances belong to a Security Group with an inbound rule allowing access through port 80 from any IP. 
- **temp1a.yaml** is a template that only deploys the network resources of temp1.