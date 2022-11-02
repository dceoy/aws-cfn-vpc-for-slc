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

3.  Deploy VPC stacks for private subnets and a VPC endpoint.

    ```sh
    $ rain deploy vpc-private-subnets-and-s3-endpoint.cfn.yml vpc-private-subnets-and-s3-endpoint
    ```

4.  Deploy VPC stacks for public subnets and a NAT gateway for internet access. (optional)

    ```sh
    $ rain deploy vpc-public-subnets-and-nat-gateway.cfn.yml vpc-public-subnets-and-nat-gateway
    ```
