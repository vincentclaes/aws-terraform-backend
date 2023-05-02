# AWS Terraform Backend

This CloudFormation template creates an S3 bucket and DynamoDB table suitable
for a Terraform S3 State Backend.

## Setup

- [Go to the Cloudformation page of your region](https://eu-west-1.console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks?filteringText=&filteringStatus=active&viewNested=true).
- Select "Create Stack" > "With new resources"
- "Upload a template" > Upload [cloudformation.yml](cloudformation.yml) > Click Next
- Provide the name "aws-terraform-backend"
- Click Next > Click Submit
- Get from the Cloudformation output the S3 bucket name and the DynamoDB
- [Follow the official documentation on how to configure terraform to use S3 + Dynamodb](https://developer.hashicorp.com/terraform/language/settings/backends/s3#s3)

## Resources

- __`LockTable`__ (`AWS::DynamoDB::Table`): DynamoDB table to lock Terraform
- __`StateBucket`__ (`AWS::S3::Bucket`): Bucket containing Terraform state

## Outputs

- __`StackName`__: Name of the CloudFormation stack
- __`Region`__: Region in which the S3 state backend resources are created
- __`StateBucketName`__: Name of the S3 bucket containing Terraform state
- __`LockTableName`__: Name of the DynamoDB table used to lock Terraform state
