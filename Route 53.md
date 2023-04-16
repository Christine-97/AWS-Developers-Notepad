



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








