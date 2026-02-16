# AWS-Security-Monitoring-System

AWS Security Monitoring System
👋 Overview

This project demonstrates how to build a real-world cloud security monitoring system using native AWS services. The goal is to detect access to sensitive AWS resources and receive immediate alerts, helping security teams respond to insider threats, credential misuse, or early signs of cloud compromise.

As a Cloud Security Engineer, you will implement monitoring, alerting, and automated mitigation (“Kill-Switch”) workflows to simulate a defensive security pipeline.

🎯 Objectives

Track sensitive AWS resource access (Secrets Manager secrets, S3 buckets, etc.)

Generate real-time security alerts via SNS

Compare multiple alerting approaches (CloudWatch Metric Filters vs EventBridge)

Automate response to potential breaches using Lambda or SSM

Understand continuous monitoring principles and forensic reporting

🧩 Architecture & Core Services

Services Used:

AWS CloudTrail – audit and log all API calls

Amazon CloudWatch – monitor logs and create metric alarms

Amazon SNS – send email notifications for alerts

AWS Secrets Manager – store sensitive secrets (honeytoken)

Amazon S3 – optional logging bucket

AWS CLI – trigger and test events

AWS Lambda / SSM – automated response (“Kill-Switch”)

Conceptual Flow:

Sensitive Access → CloudTrail → CloudWatch / EventBridge → SNS Notification → Lambda/SSM (Optional)

# Project Phases
## Phase 1: Infrastructure & Logging

Create multi-region CloudTrail integrated with CloudWatch Logs

Create a honeytoken secret (Production_Database_Credentials) in Secrets Manager

Enable S3 bucket logging for audit trail

## Phase 2: Detection Logic – Flow 1

CloudWatch Metric Filter for GetSecretValue API calls

Alarm triggers if secret accessed ≥1 time in 1 minute

Send alert via SNS email

## Phase 3: Detection Logic – Flow 2

EventBridge rule triggers on “Sensitive Data Access” events

SNS notification sent to a separate email for comparison

Test retrieval of secret using AWS CLI

## Phase 4: Active Defense (“Kill-Switch”)

Lambda function or SSM Automation strips user permissions automatically

Trigger connected to EventBridge rule from Phase 3

Test using a “Victim” IAM user to verify automatic revocation

## Phase 5: Forensic Reporting

PDF report including:

# Executive summary

Architecture screenshots (CloudWatch / EventBridge)

Evidence from CloudTrail logs (eventTime, userIdentity, sourceIpAddress)

Detection and Kill-Switch screenshots

Security analysis (speed, context, compliance)

Lessons learned

# Tools & Technologies

AWS CloudTrail

Amazon CloudWatch (Logs & Alarms)

Amazon SNS

AWS Secrets Manager

Amazon S3

AWS CLI

AWS Lambda / SSM Automation

# Security Focus

Detect access to sensitive secrets in real-time

Compare alerting flows for speed and contextual information

Automate mitigation to prevent further misuse

Understand compliance requirements and continuous monitoring principles (e.g., NIST)

# Learning Outcomes

By completing this project, users will be able to:

Implement cloud security monitoring pipelines using AWS services

Generate and compare real-time alerts for sensitive resource access

Automate response to breaches with Lambda or SSM

Analyze logs for forensic evidence and audit trails

Apply continuous monitoring concepts for compliance

# Ethical Use

This lab is strictly for educational purposes. Do not use these workflows on production accounts without proper authorization. Security monitoring and response should always be performed ethically.

Full Documenttation can be found here:
https://muhakeem.hashnode.dev/build-a-security-monitoring-system-aws
