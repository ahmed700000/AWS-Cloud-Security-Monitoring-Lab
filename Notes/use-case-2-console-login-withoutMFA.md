# Use Case 2 - Console Login Without MFA Detection

## Objective

Detect successful AWS Console logins performed without Multi-Factor Authentication (MFA).

## Event Monitored

ConsoleLogin

## CloudTrail Event

AWS CloudTrail records successful console authentication events through signin.amazonaws.com.

## Detection Logic

Metric Filter:

{ ($.eventName = "ConsoleLogin") && ($.responseElements.ConsoleLogin = "Success") && ($.additionalEventData.MFAUsed = "No") }

Namespace:

SecurityMonitoring

Metric Name:

ConsoleLoginWithoutMFA

Metric Value:

1

## Alert Logic

Condition:

ConsoleLoginWithoutMFA >= 1

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

Logged into AWS Console using IAM user Ahmed-admin without MFA enabled.

## Result

CloudTrail recorded the login event.

CloudWatch Metric increased.

CloudWatch Alarm entered ALARM state.

SNS successfully delivered an email notification.