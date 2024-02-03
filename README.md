We will Start by Creating a VPC
Below we will mention the different steps we follow to make it happen on Dashboard
after that we will create an S3 Bucket.

Issue we encountered: 
-- We missed the correct arn (Need to make sure to use the arn on the IAM user instead of s3bucket)
-- We missed the destination path (We suppose to use the same name s5groups3bucket but we use destination, and 
we use destination-s5groups3bucket)

Below is the policy we use , we can adjust accordily 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::846957663388:user/terraformTest"
            },
            "Action": [
              "s3:GetObject",
               "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::s5groups3bucket/*",
                "arn:aws:s3:::s5groups3bucket"
            ]
        },
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::846957663388:user/terraformTest"
            },
            "Action": [
                "s3:ReplicateObject",
                "s3:ReplicateDelete",
                "s3:ReplicateTags",
                "s3:GetObjectVersionTagging"
            ],
            "Resource": "arn:aws:s3:::s5groups3bucket/*"
        }
    ]
}
+++++++++++++++++++++++++++++++++++++++

Structure of the VPC
eips.tf
igw.tf
nat.tf
provider.tf
route-table-association.tf
routes.tf
subnets.tf
terraform.tfvars
variables.tf

Structure of s3-backend
main.tf
provider.tf
terraform.tfvars
variables.tf

Structure of s3-backend-with-replication
main.tf
provider.tf
terraform.tfvars
variables.tf


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
We will start with the module  for the VPC 

To create our provider tehdifferents steps will follow:
Go on google type aws then > choose aws provider > Click Upper corner right "USE PROVIDER"
Ten click on it to generate the default code.
https://registry.terraform.io/providers/hashicorp/aws/latest





















