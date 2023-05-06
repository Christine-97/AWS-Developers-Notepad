S3

name must be unique and 
aws region is under a perticular region though the category will show it as global on the top right 

s3 buckets under all thge regions can be seen in one place
Bucket : Buckets are containers for data stored in S3. 

![image](https://user-images.githubusercontent.com/26665659/236632352-b3a45e28-0032-4f50-9b7f-6a4d2970c83d.png)

Block Public Access settings for this bucket: (default)
![image](https://user-images.githubusercontent.com/26665659/236632446-613f5277-260e-49fc-a935-b0a7dceb7001.png)

Bucket Versioning: (default)
![image](https://user-images.githubusercontent.com/26665659/236632469-6625fb0c-03da-47d9-bb14-a461d952d097.png)

Default encryption: 

Encryption key type : (Default) Amazon S3 managed keys (SSE-S3)
Bucket key : (When KMS encryption is used to encrypt new objects in this bucket, the bucket key reduces encryption costs by lowering calls to AWS KMS)
![image](https://user-images.githubusercontent.com/26665659/236632489-9110a4c9-b5d9-460d-a5d1-f3094363c4f5.png)


![image](https://user-images.githubusercontent.com/26665659/236632670-54fdadd0-7b99-4996-9b5b-bf3306d6af89.png)


Buckets:
![image](https://user-images.githubusercontent.com/26665659/236632729-6cef33b2-c1bf-41a4-8397-80e6911f512f.png)

Objects :
![image](https://user-images.githubusercontent.com/26665659/236632793-22792a2b-d8d6-4183-912a-0c35d14d2cab.png)


to upload an object: ![image](https://user-images.githubusercontent.com/26665659/236632829-3422c0c2-fbf3-4b62-94e5-96683afe02d3.png)

add files : ![image](https://user-images.githubusercontent.com/26665659/236632848-48712afe-3863-44dd-a5c3-f861d62a1362.png)

once uploaded:
![image](https://user-images.githubusercontent.com/26665659/236632902-ef68290f-56a2-45c7-9a5a-04bb917f954d.png)

click on upload : ![image](https://user-images.githubusercontent.com/26665659/236632922-0f328e71-3b5b-4491-8942-eb2916f3cc84.png)

![image](https://user-images.githubusercontent.com/26665659/236632962-a1e22ad9-c1dd-4a77-b4f4-0b516e98de4c.png)

click on open to view the image  ![image](https://user-images.githubusercontent.com/26665659/236633026-ee84671e-36df-4161-9736-f87d3070b5a2.png)

![image](https://user-images.githubusercontent.com/26665659/236633160-3f36aa12-6c7e-4bea-a0ca-4f12287315a0.png)

Object URL: ( however the object URL will lead us to an access denied page)
![image](https://user-images.githubusercontent.com/26665659/236633356-52a62419-5e81-4d96-9be6-e9adcbc822db.png)

![image](https://user-images.githubusercontent.com/26665659/236633544-d91449f9-0604-40c8-9e55-55da2acf4db0.png)

The differnce in the access is that the public URL has been blocked as per the default during setup, while the private URL (S3 pre-signed URL) if you notice has a security token that has been pre-signed with the user's credentials authorizing the user to view the image.


How to ccreate a folder ?

Navigate to your bucket and click on ![image](https://user-images.githubusercontent.com/26665659/236633941-d4cba8ed-b3d0-45d9-bfe6-1ed1ec294839.png)

![image](https://user-images.githubusercontent.com/26665659/236633984-7ec1c0e3-56b1-4155-81cb-802a99219630.png)

click on ![image](https://user-images.githubusercontent.com/26665659/236634006-3f6a84dd-75e2-44f5-aa23-a38bf696fb31.png)

![image](https://user-images.githubusercontent.com/26665659/236634043-37f647b3-da46-4c0b-980e-5ae06c4d5eef.png)

click on the folder to upload a image to it:

![image](https://user-images.githubusercontent.com/26665659/236634081-4df66026-4e93-4258-9990-0458f791dd4b.png)


How to delete foler/ object from S3 bucket ?

select object you want to delete and click on ![image](https://user-images.githubusercontent.com/26665659/236634309-608d7985-3c3b-464f-ab70-d409cdae5546.png)

![image](https://user-images.githubusercontent.com/26665659/236634290-576d8712-e8ad-4962-976e-5778dc65674c.png)

Confirm deletion:

![image](https://user-images.githubusercontent.com/26665659/236634263-bf2a054d-21ce-44ce-8834-5227c1b4ad1a.png)


![image](https://user-images.githubusercontent.com/26665659/236634406-40d23489-62d6-41b2-a6b8-f1f6d5a1a1c6.png)




Amazon S3 - Security

Security levels:

1.) User-Based
  a. IAM Policies - which API calls should be allowed for a specific user from IAM

2.) Resource-Based
  a. Bucket Policies - bucket wide rules from the S3 console - allows cross account
  b. Object Access Control List (ACL) - finer grain (can be disabled)
  c. Bucket Access Control List (ACL) - less common (can be disabled)

Note: an IAM principal can access an S3 object if 
  1. The user IAM permissions ALLOW it 
OR 
  2. The resource policy ALLOWS it 
AND 
  3. There's no explicit DENY

Encryption: Objects encryption in Amazon S3 is done using encryption keys


S3 Bucket Policies:

JSON based policies
 
1. Resources: buckets and objects
2. Effect: Allow / Deny
3. Actions: Set of API to Allow or Deny
4. Principal: The account or user to apply the policy to
 
  Use S3 bucket for policy to:
1. Grant public access to the bucket
2. Force objects to be encrypted at upload
3. Grant access to another account (Cross Account)



Block public access:
Bucket settings for Block Public Access

Block all public access (feature by AWS if you don't want the bucket to be public)
On
1. Block public access to buckets and objects granted through new access control lists (ACLs)
S3 will block public access permissions applied to newly added buckets or objects, and prevent the creation of new public access ACLs for existing buckets and objects. This setting doesn’t change any existing permissions that allow public access to S3 resources using ACLs.

2. Block public access to buckets and objects granted through any access control lists (ACLs)
S3 will ignore all ACLs that grant public access to buckets and objects.

3. Block public access to buckets and objects granted through new public bucket or access point policies
S3 will block new bucket and access point policies that grant public access to buckets and objects. This setting doesn't change any existing policies that allow public access to S3 resources.

4. Block public and cross-account access to buckets and objects through any public bucket or access point policies
S3 will ignore public and cross-account access for buckets or access points with policies that grant public access to buckets and objects.


• These settings were created to prevent company data leaks
• These can be set at the account level

Note: If you know your bucket should never be public, leave these on 



How to make a file public ?

Under your bucket, go to permissions tab:
![image](https://user-images.githubusercontent.com/26665659/236636241-3ae2b41e-b2a1-4a0b-8a06-173f3727e404.png)

Click on "Edit" to untick "Block all public access" 

![image](https://user-images.githubusercontent.com/26665659/236636382-95e711d9-6c66-4e3b-88ad-7fbda417224c.png)


![image](https://user-images.githubusercontent.com/26665659/236636365-241a015b-461e-4534-afa5-a8df10607419.png)

confirm : 
![image](https://user-images.githubusercontent.com/26665659/236636420-2ff0a47f-07ec-4d5b-b5ad-7ea22e2eccba.png)

Under Bucket policy, "Edit":
![image](https://user-images.githubusercontent.com/26665659/236636449-a2762675-da50-47c3-9f1c-195c1e352952.png)

![image](https://user-images.githubusercontent.com/26665659/236636479-93a8014e-3aec-4d00-89a2-5c9bf390ad53.png)


![image](https://user-images.githubusercontent.com/26665659/236636529-fbc526df-5b5b-43bc-b19d-186cb3ea3b76.png)

AWS Policy Generator:

Select Type of Policy
![image](https://user-images.githubusercontent.com/26665659/236636794-bd9f7b5c-873f-40e0-8a52-88d141da9533.png)

Actions
![image](https://user-images.githubusercontent.com/26665659/236636723-16084bc0-9bb2-4954-981b-f3a014785dbf.png)

Amazon Resource Name (ARN)
![image](https://user-images.githubusercontent.com/26665659/236636759-f80be78b-446d-45ec-b71d-7b2dbc2ed7ee.png)
dont forget to add : '"/*"' after the ARN, as the action is applied to the objects with the given bucket.

Lets add this statement :
![image](https://user-images.githubusercontent.com/26665659/236636847-89361031-51be-4e5f-8b90-fb019993c7b4.png)

and generate this policy:
![image](https://user-images.githubusercontent.com/26665659/236637348-6b00daa6-ed2a-48f6-9320-f62cbc766a3d.png)


we get a pop up to copy the policy generated:

![image](https://user-images.githubusercontent.com/26665659/236637387-802d9cd8-7458-4d2d-bc7b-21f73c792029.png)

Paste the policy:
![image](https://user-images.githubusercontent.com/26665659/236637399-cc223712-3f27-4c17-ba02-0cd3bfca61a4.png)

Save the changes:
![image](https://user-images.githubusercontent.com/26665659/236637433-a483ef47-ce99-45d6-b645-27251589b914.png)

The bucket access is now set to public : (with warning sign)
![image](https://user-images.githubusercontent.com/26665659/236637543-a3942cbc-3fdc-41c9-adc3-6017c7057eb1.png)

![image](https://user-images.githubusercontent.com/26665659/236637468-b4131e72-5ed6-49ef-aaac-bb246236de8b.png)


now all you files will be policy !

































Storage class
Amazon S3 offers a range of storage classes designed for different use cases.

![image](https://user-images.githubusercontent.com/26665659/236634150-724d0a8f-2015-4d9d-97ef-5547b6a57857.png)




