📊 Cloud Monitoring & Log Analysis using AWS CloudWatch
📌 Project Overview
This project demonstrates Cloud Monitoring and Log Analysis using AWS CloudWatch, assuming the Internee.pk backend is hosted on AWS Lambda. The goal is to monitor system performance, analyze logs, and configure alerts for failures.

🎯 Objectives
Monitor backend performance metrics
Analyze execution logs
Detect system failures
Configure alerts using SNS

🛠️ Services Used
AWS Lambda
AWS CloudWatch
Amazon SNS
🏗️ Architecture
User Requests → Internee.pk Backend (AWS Lambda)
                     ↓
               AWS CloudWatch
          (Metrics + Logs + Alarms)
                     ↓
               SNS Email Alerts

⚙️ Implementation Steps
1️⃣ Create AWS Lambda Function
Created a Lambda function named internee-pk-backend
Runtime: Python 3.12
Used sample backend logic to simulate request handling

import time
def lambda_handler(event, context):
    time.sleep(1)
    print("Internee.pk backend request processed")
    return {
        'statusCode': 200,
        'body': 'Response from Internee.pk backend.'
    }

2️⃣ Generate Logs & Metrics
Lambda function was executed using test events

CloudWatch automatically generated logs and metrics
3️⃣ Log Analysis (CloudWatch Logs)
Log Group: /aws/lambda/internee-pk-backend


Logs captured:
Execution details
Error messages
Request IDs
4️⃣ Performance Monitoring (CloudWatch Metrics)
Monitored key metrics:
Duration → Response Time
Invocations
Errors
Throttles

5️⃣ Failure Simulation & Alerts
To simulate a failure, an exception was triggered:
def lambda_handler(event, context):
    raise Exception("Simulated backend failure")

Error logs appeared in CloudWatch Logs
Error metric increased
CloudWatch Alarm was triggered
SNS email notification was sent

🚨 CloudWatch Alarms
Alarm Condition: Errors ≥ 1
Notification Service: Amazon SNS
Alerts sent via email upon failure detection

📈 Why Cloud Monitoring is Important
Detects performance issues early
Prevents downtime
Improves system reliability
Enables proactive system management
✅ Conclusion
This project demonstrates how AWS CloudWatch can be used to monitor serverless applications effectively. It highlights real-world monitoring practices used in cloud-based architectures.

