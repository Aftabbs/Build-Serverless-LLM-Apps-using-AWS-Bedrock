# Serverless LLM Applications with AWS Bedrock

![image](https://github.com/user-attachments/assets/fce4c18a-a624-4b96-be56-17144d183972)

This project demonstrates how to build serverless applications leveraging AWS Bedrock to harness the power of Large Language Models (LLMs). The applications are designed to handle tasks such as text generation, audio summarization, logging, event-driven generations, and deploying AWS Lambda functions. 

---

## Features

1. **Text Generations**  
   Generate human-like text using LLMs available on AWS Bedrock.

2. **Audio Summarization**  
   Summarize audio files into concise text using AI models.

3. **Logging Enablement**  
   Implement detailed logging to monitor application performance and debug issues.

4. **AWS Lambda Deployment**  
   Deploy serverless Lambda functions to execute code in response to events.

5. **Event-Driven Generations**  
   Trigger text generation based on specific events using AWS services.

---

## Prerequisites

To run this project, ensure you have the following:

- **AWS IAM Account**: Required for access to AWS Bedrock and other AWS services.
- **AWS CLI**: Installed and configured with necessary permissions.
- **Python**: Version 3.7 or later.
- **Libraries**: Install dependencies using the command below:
  ```bash
  pip install boto3
  ```

---

## Architecture Overview

The project leverages AWS serverless architecture, utilizing the following components:

- **AWS Bedrock**: For accessing LLMs.
- **AWS Lambda**: To deploy serverless functions for event-driven operations.
- **Amazon S3**: For storing and processing audio files (optional).
- **Amazon CloudWatch**: For logging and monitoring.

---

## Setup and Deployment

### Step 1: Clone the Repository
```bash
git clone https://github.com/Build-Serverless-LLM-Apps-using-AWS-Bedrock.git
cd serverless-llm-aws-bedrock
```

### Step 2: Configure AWS CLI
```bash
aws configure
```
Provide your Access Key, Secret Key, Region, and Output format.

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Deploy Lambda Function
1. Create a Lambda deployment package:
   ```bash
   zip function.zip lambda_function.py
   ```
2. Deploy the Lambda function:
   ```bash
   aws lambda create-function \
       --function-name TextGenerationFunction \
       --runtime python3.x \
       --role YourIAMRoleARN \
       --handler lambda_function.lambda_handler \
       --zip-file fileb://function.zip
   ```

---

## Usage

### 1. **Text Generation**
   Invoke the Lambda function to generate text:
   ```bash
   aws lambda invoke \
       --function-name TextGenerationFunction \
       --payload '{"input_text": "Write a summary about serverless architecture."}' \
       response.json
   ```

### 2. **Audio Summarization**
   - Upload your audio file to an S3 bucket.
   - Trigger a Lambda function to process and summarize the audio.

### 3. **Event-Driven Generations**
   Use AWS EventBridge or S3 triggers to automatically initiate LLM-based operations.

---

## Logging and Monitoring

Logs are enabled using Amazon CloudWatch. You can view the logs:
```bash
aws logs get-log-events \
    --log-group-name "/aws/lambda/TextGenerationFunction" \
    --log-stream-name "stream-name"
```

---

## Future Enhancements

- Extend support to additional AWS services like Amazon Polly or Amazon Transcribe.
- Improve model integration with fine-tuned models for specific tasks.
- Implement advanced monitoring using AWS X-Ray.

---

**Note**: To run the code in these files in your own environment you will need to install  # some Python dependencies, and also have access to an AWS environment.    # AWS Development Environment Setup: # ------- 1. Create AWS Account and an IAM user.  Follow this guide for more details: https://docs.aws.amazon.com/SetUp/latest/UserGuide/setup-overview.html
- 2. Generate some access keys for your IAM user. For more information see here: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey
- 3. Install the AWS CLI. Follow this guide for more details: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
-  4. Configure AWS CLI: Run 'aws configure' with your access keys, set default region to 'us-west-2' for this code. For more information see here: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html#cli-configure-files-methods
-  5. Use Boto3 for AWS SDK in Python. Your locally run code should interact with your AWS account. https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

-  Note: If using a company AWS account, consult your AWS administrator before proceeding.   , requirements file : This code was developed and tested on Python 3.10   boto3==1.28.68
