# Using AWS Console Web App

## Restrictions & Limitations

### AWS Console only allows downloading one item at a time
The AWS console only allows downloading individual files one-at-a-time. It is not possible to select multiple files for download or to download a folder in a single operation.  If you want to download more than a handful of files we recommend using the [AWS Command Line Interface](https://aws.amazon.com/cli/). A guide for using the AWS Command Line interface is included in this repository in the [cli directory](../cli).

### Console username + password credentials only
It is only possible to log in to the AWS Console using IAM or root username + password credentials. For IAM users console access must be enabled.

The following types of credentials do NOT work with the AWS Console:

- Access Key credentials (AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY)
- Temporary credentials incuding:
  - Signed JSON Web Tokens (JWT)
  - OAuth2 / OIDC Tokens

### AWS Console does not list shared buckets
The AWS Console Buckets list only shows Buckets that are owned by your account. It does not show buckets in other AWS accounts that you have access to. However it is still possible to view a shared bucket in the AWS console, provided you already know the name of the bucket that you want to view, by navigating directly to the bucket's url: `https://s3.console.aws.amazon.com/s3/buckets/<BUCKET_NAME>`

This is an AWS limitation explained [in the AWS knowledge center](https://aws.amazon.com/premiumsupport/knowledge-center/s3-bucket-cross-account-access/).

# Prerequisites

## Account permissions

Your user must have been granted permission to perform AWS S3 actions within its own AWS account.
TODO: test the exact details of this and link to relevant info

# Instructions

## Accessing the Bucket's page in the AWS Console

1. [Log in to the aws console](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html) using your AWS username and password.
  <figure>
  <img width="1176" alt="image" src="https://user-images.githubusercontent.com/8148776/146166819-d0b24bb4-44d1-4d69-b441-852e2a8c6766.png">
  <figcaption align="center"><b>Don't Panic. Shared buckets do not appear on this page</b></figcaption>
  </figure>


2. Construct the bucket's AWS Console URL by replacing `<BUCKET_NAME>` with the name of the bucket that you want to view in `https://s3.console.aws.amazon.com/s3/buckets/<BUCKET_NAME>`. 

  For example to view the publicly-available [SpaceNet Dataset](https://registry.opendata.aws/spacenet/) that is located in the `spacenet-dataset` bucket use `https://s3.console.aws.amazon.com/s3/buckets/spacenet-dataset`
| <img width="1176" alt="image" src="https://user-images.githubusercontent.com/8148776/146167439-b8b8b6c2-f967-476a-a00f-69752e8c674b.png"> |
|:--:|
| <b>Viewing the SpaceNet Dataset bucket</b> |

## Download

1. Follow the instructions above to navigate to the Bucket's page in the AWS Console.
1. Navigate to the folder containing the file to download.
1. Select the file that you want to download.
1. Click the "Download" button.
1. Wait for the download to complete.

## Upload

1. Follow the instructions above to navigate to the Bucket's page in the AWS Console.
1. Navigate to the folder that you want to upload files to.
1. Click the "Upload" button.
1. Drag and drop, or use the "Add Files" or "Add Folder" buttons to choose the files to upload
1. Click the "Upload" button.
1. Wait for the upload to complete.
