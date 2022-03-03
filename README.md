# Upload files and folder to S3 from Ubuntu 20.04 using AWS CLI 2

Jan 10, 2021

2 min read

![upload files and folders to S3 using AWS CLI 2](https://miro.medium.com/max/1400/1*80UKmXFR3AgoO1H2qiP5rQ.png)

https://bmshamsnahid.medium.com/upload-files-and-folder-to-s3-from-ubuntu-20-04-using-aws-cli-2-2dd44f544809

By [Shams Nahid](https://bmshamsnahid.medium.com/)

Applicable for Ubuntu 20.04 and its derivatives.

## Creating a IAM User

To make any API call to AWS, we need a IAM user with appropriate permissions. According to the your purpose, create a IAM user and get the followings

- IAM user name
- Access Key ID
- Secret Access Key

You can download a csv file with these information provided by the AWS after creation of IAM user.

## Install AWS CLI in Local Machine

### Install AWS CLI

Install curl if it is not install in your machine. Also, you can use wget the default and preinstalled download manager for Ubuntu.

```java
sudo apt-get install curl
```

Download the AWS installation file

```java
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

Go to the downloaded directory and extract the files

```java
unzip awscliv2.zip
```

Now, run the installation file

```java
sudo ./aws/install
```

This will install the AWS CLI 2 in your system.

To verify the installation, use

```java
aws --version
```

## Configure Account

## To configure your account

aws configure
Now insert the access key id, secret access key, default region name, your desired output format.
This should configure the CLI with your account credentials.
You can test the configuration by invoking the following commands

```java
aws s3 ls
```

This should return all the buckets of your region.

## Upload Files and Folders

If you do not have a S3 bucket create one.

## Upload a Single File

To upload a single file we use the following

```java
aws s3 cp local_file_path s3://bucket_name/
```

Here the local_file_path stands for the local file path we are uploading from our local machine.

The bucket_name stands for our desired cloud S3 Bucket Name.

## Example:

```java
aws s3 cp /home/nahid/Documents/data.json s3://test_bucket/
```

This will upload a file named data.json to a bucket named test_bucket.

## Upload All Files and Folder Recursively

To upload a folder along with all its files and folders, we can do the followings,

```java
aws s3 cp local_folder_path s3://bucket_name/ --recursive
```

Here local_folder_path is the folder we are uploading.

The bucket_name is the desired cloud S3 bucket.

## Example:

```java
aws s3 cp /home/nahid/Documents/build s3://test_bucket/ --recursive
```

Here we are uploading a folder named build to the bucket named test_bucket.

## Reference

https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html
