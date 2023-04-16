



Registering a Domain:

Navigate to the Route 53 -> under Domains , click on registered domains -> click on Register Domains
![image](https://user-images.githubusercontent.com/26665659/232305446-23f14bd2-a562-4fe4-b597-abeb9751c138.png)

choose a domain name - >

![image](https://user-images.githubusercontent.com/26665659/232305468-767f6d27-e23a-457b-b575-7aa6d138dbed.png)

Update contact details, remember to enable the privacy protetion (to hide contact details) 

![image](https://user-images.githubusercontent.com/26665659/232309382-71e7c3b9-48ba-4e82-82e3-6c5f48ceb200.png)


Enable / disable auto domain name renewal, accept terms and conditions

click on complete order ![image](https://user-images.githubusercontent.com/26665659/232309346-f82b5b32-d44c-4e1e-b7c6-74e0cb45fe6f.png)

Once your domain name was registered, under Left hand side menu, go to - 

Hosted zone - > Check for Hosted zone Details 

your domain name should have 2 records -> NS - Server details that can provide value of the records added to the table, SOA


Under hostedzones -> domain names -> click on create record ->

![image](https://user-images.githubusercontent.com/26665659/232309452-05775b2f-aa5c-4f60-8a1a-603d26c6886a.png)

Fill the Record details and click on create records ->

![image](https://user-images.githubusercontent.com/26665659/232309442-b2510295-1696-4cfb-819f-a76d575af67f.png)


CloudTrail commands to inqury record details- 

```
sudo yum install -y bind-utils  // to install both nslookup and dig commmand
nslookup  <recordname> // to get server and sddress details as well as non authoritative answers like name and address the url is redirected too


dig <recordname> // provides additional details like TTL and Type of record

```


What is record TTL ?

Once the client makes a DNS request for a given hostname, the client will not have to issue a query to DNS system for a given TTL (TIME TO LIVE - i.e. duration), as the answer has been cached for the accessing the same host name.


High TTL 
1. Less traffic on Route 53
2. Possibly outdated records

Low TTL 
1. More traffic on Route 53, increase in cost($$)
2. Records are outdated for lesser time 
3. Easy to change record name as it is cached for less time in the client system

TTL is mandate for each DNS record, except Alias records.

AWS Resources exposes an AWS hostname via load balancers, CloudFront etc

CNAME 

CNAME allows you to point one hostname to another hostname ( only for non root domain )

ALIAS

ALIAS allows you to point one hostname to aws resources ( Both root domain and non root domain )
Free of charge
Can do health check on resources

It can be used for (Zone apex) the top node of DNS namespace 

Record name type A/AAAA is used for AWS resources (IPv4/IPv6)

TTL will be set by Route 53.

EC2 DNS name cannot be a target to a ALIAS record


Routing Policy

I. SIMPLE 
  
  Route to single resource.
  Multiple values can be specified in the same record.
  No health checks.
  Alais can be enabled only for 1 AWS resource. 

II. WEIGHTED 

  % of the request is routed to a specific resource.
  Relative weight is assigned to each record:
          traffic (%) =    weight for a specific record 
                        ___________________________________
                         Sum of all weights for all records
  Weight dont need to sum up to 100.                      
  can have health checks. 
  DNS records must have same name and record type. 
  Use case: can be used to test new version by sending small traffic to a given resource. 
  If weight is 0 then no traffic is sent to the given record. 
  If all weights are 0, then the traffic will be equally distributed.
  
  
III. LATENCY
  
  Can do health checks (has a failover capability)
  Latency is based on user and AWS regions
  redirects to the resources closest to user
  Use case: When latency for user is priority
  mention region in the record details

IV. FAILOVER 
  There are 2 EC 2 isntances primary and secondary 
  The Route 53 policy helps move traffic to the secondary instance when the primary one is deeemed           unhealthy.
  There only can be one Primary and one Secondary 

V. GEOLOCATION
  It is different from Latency based
  Routing is based on geo-location 
  Can redirect user base on content and or country (if overlapping most precise location is selected)
  A default location can be set for underfined traffic.
  Health checks can be done 
  Use case:  Restricted content distribution, website localization 

VI. MULTI-VALUE
  Route traffic to multiple resources.
  Route 53 return multiple values/ resources.
  Health checks are used return only healthy resources as value.
  You can return up to 8 health check records for each multi-value query
  It is not a substitute for ELB ( client side load balancing ) 
  
VII. GEOPROXIMITY ( Using Route 53 traffic flow feature)
  Allows you ti route traffic to your resources based on location of the user and the resources
  There is a number called Bias, used to shift the traffic to resources based on specific location  
  To change the size of geographic region you can specify the bias values:
    To expand (1 to 99) - more traffic to resource
    To shrink (-1 to - 99) - less traffic to resource
  Resources can be own resources (on premises) hence the latitude and longitude has to be specified 
  For AWS Resources AWS regions has to be specified  
  Use case : To shift traffic from one region to another.

VIII. IP-based 
  Routing is based on clients' IP addresses
  User-IP-to-endpoint mappings - list of CIDRs for your clients and the corresponding endpoints/locations   are mapped.
  Use cases: Optimized performance, reduced network costs
  
<h2> Features  </h2>

Traffic flow:

It is used to simplify the process of creating and maintaining records in large and complex configurations 
This is a visual editor to manage complex routing decision 
These configurations can be saved as Traffic Flow Policy 
this can be applied to different hosted zones  ( different domain names )
and it supports versioning

Health Checks:

Health checks are integrated with Cloud watch metrics - 

I. Endpoint:
   a.  15 global health checkers check the endpoint.
   b. Healthy/Unhealthy threshold can be set.
   c. Interval of 30 sec or 10 sec ($$$) can be set for Health checks to be done.
   d. HTTP, HTTPS, TCP are supported.
   e. > 18% health checker must report the end port to be healthy
   f. You can also choose which locations you want the Route 53 to use
   g. Health Checks pass only if it responds to 2xx and 3xx status code.
   h. Health Checkers IP range must be configured to allow incoming requests.
   
II. Calculated Health Checks (Health checks to check other health checks):
   a. Combine the results of multiple child health checks by parent health checks.
   b. combination of AND OR or NOT can be used.
   c. 256 child health checks can be monitored, and threshold to pass can be defined for the parent to           pass.
   d. Use case: to carry out maintenance on website without causing all the health checks to fail

III. CloudWatch metric with assigned CloudWatch Alarms:
  a. Used to manitor Private resources (as private endpoints cant be accessed)
  b. Create a Cloud watch metric and create a cloud watch alarms that is assigned into the Health checker



    













