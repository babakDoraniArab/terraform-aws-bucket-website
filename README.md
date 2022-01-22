# Agenda
if you want to create a static web site with s3 you have to create some resources
1. bucket 
2. route53
3. iam 
	>
    > you have to use a domain for this configuration
    > I've used `babak.local`. you can use anything you want.don't worry you don't need to buy a domain name for that

    


after you apply terraform configuration on you aws you can copy your static website into the bucket 
## AWS CLI Command 
 `aws s3 sync staticSite s3://babak.local`
 ---
 with this command you copy all the files within the staticSite folder

 ## What is your web site url ?
  you can find it with this formula below

  `http://bucket-name.s3-website-Region.amazonaws.com`

  for example here bucket-name is `babak.local` and region is `eu-west-1`
  so the url is 
  `http://babak.local.s3-website-eu-west-1.amazonaws.com`