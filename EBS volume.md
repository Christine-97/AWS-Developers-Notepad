
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





