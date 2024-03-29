# [Snyk And Hashicorp - Securing Your Infrastructure As Code Workshop](https://snyk-hashicorp.awsworkshop.io/)

**This is the setup steps to provision your AWS account to participate in the workshop**

## In your AWS account

> [!CAUTION]
> Provisioning this workshop environment in your AWS account will create resources and there will be cost associated with them. The cleanup section provides a guide to remove them, preventing further charges.


This section outlines how to set up the environment to run the labs in your own AWS account. 

What will this CloudFormation Template provision?

- Cloud9 Instance with
   - Snyk Cli
   - Terraform
   - 30 GB Volume
   - clones https://github.com/gautambaghel/vulnerable-ec2 repo



The first step is to create an IDE with the provided CloudFormation template. The easiest way to do this is using AWS CloudShell in the account you will be running the lab exercises. Open CloudShell with the link below or following this [documentation](https://docs.aws.amazon.com/cloudshell/latest/userguide/getting-started.html#launch-region-shell):

https://console.aws.amazon.com/cloudshell/home


> [!TIP]
> If using the link above make sure the AWS console has opened in the region that you wish to run the labs in.

![cloudshell terminal](/assets/images/cloudshell.png)

Once CloudShell has loaded run the following commands:

```
wget -q https://raw.githubusercontent.com/Pjv93/snyk-hashicorp-secure-iac/main/snyk-hashicorp-workshop-ide.yaml
aws cloudformation deploy --stack-name snyk-hashicorp-workshop-ide \
    --template-file ./snyk-hashicorp-workshop-ide.yaml \
    --parameter-overrides RepositoryRef=main \
    --capabilities CAPABILITY_NAMED_IAM
```


The CloudFormation stack will take roughly 5 minutes to deploy, and once completed you can retrieve the URL for the Cloud9 IDE like so:

```
aws cloudformation describe-stacks --stack-name snyk-hashicorp-workshop-ide \
    --query 'Stacks[0].Outputs[?OutputKey==`Cloud9Url`].OutputValue' --output text
```
Open this URL in a web browser to access the IDE:

![cloud9 IDE](/assets/images/cloud9-ide.png)
