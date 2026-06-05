# AWS Cloud Security Monitoring Lab

## Overview

This project demonstrates how to build a cloud security monitoring solution using AWS native security services.

The lab uses AWS CloudTrail, CloudWatch Logs, Metric Filters, CloudWatch Alarms, and SNS notifications to detect and alert on security-relevant events in near real time.

The objective is to simulate common cloud security monitoring use cases and generate automated alerts whenever suspicious or sensitive activities occur within the AWS environment.

---

## Architecture

```text
IAM User / AWS Service
          |
          v
    AWS CloudTrail
          |
          v
   CloudWatch Logs
          |
          v
     Metric Filter
          |
          v
   CloudWatch Metric
          |
          v
   CloudWatch Alarm
          |
          v
       SNS Topic
          |
          v
   Email Notification
```

---

## AWS Services Used

- AWS CloudTrail
- Amazon CloudWatch Logs
- CloudWatch Metric Filters
- CloudWatch Alarms
- Amazon SNS
- AWS IAM
- Amazon EC2
- AWS Secrets Manager

---

## Implemented Security Use Cases

### Use Case 1 – Secrets Manager Access Detection

**Objective**

Detect whenever a secret is retrieved from AWS Secrets Manager.

**CloudTrail Event**

```text
GetSecretValue
```

**Metric Filter**

```json
{ $.eventName = "GetSecretValue" }
```

**Alert Action**

Generate a CloudWatch Alarm and send an email notification through Amazon SNS.

---

### Use Case 2 – Console Login Without MFA Detection

**Objective**

Detect successful AWS console logins performed without Multi-Factor Authentication (MFA).

**CloudTrail Event**

```text
ConsoleLogin
```

**Metric Filter**

```json
{
 ($.eventName = "ConsoleLogin")
 &&
 ($.responseElements.ConsoleLogin = "Success")
 &&
 ($.additionalEventData.MFAUsed = "No")
}
```

**Alert Action**

Generate a CloudWatch Alarm and send an SNS email notification.

---

### Use Case 3 – EC2 Instance Creation Detection

**Objective**

Detect whenever a new EC2 instance is launched.

**CloudTrail Event**

```text
RunInstances
```

**Metric Filter**

```json
{ $.eventName = "RunInstances" }
```

**Alert Action**

Generate a CloudWatch Alarm and send an SNS email notification.

---

### Use Case 4 – Security Group Modification Detection

**Objective**

Detect modifications to AWS Security Groups.

**CloudTrail Event**

```text
ModifySecurityGroupRules
```

**Metric Filter**

```json
{ $.eventName = "ModifySecurityGroupRules" }
```

**Alert Action**

Generate a CloudWatch Alarm and send an SNS email notification.

---

## Project Screenshots

### Use Case 1 - Secrets Manager Access Detection

- Secret Creation
- Secret Retrieval
- CloudTrail Event
- Metric Filter
- Alarm Trigger
- Email Notification

### Use Case 2 - Console Login Without MFA

- User Without MFA
- CloudTrail Login Event
- Metric Filter
- Alarm Trigger
- Email Notification

### Use Case 3 - EC2 Instance Creation Detection

- CloudTrail RunInstances Event
- Metric Filter
- Alarm Trigger
- Email Notification

### Use Case 4 - Security Group Modification Detection

- CloudTrail Security Group Modification Event
- Metric Filter
- Alarm Trigger
- Email Notification

---

## Skills Demonstrated

- AWS Cloud Security Monitoring
- Detection Engineering
- AWS CloudTrail Analysis
- CloudWatch Metric Filters
- CloudWatch Alarm Configuration
- SNS Alerting
- IAM Security Monitoring
- EC2 Activity Monitoring
- Security Event Detection
- Security Operations Fundamentals

---

## Key Learning Outcomes

Through this project, I gained hands-on experience with:

- Monitoring AWS activity using CloudTrail
- Creating custom security detections
- Converting CloudTrail events into CloudWatch metrics
- Building automated alerting workflows
- Detecting sensitive cloud activities
- Investigating AWS security events
- Designing cloud security monitoring use cases

---

## Author

Ahmed Alsharabi

Bachelor of Computer Science (Network Technology & Cybersecurity)

Cloud Security & Security Operations Enthusiast