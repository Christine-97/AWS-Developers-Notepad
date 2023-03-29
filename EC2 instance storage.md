

what is an EBS volume?  (Amazon Elastic Block Store)

Amazon Elastic Block Store provides raw block-level storage that can be attached to Amazon EC2 instances and is used by Amazon Relational Database Service. It is one of the two block-storage options offered by AWS, with the other being the EC2 Instance Store.

EBS are bound by a given AZ, but can be moved to a new AZ by creating a snapshot and using the same snapshot to create a new volume in a new AZ using the snapshot





<h1><u>EBS :</u></h1>

EBS volume or elastic block volume is a network drive / network usb i.e a storge block connected through the network.

As it is not part of the phyiscla machine and is connected our the network it can be deattached and attached to different EC 2 instances under the same AZ

EBS volumes are bound by AZ, but can be moved around using snapshots.

You can attach multiple EBS volumes to a single instance. The volume and instance must be in the same Availability Zone.

but AWS EBS be attached to multiple EC2?
Amazon EBS Multi-Attach enables you to attach a single Provisioned IOPS SSD ( io1 or io2 ) volume to multiple instances that are in the same Availability Zone. 
Use EBS Multi-Attach volumes to enable multiple EC2 instances to simultaneously access a standard file system.
You can attach multiple Multi-Attach enabled volumes to an instance or set of instances.

When an EBS is created with an EC2 instance, u can check in advance for a delete on termination option. if yes on termination of EC2, the EBS is deleted, else the 
EBS storage can be saved to be attached to future EC2 instance.


creating a snapshot : 



You can make a copy of an EBS volumn at any given point 

It is not necessary but a recommended step

it helps create a copy of the existing EBS volumn and move it to a new AZ by restoring it to a new AZ. (transfer a EBS from one AZ to another)




Steps to create snapshot:

EC2->Volumns->Select the volumn you want to snapshot->actions-> create snapshot

