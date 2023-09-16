
# Provisioning the Amazon EKS cluster using Terraform
This repository contains the terraform file code, which we can use to provision the Amazon EKS cluster.

## Architecture Diagram

![Architecture Diagram](https://cdn-images-1.medium.com/max/800/1*T5IRoSoiqT8qnYLUprsRUQ.png)



## Installation of Terraform
Follow the blog to Install the Terraform and another dependency.

1️⃣ Clone the repo

``` https://github.com/lateef-taiwo/HMS-terraform-kube ```

2️⃣ Let's install dependency to deploy the application

``` 
cd HMS-terraform-kube/HMS-App/
terraform init
```

3️⃣ Edit the below file according to your configuration

`vim HMS-terraform-kube/HMS-App/backend.tf`

add below code

```
terraform {
  backend "s3" {
    bucket = "S3-BUCKET-NAME"
    key    = "backend/TFSTATE-FILE.tfstate"
    region = "us-east-1"
    dynamodb_table = "DYNAMODB-TABLE-NAME"
  }
}
```

Let's set up the variable for our Infrastructure and create one file with the name of terraform.tfvars inside kube_terraform/ToDo-App/backend.tf and add the below conntent into that file.

```
REGION          = "us-east-1"
PROJECT_NAME    = "HMS-App"
VPC_CIDR         = "192.168.0.0/16"
PUB_SUB1_CIDR = "192.168.0.0/18"
PUB_SUB2_CIDR = "192.168.64.0/18"
PRI_SUB3_CIDR = "192.168.128.0/18"
PRI_SUB4_CIDR = "192.168.192.0/18"
```

Please note that the above file is crucial for setting up the infrastructure, so pay close attention to the values you enter for each variable.

It's time to build the infrastructure

The below command will tell you what terraform is going to create.

`terraform plan`

Finally, HIT the below command to create the infrastructure...

`terraform apply`

type yes, and it will prompt you for permission or use --auto-approve in the command above.

This Project was accomplished using these three GitHub repositories.

➡️ [App Code] (https://github.com/lateef-taiwo/HospitalManagementSystem)

➡️ [Terraform code] (https://github.com/lateef-taiwo/HMS-terraform-kube)

➡️ [Kubernetes Manifest Repo] (https://github.com/lateef-taiwo/HMS_kube_manifest)
