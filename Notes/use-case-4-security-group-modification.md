# Use Case 4 - Security Group Modification Detection

## Objective

Detect modifications made to AWS Security Group rules.

## Event Monitored

ModifySecurityGroupRules

## CloudTrail Event

AWS CloudTrail records modifications to inbound and outbound Security Group rules.

## Detection Logic

Metric Filter:

{ $.eventName = "ModifySecurityGroupRules" }

Namespace:

SecurityMonitoring

Metric Name:

SecurityGroupModificationCount

Metric Value:

1

## Alert Logic

Condition:

SecurityGroupModificationCount >= 1

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

Modified Security Group inbound rules from the AWS Console.

## Result

CloudTrail recorded the modification event.

CloudWatch Metric increased.

CloudWatch Alarm entered ALARM state.

SNS successfully delivered an email notification.