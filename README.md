# Three Tier LAMP CloudFormation IAC

This CloudFormation Stack can be created from the console or from the AWS CLI.
If stack is created from the console then resources will be created in the region shown in the upper right.
If stack is created from the AWS CLI then the region flag must be used or the stack will be created in the AWS default region (us-east-1).
Example of creating stack from the AWS CLI:

aws --region us-east-2 cloudformation create-stack --stack-name myteststack --template-body file://creating-lamp-vpc.json --parameters ParameterKey=KeyPairName,ParameterValue=us-east-2

This template will only use the first two AZs of a region.

This CloudFormation Template will create:
- VPC
- Public and Private Subnets in two AZs so four subnets
- Route Tables (Public and Private)
- Five Security Groups (ALB, Web, DB, NAT and Bastion)
- NAT Instance (source/destination check) or NAT Gateway
- EC2 Instances - Bastion, webserver, dbserver (requires EC2 key pair which are region based)
- ALB
- Auto Scaling
