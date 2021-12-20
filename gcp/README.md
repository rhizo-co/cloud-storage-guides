# Introduction to Shared GCP Storage (buckets)

## Overview

TODO

# Required Information

- Principal Type that you want us to grant access to the shared bucket - this can be: user, service account, group or domain.
- Principal name to grant access to the shared bucket - for users, service accounts and groups this is an email address, for domains it is a domain or subdomain name (e.g. example.com or staff.example.com).

The [Google Cloud IAM documentation](https://cloud.google.com/iam/docs/overview#concepts_related_identity) has more information on identity concepts in Google Cloud.

# Required Permissions

Accessing shared buckets does not require a user to have any permissions set in their own project or domain.
