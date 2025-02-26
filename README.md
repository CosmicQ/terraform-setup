# terraform-setup
Templates to setup terraform in GCP

Reference: https://developer.hashicorp.com/terraform/language/backend/gcs

"Stores the state as an object in a configurable prefix in a pre-existing bucket on Google Cloud Storage (GCS). The bucket must exist prior to configuring the backend.

This backend supports state locking."

This means we only need to setup the bucket because it can handle the locking.

First, authenticate to Google Cloud
```
gcloud auth login
```

Find your project ID from the list
```
gcloud projects list
```
Set your project
```
gcloud config set project my-project-id
```

Deploy
```
gcloud deployment-manager deployments create terraform-setup --config terraform.yml
```

Or if you need to make changes
```
gcloud deployment-manager deployments update terraform-setup --config terraform.yml
```