![image](https://user-images.githubusercontent.com/26665659/228523257-8dd10420-45bd-4fcf-9632-65545a62fae2.png)

Add tags (optional) , helps keep track :
![image](https://user-images.githubusercontent.com/26665659/228523618-49b44601-bd51-4737-90ff-286fdd728164.png)

LHS menu  go to Snapshots:

![image](https://user-images.githubusercontent.com/26665659/228524218-c9575f6b-d273-4c30-82c3-e8dd87d7609b.png)

You copy the snapshot you created to a new AZ:

![image](https://user-images.githubusercontent.com/26665659/228524495-4d7303a6-dbb6-44ea-abc6-4c6b7d5dbaee.png)

you can create volumn in a new AZ from the copied snapshot:
![image](https://user-images.githubusercontent.com/26665659/228524587-88737958-be1b-40d1-8c66-fff5f94f4ae6.png)

![image](https://user-images.githubusercontent.com/26665659/228524974-e2966e0c-eeff-49ed-9224-7f0e84fd6eec.png)





EBS snapsot feature 

Archive : 
helps move the following to archives which is 75% cheaper 
takes 24 to 72 hrs to restore 

![image](https://user-images.githubusercontent.com/26665659/228542191-6fbb2777-7272-4dc8-bc02-585aa705bca5.png)
 
 *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*

Recycle bin : ![image](https://user-images.githubusercontent.com/26665659/228525221-7ce58043-8311-4d06-abc6-9e9b02215205.png)
helps retain deleted files for recovery for a time period of 1 month to 1 yr.
protection against accidental deletion

YOu can navigate to recycle bin from snapshots:
![image](https://user-images.githubusercontent.com/26665659/228525996-0c3bd616-94b7-4a7e-82fb-4da0b000f6cb.png)

Use can create a retention rule:
![image](https://user-images.githubusercontent.com/26665659/228525442-ec316868-0746-43f8-8f38-12a2e4e20ddb.png)
![image](https://user-images.githubusercontent.com/26665659/228525615-cae036c7-6ff5-4792-ba24-fb13d3993662.png)


You can delete / archive the snapshot: 
![image](https://user-images.githubusercontent.com/26665659/228541574-c3a8a87c-f5f7-404d-b779-d5b07fa65add.png)


under resources you can find your deleted snapshot :
![image](https://user-images.githubusercontent.com/26665659/228543182-c00cdf78-9bc2-44b9-b0d2-d11a07f9acf0.png)

Restore:
![image](https://user-images.githubusercontent.com/26665659/228543526-efc3fc63-11db-4c57-b960-7cc8ce33d355.png)

and it is back into the snaphots in the EC2 console.

<p> *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*</p>
 
Fast Snapshot restore: (FSR)
Helps restore large snaphot with no latency on first use, $$$ 


 *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*

<h5><b>AMI Overview:</b></h5>

Amazon Machine Image is a customization of the EC2 instance.

Advantages us to have a faster boot time

all software will be pre packaged / Pre defined 

Type of AMI:
Public AMI - AWS provided
Own AMI - make and maintain yourself 
AWS Marketplace  AMI : AMI made and sold over the market place

<u>AMI process:</u>

Create AMI -- >  Custome AMI -- >  Launch from AMI 

Start the EC2 instance to customize it
Stop instance for data integrity
Create AMI with EBS snapshots
Launch instances in same / other AZ
Faster Boot time


Create an Image :

![image](https://user-images.githubusercontent.com/26665659/228558460-929ab525-313d-47b0-bed1-4fc2d8f6f791.png)

continue with default :
![image](https://user-images.githubusercontent.com/26665659/228558721-8315cb6b-2b1c-4916-b87e-e627211fa456.png)
![image](https://user-images.githubusercontent.com/26665659/228559451-45f0c823-c432-4f63-bd43-b368522ff900.png)

LHS -> AMI 

To launch an instance from the AMI:
![image](https://user-images.githubusercontent.com/26665659/228560036-befee16b-8e22-4276-a3dd-70863c07c946.png)

Launch Instance from EC2 dashboard - you can find your image under "My AMI": 
![image](https://user-images.githubusercontent.com/26665659/228560618-ed9dee97-ddd6-4084-9287-6e820373ff75.png)

To delete the AMI, simply select the AMI you want to delete, click on "Deregister AMI"
![image](https://user-images.githubusercontent.com/26665659/228567280-3622ba7d-3e01-484a-923a-1642269cb19e.png)










Reference :

https://n2ws.com/blog/how-to-guides/how-to-delete-unutilized-ebs-based-amis-and-corresponding-snapshots
<h1><u>EBS :</u></h1>

EBS volume or elastic block volume is a network drive / network usb i.e a storge block connected through the network.

As it is not part of the phyiscla machine and is connected our the network it can be deattached and attached to different EC 2 instances under the same AZ

EBS volumes are bound by AZ, but can be moved around using snapshots.

You can attach multiple EBS volumes to a single instance. The volume and instance must be in the same Availability Zone.

but AWS EBS be attached to multiple EC2?
Amazon EBS Multi-Attach enables you to attach a single Provisioned IOPS SSD ( io1 or io2 ) volume to multiple instances that are in the same Availability Zone. 
Use EBS Multi-Attach volumes to enable multiple EC2 instances to simultaneously access a standard file system.
You can attach multiple Multi-Attach enabled volumes to an instance or set of instances.

When an EBS is created with an EC2 instance, u can check in advance for a delete on termination option. if yes on termination of EC2, the EBS is deleted, else the 
EBS storage can be saved to be attached to future EC2 instance.


creating a snapshot : 



You can make a copy of an EBS volumn at any given point 

It is not necessary but a recommended step

it helps create a copy of the existing EBS volumn and move it to a new AZ by restoring it to a new AZ. (transfer a EBS from one AZ to another)




Steps to create snapshot:

EC2->Volumns->Select the volumn you want to snapshot->actions-> create snapshot

![image](https://user-images.githubusercontent.com/26665659/228523257-8dd10420-45bd-4fcf-9632-65545a62fae2.png)

Add tags (optional) , helps keep track :
![image](https://user-images.githubusercontent.com/26665659/228523618-49b44601-bd51-4737-90ff-286fdd728164.png)

LHS menu  go to Snapshots:

![image](https://user-images.githubusercontent.com/26665659/228524218-c9575f6b-d273-4c30-82c3-e8dd87d7609b.png)

You copy the snapshot you created to a new AZ:

![image](https://user-images.githubusercontent.com/26665659/228524495-4d7303a6-dbb6-44ea-abc6-4c6b7d5dbaee.png)

you can create volumn in a new AZ from the copied snapshot:
![image](https://user-images.githubusercontent.com/26665659/228524587-88737958-be1b-40d1-8c66-fff5f94f4ae6.png)

![image](https://user-images.githubusercontent.com/26665659/228524974-e2966e0c-eeff-49ed-9224-7f0e84fd6eec.png)





EBS snapsot feature 

Archive : 
helps move the following to archives which is 75% cheaper 
takes 24 to 72 hrs to restore 

![image](https://user-images.githubusercontent.com/26665659/228542191-6fbb2777-7272-4dc8-bc02-585aa705bca5.png)
 
 *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*

Recycle bin : ![image](https://user-images.githubusercontent.com/26665659/228525221-7ce58043-8311-4d06-abc6-9e9b02215205.png)
helps retain deleted files for recovery for a time period of 1 month to 1 yr.
protection against accidental deletion

YOu can navigate to recycle bin from snapshots:
![image](https://user-images.githubusercontent.com/26665659/228525996-0c3bd616-94b7-4a7e-82fb-4da0b000f6cb.png)

Use can create a retention rule:
![image](https://user-images.githubusercontent.com/26665659/228525442-ec316868-0746-43f8-8f38-12a2e4e20ddb.png)
![image](https://user-images.githubusercontent.com/26665659/228525615-cae036c7-6ff5-4792-ba24-fb13d3993662.png)


You can delete / archive the snapshot: 
![image](https://user-images.githubusercontent.com/26665659/228541574-c3a8a87c-f5f7-404d-b779-d5b07fa65add.png)


under resources you can find your deleted snapshot :
![image](https://user-images.githubusercontent.com/26665659/228543182-c00cdf78-9bc2-44b9-b0d2-d11a07f9acf0.png)

Restore:
![image](https://user-images.githubusercontent.com/26665659/228543526-efc3fc63-11db-4c57-b960-7cc8ce33d355.png)

and it is back into the snaphots in the EC2 console.

<p> *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*</p>
 
Fast Snapshot restore: (FSR)
Helps restore large snaphot with no latency on first use, $$$ 


 *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*- *-*-*-*

<h5><b>AMI Overview:</b></h5>

Amazon Machine Image is a customization of the EC2 instance.

Advantages us to have a faster boot time

all software will be pre packaged / Pre defined 

Type of AMI:
Public AMI - AWS provided
Own AMI - make and maintain yourself 
AWS Marketplace  AMI : AMI made and sold over the market place

<u>AMI process:</u>

Create AMI -- >  Custome AMI -- >  Launch from AMI 

Start the EC2 instance to customize it
Stop instance for data integrity
Create AMI with EBS snapshots
Launch instances in same / other AZ
Faster Boot time


Create an Image :

![image](https://user-images.githubusercontent.com/26665659/228558460-929ab525-313d-47b0-bed1-4fc2d8f6f791.png)

continue with default :
![image](https://user-images.githubusercontent.com/26665659/228558721-8315cb6b-2b1c-4916-b87e-e627211fa456.png)
![image](https://user-images.githubusercontent.com/26665659/228559451-45f0c823-c432-4f63-bd43-b368522ff900.png)

LHS -> AMI 

To launch an instance from the AMI:
![image](https://user-images.githubusercontent.com/26665659/228560036-befee16b-8e22-4276-a3dd-70863c07c946.png)

Launch Instance from EC2 dashboard - you can find your image under "My AMI": 
![image](https://user-images.githubusercontent.com/26665659/228560618-ed9dee97-ddd6-4084-9287-6e820373ff75.png)

To delete the AMI, simply select the AMI you want to delete, click on "Deregister AMI"
![image](https://user-images.githubusercontent.com/26665659/228567280-3622ba7d-3e01-484a-923a-1642269cb19e.png)










Reference :

https://n2ws.com/blog/how-to-guides/how-to-delete-unutilized-ebs-based-amis-and-corresponding-snapshots
