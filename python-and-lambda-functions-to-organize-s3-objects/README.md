# S3 File Moving Lambda Script

This README provides guidance on setting up an AWS Lambda function to trigger when a file is uploaded to an S3 bucket. The Lambda function will move the uploaded file to a folder named `YYYYMMDD` based on the creation date of the file in the S3 bucket.

## Prerequisites

- AWS Account
- AWS IAM Role with appropriate permissions to access S3 and execute Lambda functions.
- Basic understanding of AWS Lambda, S3, and Python programming.

## Steps

### 1. Create an S3 Bucket

If you haven't already, create an S3 bucket where the files will be uploaded.

### 2. Create a Lambda Function

Create a new Lambda function in the AWS Lambda console.

- Choose a runtime. Python is commonly used for Lambda functions.
- Configure the function with the appropriate IAM role that allows it to access S3 buckets.
- Set up the trigger to be the S3 bucket you created earlier. Specify the event type as "Object Created (All)" or "Object Created (PUT)" depending on your requirements.

### 3. Write Lambda Function Code

Write the Lambda function code. Below is a sample Python code that moves the file to a folder named `YYYYMMDD` based on its creation date:

```python
import boto3
import os
from datetime import datetime

s3 = boto3.client('s3')

def lambda_handler(event, context):
    for record in event['Records']:
        bucket_name = record['s3']['bucket']['name']
        object_key = record['s3']['object']['key']
        created_date = record['eventTime']
        
        # Extract YYYYMMDD from creation date
        yyyy_mm_dd = datetime.strptime(created_date, '%Y-%m-%dT%H:%M:%SZ').strftime('%Y%m%d')
        
        # Define the new key
        new_key = f"{yyyy_mm_dd}/{os.path.basename(object_key)}"
        
        # Move the object
        s3.copy_object(
            Bucket=bucket_name,
            Key=new_key,
            CopySource={'Bucket': bucket_name, 'Key': object_key}
        )
        
        # Delete the original object
        s3.delete_object(Bucket=bucket_name, Key=object_key)
        
        print(f"Moved {object_key} to {new_key}")
```

### 4. Test the Lambda Function

Test the Lambda function by uploading a file to the S3 bucket and verifying if it gets moved to the correct folder based on its creation date.

### 5. Deployment

Deploy the Lambda function once you have tested it thoroughly and ensure it works as expected.

## Conclusion

You have successfully set up a Lambda function to trigger when a file is uploaded to an S3 bucket and move it to a folder named `YYYYMMDD` based on its creation date. Further customization can be done based on specific requirements or business logic.

Python scripts made are avilable here: https://github.com/JEgg96/python-projects
