# Terraform State Storage and Locking in Google Cloud

## Overview
This setup creates:  
1. **Google Cloud Storage (GCS)** bucket for Terraform remote state storage with versioning and encryption.  
2. **Cloud Firestore** for state locking to avoid concurrent Terraform operations.  
3. **IAM Roles** for secure access to the state bucket and Firestore.

## Prerequisites
- gcloud CLI installed and configured.  
- Terraform version 1.3.0 or higher.  
- Access to deploy Deployment Manager templates in your GCP project.

## Deploying the Deployment Manager Template
1. Save the template as `terraform-state-setup.yaml`.  
2. Deploy it using the gcloud CLI:
   ```bash
   gcloud deployment-manager deployments create terraform-state-setup \
   --config terraform-state-setup.yaml


Example
'''
terraform {
  required_version = ">= 1.3.0"
  backend "gcs" {
    bucket  = "terraform-state-bucket"
    prefix  = "terraform/state"
    project = "your-gcp-project-id"
  }
}
'''
