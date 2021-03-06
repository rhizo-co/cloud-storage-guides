# Using Google Cloud Platform (GCP) Console Web App

## Restrictions & Limitations

### GCP Console only allows downloading one item at a time
The GCP Console only allows downloading individual files one-at-a-time. It is not possible to select multiple files for download or to download a folder in a single operation.  If you want to download more than a handful of files we recommend using the [gsutil tool](https://cloud.google.com/storage/docs/gsutil). A guide for using the gsutil tool to download files from shared buckets is included in this repository in the [cli directory](../cli).

### Console login is only possible with username + password credentials
It is only possible to log in to the GCP Console using username + password (+MFA) credentials.

The following types of credentials do NOT work with the GCP Console, regardless of the type of account being used:

- API Keys
- Service Account Tokens
- Temporary credentials incuding:
  - Signed JSON Web Tokens (JWT)
  - OAuth2 / OIDC Tokens

### GCP Service Accounts cannot log in to the console
It is not possible to log in to the GCP Console using GCP Service Account (sometimes called GCP IAM account) credentials. You should log in using a Google Account. Google (user) Accounts can be personal or part of a Google Workspace or Google Identity Service domain.

### GCP Console does not list shared buckets
The GCP Console Cloud Storage Browser only shows Buckets that belong to the current project that you are viewing. It does not show buckets that are shared with you but belong to other GCP projects. However it is still possible to view a shared bucket in the GCP console, provided you already know the name of the bucket that you want to view, by navigating directly to the bucket's url: `https://console.cloud.google.com/storage/browser/<BUCKET_NAME>`

This is a limitation of GCP.

## Prerequisites

Surprisingly the only prerequisite for using the GCP console to upload or donwload files is having a valid Google (user) Account. If you are encountering problems in the GCP Console check the "Don't Panic" section later in this document.


# Instructions

## Accessing the Bucket's page in the GCP Console

1. [Log in to the GCP Console](https://console.cloud.google.com/) using your username and password.

  | <img width="1159" alt="image" src="https://user-images.githubusercontent.com/8148776/146592776-4cf4da08-3550-49fb-9148-76a333faa94a.png"> |
  |:--:|
  | <b>Don't Panic. Shared buckets do not appear on this page and you do not need to select a project</b> |

2. Construct the bucket's GCP Console URL by replacing `<BUCKET_NAME>` with the name of the bucket that you want to view: `https://console.cloud.google.com/storage/browser/<BUCKET_NAME>`. 

  For example to view the publicly-available [Landsat Dataset](https://cloud.google.com/storage/docs/public-datasets/landsat) that is located in the `gcp-public-data-landsat` bucket use `https://console.cloud.google.com/storage/browser/gcp-public-data-landsat`
  
  | <img width="1162" alt="image" src="https://user-images.githubusercontent.com/8148776/146592903-c59c5e88-90d6-437a-9a2d-1d116e5067cf.png"> |
  |:--:|
  | <b>Viewing the Landsat Dataset bucket</b> |

## Download

1. Follow the instructions above to navigate to the Bucket's page in the GCP Console.
1. Navigate to the folder containing the file to download.
1. Select the file that you want to download.
1. Click the "Download" button.
1. Wait for the download to complete.

## Upload

1. Follow the instructions above to navigate to the Bucket's page in the GCP Console.
1. Navigate to the folder that you want to upload files to.
1. Click on either "Upload Files" or "Upload Folder".
1. Select the files or folder to upload.
1. Click the "Upload" button.
1. Wait for the upload to complete.

## Don't Panic

When you log in to the Google Cloud console you may see messages, warnings or prompts, if you just want to view a shared bucket then you can ignore those messages and continue by entering the bucket's URL in your browser's address bar once you have logged in. Examples of things that you might see and can ignore include:

- Prompts to select or create a project
- Warnings that you do not have permissions to list buckets
- Invitations to begin a free trial of Google Cloud Platform
 
