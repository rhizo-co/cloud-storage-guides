# Using the Google Cloud Platform Command Line Interface (CLI)

## Restrictions & Limitations

### GCP Console does not list shared buckets
The gsutil tool does not allow you to list all buckets that you have access to. The gsutil tool lists Buckets that belong to a specified project. It is still possible to view a shared bucket in the GCP console, even if you do not know or have access to the bucket's project id, provided you already know the name of the bucket that you want to view, using: `gsutil ls gs://<BUCKET_NAME>`.

## Prerequisites

### gsutil Tool

The gsutil tool (CLI) needs to be installed and configured before you can use it. See [the gsutil documentation](https://cloud.google.com/storage/docs/gsutil) for more details.

Alternatively, the gsutil tool can be accessed without installation and configuration by logging in to the GCP Console and using [Google Cloud Shell](https://cloud.google.com/shell).

# Instructions

## Download

1. To view the contents of a bucket use `gsutil ls gs://<BUCKET NAME>`
  
  For example to view the publicly-available [Landsat Dataset](https://cloud.google.com/storage/docs/public-datasets/landsat) that is located in the `gcp-public-data-landsat` bucket use `gsutil ls gs://gcp-public-data-landsat`

  |  |
  |:--:|
  | <b>Viewing the Landsat Dataset bucket</b> |

2. Use `gsutil -m cp -r gs://<BUCKET NAME>/path/to/files /path/to/destination` to download the files/folders that you need. 
  
  For example to download a small (1.5GB) piece of the  [Landsat Dataset](https://cloud.google.com/storage/docs/public-datasets/landsat) to the local `landsat_dataset/` folder use `gsutil -m cp -r gs://gcp-public-data-landsat/LC08/01/100/010/ ./landsat_dataset/LC08/01/100/`
  |  |
  |:--:|
  | <b> Download a small piece of the Lansat dataset </b> |

See the `gsutil cp` [documentation](https://cloud.google.com/storage/docs/gsutil/commands/cp) for more information on the arguments that the `cp` command supports. The [gsutil tool documentation](https://cloud.google.com/storage/docs/gsutil) also has information about additional `gsutil` commands, such as `gsutil rsync`.

## Upload

1. Use `gsutil -m cp -r /path/to/files gs://<BUCKET NAME>/path/to/destination ` to upload the files/folders that you need. 

See the `gsutil cp` [documentation](https://cloud.google.com/storage/docs/gsutil/commands/cp) for more information on the arguments that the `cp` command supports. The [gsutil tool documentation](https://cloud.google.com/storage/docs/gsutil) also has information about additional `gsutil` commands, such as `gsutil rsync`.
