# awsretryspringbootcall


add to role to be able to add vpc

for lambda to have internet access you need to setup NAT.  in aws from VPC select create VPC, 
choose VPC and more, choose 2 Azs, 2 private subnets, importantly choose 1 Natgateway in 1 AZ.
When deploying lambda, deploy to private subnets. The Nat should route traffic through public subnets. 
This should allow lambda access to AWS resource as well as internet access.

{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "Statement1",
"Effect": "Allow",
"Action": [
"ec2:DescribeNetworkInterfaces",
"ec2:CreateNetworkInterface",
"ec2:DeleteNetworkInterface",
"ec2:DescribeInstances",
"ec2:AttachNetworkInterface"
],
"Resource": "*"
}
]
}

add VPC to allow external access