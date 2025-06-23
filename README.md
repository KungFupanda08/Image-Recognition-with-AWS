project:
  name: Image Recognition with AWS Lambda, Rekognition & S3
  description: >
    A serverless image recognition pipeline using AWS services.
    Upload an image to S3, trigger a Lambda function, and analyze the image using Amazon Rekognition.

features:
  - Upload an image to S3
  - Automatically trigger AWS Lambda
  - Detect labels and objects using Rekognition
  - Log results to CloudWatch

technologies:
  - Amazon S3
  - AWS Lambda
  - Amazon Rekognition
  - AWS CloudFormation
  - GitHub Actions (optional for CI/CD)

workflow:
  steps:
    - Upload image to S3 bucket
    - Trigger Lambda function via S3 event
    - Analyze image using Amazon Rekognition
    - Log or store results

project_structure:
  - template.yaml: CloudFormation template
  - lambda/index.py: Lambda function code
  - test-images/: Sample images
  - .github/workflows/deploy.yml: CI/CD automation (optional)
  - README.md: Project documentation

deployment:
  prerequisites:
    - AWS CLI configured
    - AWS account with required permissions
    - Python 3.x
    - Docker (optional for packaging)
  steps:
    - Deploy with CloudFormation:
        command: >
          aws cloudformation deploy --template-file template.yaml
          --stack-name image-rekognition-stack --capabilities CAPABILITY_NAMED_IAM
    - Upload an image to the S3 bucket
    - View results in CloudWatch logs

ci_cd:
  tool: GitHub Actions
  trigger: Push changes to template.yaml or Lambda source code
  actions:
    - Redeploy Lambda function
    - Update CloudFormation stack

sample_output:
  Labels:
    - Name: Person
      Confidence: 98.2
    - Name: Car
      Confidence: 89.1

learning_objectives:
  - Understand serverless design on AWS
  - Use event-driven architecture with S3 and Lambda
  - Analyze images with Rekognition API
  - Automate deployments using CloudFormation and GitHub Actions

credits:
  author: Your Name
  purpose: Hands-on learning with AWS serverless and AI services

license: MIT
