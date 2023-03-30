
EBS :

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



EFS :

Managed NFS (N/W file system) that can be mounted on many EC2 and to EC2 instances in different AZ
It is highly scable and expensive $$$ , pay per use.
It uses NFSv4.1 protocol and security group to contol EFS 
KMS encrypted and compatible with linus not windows



Navigate to EFS-> Create file system

you will get a small pop up -> click on "customize"

![image](https://user-images.githubusercontent.com/26665659/228904496-c9b89a06-0207-45fa-9c2a-3194b5dcce34.png)

Enter name 
![image](https://user-images.githubusercontent.com/26665659/228904265-adcfe08d-ec8b-4dbb-85cb-c27ef37dc75f.png)

Storage class:
1. Regional option will store the data redundancy across the AZ 
2. One zone option will store the data in a single AZ

![image](https://user-images.githubusercontent.com/26665659/228903636-7d1b2328-2603-4277-9d7e-c79d1efe5b5e.png)

You can enable / disable auto backup:
![image](https://user-images.githubusercontent.com/26665659/228904726-e6bb9850-fc50-4457-b3b3-ca44c517b81e.png)


You archive the files to save cost as part of the lifecycle settings:
![image](https://user-images.githubusercontent.com/26665659/228905017-ce12da71-82b2-43ae-a644-51e38fb856fd.png)


you customize your setting with KMS :

![image](https://user-images.githubusercontent.com/26665659/228905157-8c8131c6-cbdd-4632-b3dd-07bd54ba5f83.png)


You can customize the performance:
Performance mode:
General - for content management like wordpress sites
Max I/O - Scale to higher levels of operations per sec

Throughput mode:
Burst - Scales with increase in data 
Provisioned - throughput is fixed

![image](https://user-images.githubusercontent.com/26665659/228905453-d711f5ba-82af-4dd5-95b1-fa0a0681c412.png)

Network access:

you can add your security group or keep the default 
![image](https://user-images.githubusercontent.com/26665659/228907485-4a838e49-9e8f-4ed3-9c72-45cc9edd3c42.png)


File system policy - optional:
![image](https://user-images.githubusercontent.com/26665659/228908329-3281ca7f-e3ab-436a-84b1-2e75d720e0df.png)

Review and click on "create"!

How to add EFS to an EC2 instance ? 
While creating an EC2 instance,


Under Network setting u can edit, and add a subnet :
![image](https://user-images.githubusercontent.com/26665659/228910841-5bc447dc-c8cb-4586-a548-50a1e9314e81.png)


under storage volumes you can now add your EFS, save the file path:
![image](https://user-images.githubusercontent.com/26665659/228911205-e6f6b509-6138-4e83-aab5-665b3f2961b0.png)



to chekc if u are connected to the EFS:
use instance connect to connect to your instance

``` 
 ls <file path>
 echo "hello" > <file path>/hello.txt
 cat <file path>/hello.txt 
```

you will be in your file system.




