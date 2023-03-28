How to connect to AWS CLI ?

1. Navigate to IAM
2. Go to tab -> user
3. Go to tab -> Security credentials
4. Click on "Create access Key"  
     ![image](https://user-images.githubusercontent.com/26665659/228025519-9705ac97-5bfa-4b14-bad6-c3f5242ba477.png)
5. Generate for CLI 
  ![image](https://user-images.githubusercontent.com/26665659/228025805-4658d72d-d89f-4b51-9df0-46bb6b5425d8.png)
6. Add Tag Value and click on create access key
7. This is the only time you view this Access key (username) and Secret access key(password), so download the csv file for safe keeps. 
  ![image](https://user-images.githubusercontent.com/26665659/228027595-975234df-34ae-4cd2-8779-6861a0af53d9.png)
8. Open your cmd and type "aws configure"
9. the terminal will provide certain input details to be filled up 
10. $ aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: json
11. you can check the list of users on your AWS account with the following command : "aws iam list-users"
12. ![image](https://user-images.githubusercontent.com/26665659/228029607-7690137c-48b4-4785-b5cd-618534249c0b.png)
13. tjfgfyghkfy
14. hftjgfytjh





Reference :


1. https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html
2. 
