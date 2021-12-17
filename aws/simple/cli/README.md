# Using AWS Command Line Interface

## Restrictions & Limitations

### AWS CLI does not support username+password login
It is not generally possible to log in to the AWS CLI using AWS account username + password credentials. Supported credentials include:

- Access Key credentials (AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY)
- Temporary credentials incuding:
  - Signed JSON Web Tokens (JWT)
  - OAuth2 / OIDC Tokens
- AWS Single Sign On [AWS Single Sign On (SSO)](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html)

Alternatively, the AWS CLI can be accessed using only username+password credentials by logging into the AWS Console and using [AWS CloudShell](https://aws.amazon.com/cloudshell/).


### AWS CLI does not list shared buckets
The AWS CLI list command, `aws s3 ls`, only shows Buckets that are owned by your account. It does not show buckets in other AWS accounts that you have access to. However it is still possible to view a shared bucket using the AWS CLI, provided you already know the name of the bucket that you want to view using: `s3 ls s3://<BUCKET_NAME>`.

This is an AWS limitation explained [in the AWS knowledge center](https://aws.amazon.com/premiumsupport/knowledge-center/s3-bucket-cross-account-access/).

## Prerequisites

### AWS CLI

The AWS CLI needs to be installed and configured before you can use it. See [the AWS CLI website](https://aws.amazon.com/cli/) for more details.

### Account permissions

Ensure that the IAM user/role being used has the necessary permissions within your account. See the [introduction to AWS shared buckets](../README.md) for more information.

# Instructions

## Download

1. To view the contents of a bucket use `aws s3 ls s3://<BUCKET NAME>`
  For example to view the publicly-available [SpaceNet Dataset](https://registry.opendata.aws/spacenet/) that is located in the `spacenet-dataset` bucket use `aws s3 ls s3://spacenet-dataset`
1. Use `aws s3 cp s3://<BUCKET NAME>/path/to/files /path/to/destination` to download the files/folders that you need. See the `aws s3 cp` [documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) for more information on the arguments that the `cp` command supports.

The [AWS CLI documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/index.html#available-commands) has information about additional `aws s3` commands, such as `aws s3 sync`, that may be of use.

## Upload

1. Use `aws s3 cp /path/to/files s3://<BUCKET NAME>/path/to/destination ` to upload the files/folders that you need. See the `aws s3 cp` [documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) for more information on the arguments that the `cp` command supports.
  
## Troubleshooting

1. To show the AWS CLI configuration run `aws configure list`
1. To get the identity of the currently logged in user run
 `aws sts get-caller-identity` *this call my fail if the STS api is not enabled or you do not have sufficient permissions