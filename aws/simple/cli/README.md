# Using AWS Command Line Interface

## Restrictions & Limitations

### AWS CLI does not support username+password login
It is generally not  possible to log in to the AWS CLI using AWS account username + password credentials. Supported credentials include:

- Access Key credentials (AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY)
- Temporary credentials incuding:
  - Signed JSON Web Tokens (JWT)
  - OAuth2 / OIDC Tokens
- AWS Single Sign On [AWS Single Sign On (SSO)](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html)

Alternatively, the AWS CLI can be accessed using username+password credentials by logging into the AWS Console and using [AWS CloudShell](https://aws.amazon.com/cloudshell/).


### AWS CLI does not list shared buckets
The AWS CLI list command, `aws s3 ls`, only shows Buckets that are owned by your account. It does not show buckets in other AWS accounts that you have access to. However it is still possible to view a shared bucket using the AWS CLI, provided you already know the name of the bucket that you want to view using: `s3 ls s3://<BUCKET_NAME>`.

This is an AWS limitation explained [in the AWS knowledge center](https://aws.amazon.com/premiumsupport/knowledge-center/s3-bucket-cross-account-access/).

# Prerequisites

## AWS CLI

The AWS CLI needs to be installed and configured before you can use it. See [the AWS CLI website](https://aws.amazon.com/cli/) for more details.

## Account permissions

Ensure that the IAM user/role being used has the necessary permissions within your account. See the [introduction to AWS shared buckets](../README.md) for more information.

# Instructions

## Download

1. To view the contents of a bucket use `aws s3 ls s3://<BUCKET NAME>`
  
  For example to view the publicly-available ["Helpful Sentences from Reviews" dataset](https://registry.opendata.aws/helpful-sentences-from-reviews/), located in the `helpful-sentences-from-reviews` bucket, use `aws s3 ls s3://helpful-sentences-from-reviews/`
  | <img width="896" alt="image" src="https://user-images.githubusercontent.com/8148776/146378233-17402f3b-77e3-4fb7-8d39-2304060aae07.png"> |
  |:--:|
  | <b> Viewing the contents of the Helpful Sentences from Reviews dataset </b> |
  
2. Use `aws s3 cp --recursive s3://<BUCKET NAME>/path/to/files /path/to/destination` to download the files/folders that you need. 
  
  For example to download the ["Helpful Sentences from Reviews" dataset](https://registry.opendata.aws/helpful-sentences-from-reviews/) to the local `sentences_dataset/` folder use `aws s3 cp --recursive  s3://helpful-sentences-from-reviews/ ./sentences_data`
  | <img width="974" alt="image" src="https://user-images.githubusercontent.com/8148776/146379034-fc0cd705-0152-4da7-9d9c-54db370d0080.png"> |
  |:--:|
  | <b> Download the Helpful Sentences from Reviews dataset </b> |

See the `aws s3 cp` [documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) for more information on the arguments that the `cp` command supports. The [AWS CLI documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/index.html#available-commands) also has information about additional `aws s3` commands, such as `aws s3 sync`.

## Upload

1. Use `aws s3 cp --recursive /path/to/files s3://<BUCKET NAME>/path/to/destination ` to upload the files/folders that you need. See the `aws s3 cp` [documentation](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) for more information on the arguments that the `cp` command supports.
  
## Troubleshooting

1. To show the AWS CLI configuration run `aws configure list`
1. To get the identity of the currently logged in user run
 `aws sts get-caller-identity` *this call my fail if the STS api is not enabled or you do not have sufficient permissions
 
| <img width="630" alt="image" src="https://user-images.githubusercontent.com/8148776/146238709-85862735-ba4e-4d2b-8512-1bd95cb9006d.png"> |
|:--:|
| <b> Using `sts get caller-identity` to check what identity is currently being used </b> |

<CodeSample>
  <Python src='./example.py'/>
  <Javascript/>
</CodeSample>
