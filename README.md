# Real Time Data Validation using Serverless

## Overview
This tool is designed for system administrators to automate the processing of CSV files uploaded into AWS S3, detect input errors, and route erroneous files to a specified error's bucket to be reviewed.

## Features
- **Serverless Event Driven:** Triggers real time data validation when a new CSV file is loaded.
- **Re-routing of Erroneous Files** If errors are detected, moves file to an error bucket.

## Prerequisites
- Python 3.x
- `csv` library
- `boto3` library
- CSV file for testing
- AWS account with two S3 buckets
- Boilerplate Lambda function: Create a new function in the AWS console

## Installation
1. **AWS Toolkit**
2. **Sam CLI**
3. **Docker**
4. **Download the boilerplate Lambda function locally**
5. Replace the boilerplate code with code provided in the `lambda_function.py` file in this repository.
6. Update the code to reflect your S3 error bucket name in the `events.json` file. Also tailor the product and item lists to reflect your CVS file columns based on your specific use case.

## Usage
The event driven function will perform real time data validation of CSV files once they are uploaded to an S3 bucket. If errors in the file are found, the file will be moved to a specified errors bucket to be reviewed. 

Invoke the function using the **Sam CLI**:
- `sam local invoke -e event.json` to test locally before deploying to AWS
- `sam remote invoke arn:aws:lambda:...:YourFunctionName --event-file event.json` to manually invoke after deploying completed function to AWS

After uploading the completed function to AWS, you must create the trigger for your Lambda function.
1. In the Lambda console, click Add Trigger
2. Select a Source: S3
3. Choose your default bucket (not the error bucket)
4. Change Event types to "PUT" only
5. Save
6. Test functionality by uploading your CSV file to the default S3 bucket

## Functionality

1. **Python Automation with AWS Resources**
   - The script uses `boto3` to interact with AWS S3.

2. **AWS Lambda Serverless Event Driven:**
   - Uses AWS Lambda trigger to automate the processing of new files uploaded to an S3 bucket.

3. **Data Validation:**
   - Check each entry of a CSV file line by line to detect invalid entries.

## Customization
You can customize the function for your specific use case. Be sure to customize the product_line and item variable lists to reflect your preapproved values specific to your CVS file columns and format. Also change the row number to corresponds to the correct placement in your file.

## Note
Ensure that your AWS credentials are properly configured for `boto3` to interact with AWS Lambda. Also, ensure your Lambda Function has the proper permissions to S3. 

## License
This project is licensed under the [MIT License](LICENSE).
