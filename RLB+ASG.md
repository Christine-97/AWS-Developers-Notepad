
What is Scalability & High Availability ?

  Scalability is the application/system ability to handle greater role by adapting.
  
  There are 2 types of scalability:
1. vertical 
2. horizontal (also called as elasticity)
  




1. vertical scalability:(scale up/down)

-It means increase in the size of the instance.
-There can always be a hardware limitation to vertical scaling.
-This is applied to non distributed systems.

  
2. horizontal scalability:(scale in/out)

-It means increase in the number of the instance.
-This is applied to distributed systems.




High availability:

1. High availability goes in hand with horizontal scalability
2. The goal is to survive data loss
3. when the same application is ran across multiple AZ






What is load balancing ?

  Load balancer are server that forward traffic to multiple servers

Why use an Elastic Load Balancer?
  
  It is a managed load balancer. AWS guarantees 24/7 uptime, upgrades,maintainence,high availability & also provides few configuration knobs.
  
   
Health Checks:

 1. crucial for LB
 2. helps the LB to know which instances is up and running for traffic control
 3. health checks are done on ports and routes
 4. if response from HC is not 200 (okay) then the instance is unhealthy
  
  
 Types of Load blancer on AWS:
 
 There are 4 types of managed Load balancer:
 
 
1. Classic Load Balancer - deprecated 
2. Application Load Balancer - HTTPS, HTTP, Websocket
3. Network load balancer - TCP, TLS, UDP
4. Gateway load balancer - 3 N/W layers (IP protocol)


Security around load balancer 

The inbound Traffiic to the load balancer is routed to the instance, hence the traffic to the instance is only accepted as a inbound rule to the instance security group.


![image](https://user-images.githubusercontent.com/26665659/229276708-4501bffd-2e52-48f6-b420-6c0dcd107004.png)


Appilcation load balancer:

1. Application Load Balancer manages Layer 7 
2. Load Balancing is done on 2 bases -
   i. load balacing is done to multiple HTTP applications across different machine. (target group)
   ii. Load balancing is done to multiple HTTP applications on the same machine. (container)
3. Supoorts redirect 
4. support for HTTP/S and Websocket

Routing can be done to different target groups based:
  1. path of the URL (eg.com/user & eg.com/ports)
  2. hostmname in URL (site.eg.com & othersite.eg.com)
  3. query, strings,headrers in URL

It is great for micro-services and container-based application.


Target Groups:

ALB can route to multiple target groups.
Health Checks are done at target group level.

1. IP addresses  - must be private IPs
2. Lambda funstions
3. ECS (Amazon ECS - Amazon ECS is a fully managed container orchestration service that helps you to more efficiently deploy, manage, and scale containerized applications. It deeply integrates with the AWS environment to provide an easy-to-use solution for running container workloads in the cloud and on premises with advanced security features using Amazon ECS Anywhere.)
4. EC2 instances




  








