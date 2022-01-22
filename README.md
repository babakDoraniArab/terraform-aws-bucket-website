# 
#  <span style="color:yellow">Agenda</span>

if you want to create a static web site with s3 you have to create some resources

1. bucket
2. route53
3. iam
   > you have to use a domain for this configuration
   > I've used `babak.local`. you can use anything you want.don't worry you don't need to buy a domain name for that

after you apply terraform configuration on you aws you can copy your static website into the bucket

## <span style="color:yellow">AWS CLI Command</span>

`aws s3 sync staticSite s3://babak.local`

---

with this command you copy all the files within the staticSite folder


## <span style="color:yellow"> What is your web site url?</span>

you can find it with this formula below

`http://bucket-name.s3-website-Region.amazonaws.com`

for example here bucket-name is `babak.local` and region is `eu-west-1`
so the url is
`http://babak.local.s3-website-eu-west-1.amazonaws.com`


## <span style="color:yellow"> How to use this module?</span>


this is very easy! just do the following steps

`mkdir testFolder`

`cd testFolder`

`testFolder> touch main.tf`

and add the following configuration to the main.tf

```terraform
   provider "aws" {
     profile = "default"
     region  = "eu-west-1"
    }

   variable "domain_name" {
    type = string
    }

   module "bucket-website" {
    source  = "babakDoraniArab/bucket-website/aws"
    version = "1.0.1"
    domain_name = var.domain_name
  # please check the link below and use the latest version
  # https://registry.terraform.io/modules/babakDoraniArab/bucket-website/aws/latest
 ```

 ### 
 ### <span style="color:yellow">final codes</span>

   `terraform init` 

   `terraform fmt`

   `terraform validate`

   `terraform apply`



   <h1 style="color:yellow">congratulation you maid it!</h1>

