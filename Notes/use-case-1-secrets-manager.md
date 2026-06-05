# Use Case 1 - Secrets Manager Access Detection

## Objective

Detect access to AWS Secrets Manager secrets using CloudTrail, CloudWatch Metrics, CloudWatch Alarms and SNS notifications.

## Event Monitored

GetSecretValue

## CloudTrail Event

AWS CloudTrail records GetSecretValue API calls whenever a user, application, EC2 instance, Lambda function or service retrieves a secret from AWS Secrets Manager.

## Detection Logic

Metric Filter:

{ $.eventName = "GetSecretValue" }

Namespace:

SecurityMonitoring

Metric Name:

GetSecretValueCount

Metric Value:

1

## Alert Logic

Condition:

GetSecretValueCount >= 1

Evaluation:

1 out of 1 datapoints

Period:

5 minutes

## Notification

SNS Topic:

SecretsManagerAlerts

Delivery Method:

Email

## Test Performed

A secret was retrieved from AWS Secrets Manager.

## Result

CloudTrail recorded the event.

CloudWatch Metric increased.

CloudWatch Alarm entered ALARM state.

SNS successfully delivered an email notification.