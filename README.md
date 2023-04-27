# AWS Terraform Backend

This CloudFormation template creates an S3 bucket and DynamoDB table suitable
for a \[Terraform S3 State Backend\]. 

## Setup

- [Go to the Cloudformation page of your region](https://eu-west-1.console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks?filteringText=&filteringStatus=active&viewNested=true). 
- Select "Create Stack" > "with new resources"
![./assets/create-stack.png](assets/create-stack.png)
- "upload a template" > Next
![assets/upload-template.png](assets/upload-template.png)
- Provide the name "aws-terraform-backend"
![assets/setup.png](assets/setup.png)
- Click Next > Submit

## Parameters

- __`StateBucketName`__ (`String`): Name of the S3 bucket used to store the
  terraform state
- __`LockTableName`__ (`String`): Name of the DynamoDB table to store the
  terraform state lock

## Resources

- __`LockTable`__ (`AWS::DynamoDB::Table`): DynamoDB table to lock Terraform
- __`StateBucket`__ (`AWS::S3::Bucket`): Bucket containing Terraform state
- __`StateBucketPolicy`__ (`AWS::S3::BucketPolicy`): Bucket policy for the state
  bucket enforcing encryption

## Outputs

- __`StackName`__: Name of the CloudFormation stack
- __`Region`__: Region in which the S3 state backend resources are created
- __`StateBucketName`__: Name of the S3 bucket containing Terraform state
- __`LockTableName`__: Name of the DynamoDB table used to lock Terraform state
