
<h2> Launching an EC 2 machine with Free tier options </h2>

EC2 - > instances  - > launch Intances 

![image](https://user-images.githubusercontent.com/26665659/228292503-b1a5c121-a710-4b5c-ac7a-b8def204cce3.png)


add name tag - < My First Instance >
select Basic image / AMI (amazon Machine Image (AMI) under Quick start - < Amazon Linux >

![image](https://user-images.githubusercontent.com/26665659/228292816-5d38bfa1-999a-4d32-8c24-f4d646fddfa3.png)

Architecture - 64 bit

Instance type - t2.micro

Key pair (login) (required for ssh connection)  - Create a Key pair

Save the downloaded file for future use:

![image](https://user-images.githubusercontent.com/26665659/228294540-da46ffe2-d7f2-4b74-8da9-cd75dcaaf285.png)

Network Setting:
continue with the default (tick the allow HTTPS/HTTP traffic from the internet if u want to allow any incoming traffic to your instance)

![image](https://user-images.githubusercontent.com/26665659/228296508-9f761350-8e92-4b07-be4b-1caf275bb73d.png)

Storage volumes:

continue with default free tier

![image](https://user-images.githubusercontent.com/26665659/228297615-fb916320-9db4-4291-b131-b088a522ab63.png)

if u want to save your volume (data ram ? ) on deletion of yourinstace please go to advance and change delete on termination to NO

![image](https://user-images.githubusercontent.com/26665659/228298281-78fb1ab4-bd39-4a9b-aed6-2a00c063dfc7.png)


Advance Details:
Continue with default, If you want to run a code during your first boot up of your EC 2 instance :
add it to  ->   User data - optional  

![image](https://user-images.githubusercontent.com/26665659/228301205-4814f8b1-a599-4446-b6a1-0725b50aec45.png)

Summary:
Review your configuration settings under "Summary"

![image](https://user-images.githubusercontent.com/26665659/228301950-bbdad76d-5673-4afd-bf7f-0dad809ee847.png)


Now u can click on launch instance to launch your instance.
![image](https://user-images.githubusercontent.com/26665659/228301764-07670547-8c1e-4a60-bfe5-c9cb8ef84366.png)



To check if your server is up and running -

you can go to the 
EC2 dashboard  -> click on the instance you created and click on the "open address" under public IPv4 address:

![image](https://user-images.githubusercontent.com/26665659/228328829-0c1011ee-91fa-4749-9ba9-18ce43bdcc0c.png)

Please Note:

To start or stop your instance :

Select your instance and click on instance state to change status of your instance, to save billing cost.

![image](https://user-images.githubusercontent.com/26665659/228330928-e3f23762-57fc-42d8-a5f0-ef075843c43e.png)



Public IP will change everytime you stop and start your instance but your private IP will always be same.


__________________________________________________________________________________________________________



Types of EC2



![image](https://user-images.githubusercontent.com/26665659/228335352-4e2e66f0-63c2-474d-a936-18ba397dc3fa.png)



Naming Convention family ;

m5.8xlarge

m = instance
5 =  generation
8xlarge =  size of the instance.


Security Group:

Acts as a firewall
fundatmentals of n/w security 
controlls traffic into (inbound) or out (outbound) our EC2 instances
it contains only allow rules 
can reference by IP or by other security groups
They regulate access to ports 
They also regulate authorised IP ranges - IPv4 and  Ipv6
can be attached to multiple instances and multiple groups can be aatached to the a single instance
they can be created under a single region / VPC combo
good practice to maintain a group only for ssh access

(incase of time-out issue, please check your security group)

![image](https://user-images.githubusercontent.com/26665659/228353810-c5f2f644-f86e-4098-a2e0-38d0239d183c.png)


Basic Ports you need to know:


![image](https://user-images.githubusercontent.com/26665659/228355627-05d80e21-c183-4127-a4b8-8374ef7d21cf.png)



IAM instance role

IAM roles you delegate access to users or AWS services to operate within your AWS account. 
Users from your identity provider or AWS services can assume a role to obtain temporary security credentials that can be used to make an AWS request in the account of the IAM role.




