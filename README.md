aws-cfn-vpc-for-slc
===================

AWS CloudFormation stacks of VPC for serverless computing

[![Lint](https://github.com/dceoy/aws-cfn-vpc-for-slc/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/aws-cfn-vpc-for-slc/actions/workflows/lint.yml)

Installation
------------

1.  Check out the repository.

    ```sh
    $ git clone git@github.com:dceoy/aws-cfn-vpc-for-slc.git
    $ cd aws-cfn-vpc-for-slc
    ```

2.  Install [Rain](https://github.com/aws-cloudformation/rain) and set `~/.aws/config` and `~/.aws/credentials`.

3.  Deploy VPC stacks for private subnets with gateway endpoints.

    ```sh
    $ rain deploy \
        vpc-private-subnets-with-gateway-endpoints.cfn.yml \
        vpc-private-subnets-with-gateway-endpoints
    ```

4.  Deploy VPC stacks for interface endpoints. (optional)

    ```sh
    $ rain deploy \
        vpc-interface-endpoints-for-ecr-and-ecs.cfn.yml \
        vpc-interface-endpoints-for-ecr-and-ecs
    ```

5.  Deploy VPC stacks for public subnets. (optional)

    - public subnets with NAT gateways

      ```sh
      $ rain deploy \
          vpc-public-subnets-with-nat-gateway-per-az.cfn.yml \
          vpc-public-subnets-with-nat-gateway-per-az
      ```

    - public subnets with a NAT gateway in 1 AZ

      ```sh
      $ rain deploy \
          vpc-public-subnets-with-nat-gateway-in-1az.cfn.yml \
          vpc-public-subnets-with-nat-gateway-in-1az
      ```

    - public subnets without NAT gateway

      ```sh
      $ rain deploy \
          vpc-public-subnets.cfn.yml vpc-public-subnets
      ```

6.  Deploy EC2 stacks for an EC2 instance. (optional)

    ```sh
    # Create EC2 key pair
    $ aws ec2 create-key-pair \
        --key-name MyKeyPair --query 'KeyMaterial' --output text \
        > MyKeyPair.pem
    $ chmod 400 MyKeyPair.pem

    # Deploy the stacks
    $ rain deploy \
        vpc-interface-endpoints-for-ssm-and-ec2.cfn.yml \
        vpc-interface-endpoints-for-ssm-and-ec2
    $ rain deploy \
        ec2-instance-with-iam-role.cfn.yml \
        ec2-instance-with-iam-role
    ```
