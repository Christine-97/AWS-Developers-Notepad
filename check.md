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
