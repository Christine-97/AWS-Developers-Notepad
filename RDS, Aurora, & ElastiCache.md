
Amazon RDS 

1. RDS stands Relational Database Service.
2. It is managed DB service
3. Allows you to create DB in cloud  ( Postgres, MySQL, Oracle, etc.)
4. Disadvantage - you can't SSH into your isntances as it is the service provided by AWS.
5. Advantage - 
    a. Auto provisioning, OS patching 
    b. continuous backup and restore to a spcific timestamp (Point in time restore)
    c. Monitoring dashboards
    d. Read replicas
    e. Multi AZ setup for Disaster Recovery
    f. Maintenance windows
    g. Scaling capability both horizontally and vertically
    h. storage by gp2 or io1 EBS 



RDS  - Storage Auto Scaling 

1. helps your dynamically increase your storatge 
2. detects when the Free DB storage is running out 
3. no need to manually scale the DB
4. You can st a Maximum Storage Thresholf 
5. you can auto modify based on condoitions set 
6. Useful for applications with unpredictable workloads
7. supports all RDS database engines



RDS Read Replicas for read scalability
  1. You can create up to 15 Read replicas
  2. Read Replicas can be created within AZ, Cross AZ or Cross Region
  3. replication is asynchronuos
  4. Replicas can be made DB 
  5. the application must be connected to leverage read replicas


Can be used for read/ Select statements for a separate application for a separate task.


Multi AZ network cost is free , Multi Region is not free


Multi AZ - Disaster Recovery: 

1. It is a SYNC replication between the Master DB and replica.
2. one DNS name is used, it is passed on to the replica incase of failover.
3. Increased availability 
4. No intervention required 
5. Not used for scale just a stand by


Note: Read Replicas can be setup as Multi AZ for Disaster Recovery. 


Single - AZ to Multi - AZ

1. Zero downtime operation 
2. A snapshot is taken and restored in a new AZ 
3. Synchronized replication is established between the stand by and the RDS DB instance.
