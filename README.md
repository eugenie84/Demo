# Demo

This project automates the deployment of an EC2 instance in a specific Virtual Private Cloud (VPC) using AWS CloudFormation. The CloudFormation template includes user data, allowing for custom configuration during the instance launch.

## Prerequisites if you which to use the CLI(Command Line Interphase)

Before deploying the EC2 instance using CloudFormation, ensure you have the following:

- AWS CLI installed and configured with the necessary credentials.
- Appropriate IAM permissions to create CloudFormation stacks and manage EC2 instances.

## Usage

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/eugenie84/CloudFormation-mini-project.git
    ```

2. Navigate to the project directory:

    ```bash
    cd Sample-EC2.yml
    ```

3. Update the `Sample-EC2.yml` CloudFormation template with your desired parameters, such as VPC ID, subnet ID, instance type, key pair, etc.

4. Deploy the CloudFormation stack using the AWS CLI:

    ```bash
    aws cloudformation create-stack \
        --stack-name ec2-deployment-stack \
        --template-body file://Sample-EC2.yml \
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

For additional custom configurations during instance launch, update the `user-data.sh` script within the CloudFormation template (`Sample-EC2.yml`).

## Cleanup

To delete the CloudFormation stack and associated resources, use the following CLI command:

```bash
aws cloudformation delete-stack --stack-name ec2-deployment-stack
