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

## Creating the Access Key for the terraform-en-1 user using the IAM service

- Access the **terraform-en-1** user

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/133a717b-f434-4d98-8f6c-3f2e2ac01aac)

- Click on the Security credentials tab

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/feba1499-7be2-47a9-a99c-2f3a04b4e26d)

- Navigate to the **Access keys** section
- Click on **Create access key**

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/250c863e-422d-4e00-b38a-db7d4cc99657)

- Select Command Line Interface (CLI) and I understand the above recommendation and want to proceed to create an access key.

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/5e963272-7e2b-41b0-9988-2dd4ca98914b)

- Click on **Next**.
- Click on **Create access key**
  
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/d9ef6e3f-060a-4583-81b7-d43e30c87352)

- Click on Download .csv file

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/23f88e38-bb83-4435-a1ad-68b7d0f75fcd)

- After the download finishes, click on Done.
- Once the download is complete, rename the **.csv** file to **key.csv**


