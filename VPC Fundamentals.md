

Introduction:


VPC - Virtual private cloud

VPC, subntes, internet gateways & NAT gateway
Security Group, Network ACL (NACL), VPC flow logs
VPC peering, VPC endpoints
site to site VPN & Direct connect.


VPC : 

It is a private network to deploy your resources (regional resource)


Subnets:
tied ti an AZ

It allows you to partition your network inside your VPC (AZ resources)


A Public subnet are accessible from internet and private is not accessible from the internet 


To define access to the internet and between subnets , route table is used.

for default VPC there are no private subnets.

VPC CIDR Range are the range of IP allowed in your VPC.

Internet Gateway helps our VPC instances to connect withthe internet.

Public Subnet have a route to the internet gateway, hence helping it connect with the internet.

NAT Gateway ( managed by AWS) and NAT instances ( self managed) help connect your instance in private subnets to access the internet while remaining private.

the instance in the private subnet can rout e to NAT Gateway present in the public subnet, the NAT gateway then routes to the Internet Gateway, that can in return connet to the internet.


Network ACL:

A firewell which controls traffic from and to subnet.
Allow and Deny rules.
It is attached at the Subnet level.
Rules only include IP addresses.

Security Group:
Controls traffic to and from an ENI (Elastic network interface (ENI))/ EC2 instances.
only Allow rules.
Rules include IP address and other security groups.


VPC flow logs:

Capture inforamtion regarding all the IP traffic going into your interfaces:

 1. VPC flow logs
 2. Subnet flow logs 
 3. Elastic network Interface flow logs 

Helps troubleshoot and monitor connectivity:

  1. Subnets to Subnets
  2. Subnet to Internet 
  3. Internet to Subnets 

It also captures network information from AWS managed interfaces :  ELB,RDS,Aurora etc

The data can go to S3, cloud watch logs, kinesis data firehose.


VPC Peering:

It helps connect 2 VPC, privately using AWS network, making them behave as if they belong to same network

The CIDR must not overlap for the VPC connected via peering 

VPC peering conenction is not transitive ( new connection has to be established betwen each VPC that needs to communicate)

eg. if VPC A and VPC B are connected via peering and VPC A and VPC C are connnected using peering the VPC B and VPC C needs to establish peering to communicate.


VPC endpoint :

It helps achieve lower latency and enhance security.
It helps connect to AWS services using private network instead public network.i.e. if your instance is in a VPC private network and the wants to access the AWS service we use Endpoints


There are 2 Endpoints: (only used within VPC)

1. VPC endpoints gateway: S3 & DynamoDB
2. VPC endpoint interface: for all the other services.



Site to site VPN 

1. It is used to connect the on premises VPN to AWS 
2. The connection is encrypted and goes over the public internet

Direct Conect DX

1. It uses a physical connection between on- premises and AWS 
2. It is private fast and secure
3. It takes 1 month to establish 

Site-to-site VPN and Direct Connect cannot access VPC endpoints


3 tier solutoin architecture
1. public subnet 
2. private subnet
3. data subnet

other architectures:

LAMP stack
wordpress onAWS







