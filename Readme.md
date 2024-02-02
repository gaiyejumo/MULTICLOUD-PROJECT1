# Steps in Amazon Web Services (AWS)

## Creating the terraform-en-1 user using the IAM service

- Access the AWS console ([https://aws.amazon.com](https://aws.amazon.com/)) **and log in with your newly created account**. In the search bar, type IAM. In the Services section, click on IAM.
- Click on Users and then Add users, enter the name **terraform-en-1** and click Next to create a programmatic type user.

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/1b5f0a8b-4f67-4e48-9e68-0ac98a6b3a37)

- After advancing, in Set permissions, click on the Attach existing policies directly button.

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/6bf9a15f-3e6f-453a-8dc4-0678ca758c9b)

- Type **AmazonS3FullAccess** in **Search.**
- Select **AmazonS3FullAccess**

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/5094cc15-d191-4853-9bc6-7b91499ee77e)

- Click on **Next**
- Review all the details
- Click on **Create user**
