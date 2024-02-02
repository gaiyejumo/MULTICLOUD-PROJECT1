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

# Steps in Google Cloud Platform (GCP)

## Preparing the environment to run Terraform

- Access the Google Cloud Console ([console.cloud.google.com](http://console.cloud.google.com/)) **and log in with your newly created account**
- Open the Cloud Shell

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/670f60f6-a22d-4234-92cb-fb70c3f0c74e)
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/52e3cd1e-fea1-4b9a-9f7c-ba1a5f95b0f7)

- Download the mission1.zip file in the Google Cloud shell using the wget command. Copy and paste:

```
wget https://tcb-public-events.s3.amazonaws.com/icp/mission1.zip

```

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/77f2f80c-f8c6-4013-89ab-95d8162b3862)

- Upload the key.csv file to the Cloud Shell using the browser
Step 1
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/9a133300-145e-4371-857c-93905cbd86de)
Step 2
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/0eb64af8-cdfc-4e80-b4fe-76953fd77a52)
Step 3
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/404ff8c9-f6a7-47a6-b8fd-75bc8b12ab84)
- Verify if the mission1.zip and key.csv files are in the folder in the Cloud Shell using the command below

ls

Result

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/71d0f145-529d-4b41-a2a1-a30e1a5777cc)

- Execute the file preparation commands:
```
unzip mission1.zip

```

```
mv key.csv mission1/en

```

```
cd mission1/en

```

```
chmod +x *.sh
```

Result
![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/257185bb-3aeb-4276-adc8-25a2dffa92da)

- Execute the commands below to prepare the AWS and GCP environment

```
mkdir -p ~/.aws/

```

```
touch ~/.aws/credentials_multiclouddeploy

```

```
./aws_set_credentials.sh key.csv

```

```
GOOGLE_CLOUD_PROJECT_ID=$(gcloud config get-value project)

```

```
gcloud config set project $GOOGLE_CLOUD_PROJECT_ID

```

- Click on Authorize

![image](https://github.com/gaiyejumo/MULTICLOUD-PROJECT1/assets/41402706/4d4a27d4-cf63-4890-b346-2dc7a4279976)

- Execute the command below to set the project in the Google Cloud Shell
```
./gcp_set_project.sh

```

- Execute the commands to enable the Kubernetes, Container Registry, and Cloud SQL APIs

```
gcloud services enable containerregistry.googleapis.com

```

```
gcloud services enable container.googleapis.com

```

```
gcloud services enable sqladmin.googleapis.com

```

```
gcloud services enable cloudresourcemanager.googleapis.com

```

```
gcloud services enable serviceusage.googleapis.com
```

```
gcloud services enable compute.googleapis.com
```

```
gcloud services enable servicenetworking.googleapis.com --project=$GOOGLE_CLOUD_PROJECT_ID
```

Ensure your Kuberetes Cluster is enabled!

## Running Terraform to provision MultiCloud infrastructure in AWS and Google Cloud

- Execute the following commands to provision infrastructure resources
```
cd ~/mission1/en/terraform/

```

```
terraform init

```

```
terraform plan

```

```
terraform apply

```

Attention: The provisioning process can take between 15 to 25 minutes to finish. Keep the CloudShell open during the process. If disconnected, click on Reconnect when the session expires (the session expires after 5 minutes of inactivity by default)

# Cleaning Up and Starting Over

If you feel that you might have made some mistake, the best option is to clean up your Cloud Shell and start over again. Please use the commands below to clean up your Cloud Shell:

```json
cd ~
rm -rf mission*
rm -rf .aws
```

# Security Tips

- For production environments, it's recommended to use only the Private Network for database access.
- Never provide public network access (0.0.0.0/0) to production databases. ⚠️
# Cleaning Up and Starting Over

If you feel that you might have made some mistake, the best option is to clean up your Cloud Shell and start over again. Please use the commands below to clean up your Cloud Shell:

```json
cd ~
rm -rf mission*
rm -rf .aws
```

# Security Tips

- For production environments, it's recommended to use only the Private Network for database access.
- Never provide public network access (0.0.0.0/0) to production databases. ⚠️

**🎉🚀🚀🚀🚀🚀🚀🚀Step 1 Completed 🚀🚀🚀🚀🚀🚀🚀🎉**
