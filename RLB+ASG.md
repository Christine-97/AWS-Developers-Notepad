
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
  
















