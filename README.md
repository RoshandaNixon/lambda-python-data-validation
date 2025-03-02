# lambda-python-data-validation
Automate Data Validation for CSV files using AWS Lambda and Python Boto3

# Real Time Data Validation using Serverless

## Overview
This tool is designed for system administrators to automate the processing of CSV files uploaded into AWS S3, detect input errors, and route erroneous files to a specified error's bucket to be further reviewed.

## Features
- **Serverless Event Driven:** Triggers real time data validation when a new file is loaded.
- **Re-routing of Erroneous Files** If errors are detected, moves file to an error bucket.

## Prerequisites
- Python 3.x
- `csv` library
- `boto3` library
- CSV file for testing
- AWS account with two S3 buckets
- Boilerplate Lambda function

## Installation
1. **AWS Toolkit**
2. **Sam CLI**
3. **Docker**
4. **Download the boilerplate Lambda function locally**
- Update the code to reflect your S3 error bucket name. Also tailor the product and item lists to reflect your CVS file columns based on your specific use case.

## Usage
The event driven function will automatically validate CSV files when uploaded to an S3 bucket.
Run the script using sam cli:
- `sam local invoke -e event.json` to test locally
- `sam remote invoke arn:aws:lambda:...:YourFunctionName --event-file event.json` to manually invoke after uploading complete function to AWS

After uploaded the completed function to AWS, you must create a trigger for your Lambda function.
1. Click Add Trigger
2. Source: S3
3. Change to "PUT"
4. Save

## Functionality

1. **Python Automation with AWS Resources**
   - The script uses `boto3` to interact with AWS Lambda.

2. **Serverless Event Driven:**
   - If a new file is uploaded to specified S3 bucket data validation will triggered.

3. **Data Validation:**
   - Check each entry of a CSV file line by line to detect invalid entries.

## Customization
You can customize the product_line and item variable lists to reflect your preapproved values for your CVS file columns. Also change the row number that corresponds to placement in your file.

## Note
Ensure that your AWS credentials are properly configured for `boto3` to interact with AWS Lambda. Also, ensure your Lambda Function has the proper permissions to S3. 

## License
This project is licensed under the [MIT License](LICENSE).
