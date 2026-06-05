# Use Case 3 - EC2 Instance Creation Detection

## Objective

Detect creation of new EC2 instances within the AWS environment.

## Event Monitored

RunInstances

## CloudTrail Event

AWS CloudTrail records RunInstances API calls whenever a new EC2 instance is launched.

## Detection Logic

Metric Filter:

{ $.eventName = "RunInstances" }

Namespace:

SecurityMonitoring

Metric Name:

EC2InstanceCreationCount

Metric Value:

1

## Alert Logic

Condition:

EC2InstanceCreationCount >= 1

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

Launched a new Amazon Linux EC2 instance.

## Result

CloudTrail recorded the RunInstances event.

CloudWatch Metric increased.

CloudWatch Alarm entered ALARM state.

SNS successfully delivered an email notification.