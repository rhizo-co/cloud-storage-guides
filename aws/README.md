# Introduction to Shared AWS Storage (buckets)

## Overview

TODO

# Required Permissions

## IAM permissions in user's account

Rhizo grants permissions on the shared bucket to the IAM users or roles that you specify. 

However those permissions alone are not sufficient for IAM users/roles to access a shared bucket. 

The users/roles being used must also have sufficient permissions *within the scope of their own AWS account* to perform the desired AWS S3 actions on the shared bucket.

TODO: test the exact details of this and link to relevant info
