
<p><em>53 is the traditional DNS port.</em></p>

<p>Highly available, scalable, fully managed and authoritative DNS (i.e. the customer can update the DNS records).</p>

<p>Route 53 is a domain registrar.</p>

<p>Can check health of resources.</p>

<p>AWS provides 100% availability SLA. (The availability SLA is a contract between a service provider and their end-user that defines the expected level of application/database uptime and accessibility a vendor is to ensure and outlines the penalties involved (usually financial) if the agreed-upon service levels are not met.)</p>

<p>Can help route traffic for a domain by reacting records.</p>

<p>Each record contains:</p>

<ul>
	<li>Domain / subdomain name - example.com</li>
	<li>Record type- A / AAAA / CNAME / NS</li>
	<li>Value - xx.xx.xx.xx</li>
	<li>Routing policy - how to route / response to queries</li>
	<li>TTL - time to live (amt of time the record is cached at the DNS resolvers).</li>
</ul>

<p>Record types:</p>

<ul>
	<li>A - maps a host name to IPv4</li>
	<li>AAAA - maps a host name to IPv6</li>
	<li>CNAME - maps a host name to another host name.</li>
	<li>NS - name servers for the hosted zone (control how traffic is routed for a domain)</li>
</ul>

<h2>Hosted Zones</h2>

<p>A directory of records and how to navigate traffic to a domain and its subdomain.</p>

<p>Public hosted zone - contains records to route public domain names</p>

<p>Private hosted zone - contains records to route private domain names (within one or more VPC)</p>

<h2>Registering a Domain:</h2>

<p>Navigate to the Route 53 -> under Domains, click on registered domains -> click on Register Domains image</p>

<p>choose a domain name - &gt; image</p>

<p>Update contact details, remember to enable the privacy protection (to hide contact details from unsolicited communication)</p>

<p>image</p>

<p>Enable / disable auto domain name renewal, accept terms and conditions image</p>

<p>Click on image</p>

<p>Once your domain name was registered, under Left hand side menu, go to -</p>

<p>Hosted zone - &gt; Check for Hosted zone Details</p>

<p>your domain name should have 2 records -> NS - Server details that can provide value of the records added to the table, SOA</p>

<p>Under hostedzones -&gt; domain names -&gt; click on create record -&gt;</p>

<p>image</p>

<p>Fill the Record details and click on create records -&gt;</p>

<p>image</p>

<p>CloudTrail commands to inquire record details-</p>

<p>sudo yum install -y bind-utils // to install both nslookup and dig command</p>

<p>nslookup &lt;recordname&gt; // to get server and address details as well as non
