# CloudFormation-mini-project
# AWS CloudFormation EC2 Deployment

This project automates the deployment of an EC2 instance in a specific Virtual Private Cloud (VPC) using AWS CloudFormation. The CloudFormation template includes user data, allowing for custom configuration during the instance launch.

## Prerequisites

Before deploying the EC2 instance using CloudFormation, ensure you have the following:

- AWS CLI installed and configured with the necessary credentials.
- Appropriate IAM permissions to create CloudFormation stacks and manage EC2 instances.

## Usage

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/your-username/cloudformation-ec2-deployment.git
    ```

2. Navigate to the project directory:

    ```bash
    cd cloudformation-ec2-deployment
    ```

3. Update the `ec2-deployment.yaml` CloudFormation template with your desired parameters, such as VPC ID, subnet ID, instance type, key pair, etc.

4. Deploy the CloudFormation stack using the AWS CLI:

    ```bash
    aws cloudformation create-stack \
        --stack-name ec2-deployment-stack \
        --template-body file://ec2-deployment.yaml \
        --parameters ParameterKey=VpcId,ParameterValue=your-vpc-id \
                     ParameterKey=SubnetId,ParameterValue=your-subnet-id \
                     ParameterKey=InstanceType,ParameterValue=t2.micro \
                     ParameterKey=KeyName,ParameterValue=your-key-pair-name \
        --capabilities CAPABILITY_IAM
    ```

5. Monitor the stack creation progress in the AWS CloudFormation console or use the following CLI command:

    ```bash
    aws cloudformation describe-stacks --stack-name ec2-deployment-stack
    ```

6. Once the stack is created, retrieve the EC2 instance ID and other details from the CloudFormation outputs.

## Customization

For additional custom configurations during instance launch, update the `user-data.sh` script within the CloudFormation template (`ec2-deployment.yaml`).

## Cleanup

To delete the CloudFormation stack and associated resources, use the following CLI command:

```bash
aws cloudformation delete-stack --stack-name ec2-deployment-stack
