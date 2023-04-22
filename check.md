<!DOCTYPE html>
<html>

<body>
	<h1>🌐 Route 53</h1>
	<p>53 is the traditional DNS port. 🌎</p>
	<p>Highly available, scalable, fully managed and authoritative DNS (i.e. the customer can update the DNS records). 🚀</p>
	<p>Route 53 is a domain registrar. 🏭</p>
	<p>Can check health of resources. 🏥</p>
	<p>AWS provides 100% availability SLA. 💯 
		(The availability SLA is a contract between a service provider and their end-user that defines the expected level of application/database uptime and accessibility a vendor is to ensure and outlines the penalties involved (usually financial) if the agreed-upon service levels are not met.)</p>
	<p>Can help route traffic for a domain by reacting records. 🚥</p>
	<p>Each record contains:</p>
	<ul>
	  <li>Domain / subdomain name - example.com</li>
	  <li>Record type- A / AAAA / CNAME / NS</li>
	  <li>Value - xx.xx.xx.xx</li>
	  <li>Routing policy - how to route / response to queries</li>
	  <li>TTL - time to live (amt of time the record is cached at the DNS resolvers). ⏰</li>
	</ul>
	<p>Record types:</p>
	<ul>
	  <li>A - maps a host name to IPv4</li>
	  <li>AAAA - maps a host name to IPv6</li>
	  <li>CNAME - maps a host name to another host name</li>
	  <li>NS - name servers for the hosted zone (control how traffic is routed for a domain)</li>
	</ul>
	<p>Hosted Zones:</p>
	<ul>
	  <li>A directory of records and how to navigate traffic to a domain and its subdomain.</li>
	  <li>Public hosted zone - contains records to route public domain names. 🌐</li>
	  <li>Private hosted zone - contains records to route private domain names (within one or more VPC). 🔒</li>
	</ul>
	
<h3>📝 Registering a Domain:</h3>
	
<p><b>🔍 Navigate to the Route 53 </b></p>
<p><b>	-> under Domains , click on registered domains </b></p>
<p><b>	-> click on Register Domains</b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798301-a7df37b6-ddad-4db3-ae83-a81c238c4c4e.png">

<p><b>🔍 Choose a domain name : </b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798246-f6f699a8-839a-43a2-9249-b256f5d006ef.png">

<p><b>👥 Update contact details, remember to enable the privacy protection (Hides contact details to avoid unsolicited communication) :</b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798440-c98e9cad-8cc1-4b4a-9083-9cb152529536.png">

<p><b>🔧 Enable / disable auto domain name renewal, accept terms and conditions :</b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798509-9a435ff1-e41f-416a-9bfa-cbe4aa9d99b7.png">

<p><b>👉 Click on <img src="https://user-images.githubusercontent.com/26665659/233798880-a39ea5d8-1dd7-44ee-b717-1cae13fc5d4f.png"></b></p>

<p><b>🔍 Once your domain name was registered, under Left-hand side menu, go to :  </b></p>
<p><b>🏠 Hosted zone </b></p>
<p><b>	 -> Check for Hosted zone Details</b></p>

<p><b>📝 Your domain name should have 2 records  </b></p>
<p><b>	-> NS - Server details that can provide value of the records added to the table, SOA</b></p>

<p><b>🔍 Under hosted zones </b></p>
<p><b>	-> domain names </b></p>
<p><b>	-> click on create record : </b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798571-896bd91f-2cfb-4878-9be6-6326f5c7227b.png">

<p><b>📝 Fill the Record details and click on create records -></b></p>
<img src="https://user-images.githubusercontent.com/26665659/233798698-76495c99-f001-4f41-add9-7f425a792766.png">

<p><b>🔍 CloudTrail commands to inquiry record details- </b></p>

```
sudo yum install -y bind-utils  // to install both nslookup and dig commmand
nslookup  <recordname> // to get server and sddress details as well as non authoritative answers like name and address the url is redirected too
dig <recordname> // provides additional details like TTL and Type of record
```

	
<div>
    <p>🤔 What is a record TTL?</p>
    <p>🔍 Once the client makes a DNS request for a given hostname, the client will have to query the DNS system for a given TTL (<span>⏰</span> TIME TO LIVE - i.e. duration), as the answer has been cached for accessing the same hostname.</p>
    <p>👉 High TTL</p>
    <ul>
        <li>1 Less traffic on Route 53</li>
        <li>2 Possibly outdated records</li>
    </ul>
    <p>👉 Low TTL</p>
    <ul>
        <li>1 More traffic on Route 53, increase in cost ($$)</li>
        <li>2 Records are outdated for a short time</li>
        <li>3 Easy to change the record name as it is cached for a short time in the client system.</li>
    </ul>
    <p>🔐 TTL is mandated for each DNS record, except Alias records.</p>
    <p>🚀 AWS Resources exposes AWS hostnames via load balancers, CloudFront etc</p>
    <p>🔗 CNAME</p>
    <p>CNAME allows you to point one hostname to another hostname ( only for non-root domains )</p>
    <p>🎯 ALIAS</p>
    <p>ALIAS allows you to point one hostname to AWS resources ( Both root domain and non-root domain ) 🆓 Free of charge 🏥 Can do a health check on resources</p>
    <p>🌐 It can be used for (Zone apex) the top node of the DNS namespace</p>
    <p>📝 Record name type A/AAAA is used for AWS resources (IPv4/IPv6)</p>
    <p>👨‍💼 Route 53 will set TTL.</p>
    <p>👎 EC2 DNS names cannot be targeted for ALIAS records</p>
    <p>🚦 Routing Policy</p>
</div>
	
	
	
</body>
</html>
