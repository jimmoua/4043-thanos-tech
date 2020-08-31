<h1>Table of Contents</h1>

- [AWS Serverless Resources](#aws-serverless-resources)
  - [Cognito](#cognito)
  - [API Gateway](#api-gateway)
  - [Lambda](#lambda)
    - [What is Lambda](#what-is-lambda)
    - [Lambda Function](#lambda-function)
    - [Packaging Functions](#packaging-functions)
    - [Execution Model](#execution-model)
  - [DynamoDB](#dynamodb)
  - [S3](#s3)
    - [Enabling CORS](#enabling-cors)
  - [CloudFront](#cloudfront)
  - [Route 53](#route-53)
  - [Certificate Manager](#certificate-manager)
- [Other AWS Stuff](#other-aws-stuff)
  - [ARN](#arn)
    - [Use Cases](#use-cases)
      - [Communication](#communication)
      - [IAM Policy](#iam-policy)
- [Serverless Framework](#serverless-framework)
  - [`serverless.yml`](#serverlessyml)

# AWS Serverless Resources
Below are the services that are important to the serverless stack.

## Cognito
Cognito lets users sign up, in, and access our web applications quickly and easily.

## API Gateway
Fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure API's at any scale.

Can handle all tasks involving accepting and processing countless concurrent API calls including traffic managements, CORS support, authorization, etc.

Pay only for the API calls that we receive.

> API Gateway makes it easy for developers to create, publish, maintain, monitor, and secure APIs.

## Lambda
What is AWS Lambda?
> AWS Lambda is a compute service that lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running.

+ Run code without any administration.
+ We can also set up our code to trigger other AWS services or call it directly from any web or mobile application.

### What is Lambda
Lambda is a pay-as-you-go serverless computing service from AWS. It's really nice because we don't have to manage an actual server. This means it is cheaper as well, since we only pay for the functions that are executed by customers.

### Lambda Function

![](https://d33wubrfki0l68.cloudfront.net/431b4864a64ada20df9ccccc8a4f4b2e8274b9f8/40bad/assets/anatomy-of-a-lambda-function.png)

|    Name     |                                    Description                                     |
| :---------: | :--------------------------------------------------------------------------------: |
| `myHandler` |                            Name of our Lambda function                             |
|   `event`   |                  Contains information about event being triggered                  |
|  `context`  |          Contains information about the runtime our Lambda is running in           |
| `callback ` | Call this callback function with the results or errors and AWS will respond to it. |

### Packaging Functions
Lambda functions have to packaged and sent to AWS. This is the process of compressing the function and all of its dependencies and uploading it onto an S3 bucket. **Have you let AWS know to use this package upon a specific event trigger**. We can use the [Serverless Framework](https://www.serverless.com/) to help us with this process.

### Execution Model
The model or runtime that will be executing our function is all handled by AWS.

> Firstly, our functions are effectively stateless. Secondly, each request (or event) is served by a single instance of a Lambda function. This means that you are not going to be handling concurrent requests in your code. AWS brings up a container whenever there is a new request. It does make some optimizations here.

What does it mean to be a stateless function?

> The above execution model makes Lambda functions effectively stateless. This means that every time your Lambda function is triggered by an event it is invoked in a completely new environment. You don’t have access to the execution context of the previous event.

## DynamoDB
Each DynamoDB table has a primary key that can't be changed once set. The primary key uniquely identifies each item in the table so that no two items have the same key. There is support for two types of keys:
1. Partition Key
2. Partition and sort key (composite keys)

The composite key will give us more flexibility when querying data.

> It is also a good idea to set up backups for your DynamoDB table, especially if you are planning to use it in production.

## S3
It's an object storage device. Using this, we can send files to our REST API and have it store files.

> You can store any object in S3 including images, videos, files, etc. Objects are organized into buckets, and identified within each bucket by a unique, user-assigned key.

### Enabling CORS
> By default, S3 does not allow its resources to be accessed from a different domain. However, cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain.

## CloudFront
Fast CDN service that securely delivers data, videos, applications, and API's to customers globally with low latency.

## Route 53
Highly available and scalable cloud DNS web service. Designed to give developers and businesses a reliable and cost effective way to route end users to Internet applications by translating `www.example.com` to an IP address like `192.0.2.1`.

Route 53 is fully compliant with IPv6 as well.

Offers Domain Name Registration. We can purchase and manage our domain names and Route 53 will automatically configure our DNS settings for the domains.

## Certificate Manager
Let's us provision, manage, and deploy public and private SSL/TSL certificates for use with AWS services.

+ Quickly request certificates, deploy on ACM-integrated AWS, and handles renewals.

# Other AWS Stuff

## ARN
ARN stands for Amazon Resource Name. They are globally unique identifiers that identify an AWS resource.

### Use Cases

#### Communication

> ARN is used to reference a specific resource when you orchestrate a system involving multiple AWS resources. For example, you have an API Gateway listening for RESTful APIs and invoking the corresponding Lambda function based on the API path and request method. The routing looks like the following.


#### IAM Policy

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": ["s3:GetObject"],
    "Resource": "arn:aws:s3:::Hello-bucket/*"
  }
}
```

> ARN is used to define which resource (S3 bucket in this case) the access is granted for. The wildcard `*` character is used here to match all resources inside the Hello-bucket.


# Serverless Framework

## `serverless.yml`

This file contains the configuration on what AWS services Serverless will provision and how to configure them.

**Here is the default that came with the serverless framework on CLI**:

```yml
# NOTE: update this with your service name
service: notes-app-api

# Create an optimized package for our functions 
package:
  individually: true

plugins:
  - serverless-bundle # Package our functions with Webpack
  - serverless-offline
  - serverless-dotenv-plugin # Load .env as environment variables

provider:
  name: aws
  runtime: nodejs12.x
  stage: prod
  region: us-east-1
  # To load environment variables externally
  # rename env.example to .env and uncomment
  # the following line. Also, make sure to not
  # commit your .env.
  #
  #environment:
  #  SAMPLE_ENV_VAR: ${env:SAMPLE_ENV_VAR}
```

**Service name**:
> The `service` name is pretty important. We are calling our service the `notes-app-api`. Serverless Framework creates your stack on AWS using this as the name. This means that if you change the name and deploy your project, it will create a completely new project!

**Important plugins that the authors have included**:
> You’ll notice the plugins that we’ve included — `serverless-bundle`, `serverless-offline`, and `serverless-dotenv-plugin`. The `serverless-offline` plugin is helpful for local development. While the `serverless-dotenv-plugin` will be used later to load the .env files as Lambda environment variables.

> On the other hand, we use the `serverless-bundle` plugin to allow us to write our Lambda functions using a flavor of JavaScript that’s similar to the one we’ll be using in our frontend React app.