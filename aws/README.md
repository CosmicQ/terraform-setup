# Terraform State Storage and Locking with S3 and DynamoDB

## Overview
This setup creates the following AWS resources for managing Terraform state:  
1. **S3 Bucket** with versioning and encryption for remote state storage.  
2. **DynamoDB Table** for state locking and consistency.  
3. **IAM Role and Policy** for secure access to these resources.

## Prerequisites
- AWS CLI installed and configured.  
- Terraform version 1.3.0 or higher.  
- Access to deploy CloudFormation stacks in your AWS account.

## How to Deploy the CloudFormation Stack
1. Save the CloudFormation template as `terraform-state-setup.yaml`.  
2. Deploy the stack using the AWS CLI:
   ```bash
   aws cloudformation create-stack --stack-name terraform-state-setup \
   --template-body file://terraform-state-setup.yaml \
   --capabilities CAPABILITY_NAMED_IAM


Example
```
terraform {
  required_version = ">= 1.3.0"
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "global/s3/terraform.tfstate"
    region         = "us-west-2"
    encrypt        = true
    dynamodb_table = "terraform-state-lock"
  }
}
```
