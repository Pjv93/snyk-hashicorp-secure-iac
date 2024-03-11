# snyk-hashicorp-secure-iac
SNYK AND HASHICORP SECURING YOUR INFRASTRUCTURE AS CODE Workshop CFT [https://snyk-hashicorp.awsworkshop.io/] 

In your AWS account
[!CAUTION]
Provisioning this workshop environment in your AWS account will create resources and there will be cost associated with them. The cleanup section provides a guide to remove them, preventing further charges.

This section outlines how to set up the environment to run the labs in your own AWS account. 

The first step is to create an IDE with the provided CloudFormation template. The easiest way to do this is using AWS CloudShell in the account you will be running the lab exercises. Open CloudShell with the link below or following this documentation:

https://console.aws.amazon.com/cloudshell/home

[!TIP]
If using the link above make sure the AWS console has opened in the region that you wish to run the labs in.


Once CloudShell has loaded run the following commands:

```sh wget -q https://raw.githubusercontent.com/Pjv93/snyk-hashicorp-secure-iac/main/snyk-hashicorp-workshop-ide.yaml
aws cloudformation deploy --stack-name snyk-hashicorp-workshop-ide \
    --template-file ./snyk-hashicorp-workshop-ide.yaml \
    --parameter-overrides RepositoryRef=main \
    --capabilities CAPABILITY_NAMED_IAM
```

The CloudFormation stack will take roughly 5 minutes to deploy, and once completed you can retrieve the URL for the Cloud9 IDE like so:

```sh aws cloudformation describe-stacks --stack-name snyk-hashicorp-workshop-ide \
    --query 'Stacks[0].Outputs[?OutputKey==`Cloud9Url`].OutputValue' --output text
```
