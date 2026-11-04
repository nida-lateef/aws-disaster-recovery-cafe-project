# AWS Multi-Region Disaster Recovery Plan – Café Business

## Project Overview

This project presents a proposed AWS Cloud Disaster Recovery (DR) architecture for a café business that relies on cloud-based systems for point-of-sale (POS), customer records, inventory management and online ordering.

The design uses a **Warm Standby disaster recovery strategy** across two AWS regions to support business continuity, data protection and recovery during major service disruptions.

**Project type:** TAFE NSW Cloud Architecture project  
**Platform:** Amazon Web Services (AWS)  
**Architecture:** Multi-region Warm Standby  
**Primary Region:** Sydney – `ap-southeast-2`  
**Secondary Region:** Melbourne – `ap-southeast-4`

> **Project status:** Architecture design and documentation completed as part of TAFE NSW studies. This repository documents the proposed solution; it does not claim that the complete multi-region environment was deployed.

## Business Scenario

The café depends on several technology systems:

- Point-of-sale (POS) system
- Customer database
- Inventory management
- Online ordering platform

An outage affecting these systems could interrupt business operations, affect customer experience and result in financial losses.

The project identifies recovery requirements and proposes an AWS architecture to minimise downtime and data loss.

## Disaster Recovery Objectives

The project defines the following Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO):

| System | RTO | RPO |
|---|---:|---:|
| POS System | 2 hours | 1 hour |
| Customer Database | 1 hour | 15 minutes |
| Inventory System | 4 hours | 1 hour |
| Online Ordering System | 2 hours | 30 minutes |

- **RTO:** Maximum targeted time to restore a system.
- **RPO:** Maximum targeted period of data loss measured in time.

## Proposed AWS Architecture

The design uses Sydney as the primary AWS region and Melbourne as the secondary disaster recovery region.

### Primary Region – Sydney

The primary environment is designed to host the live workloads.

Proposed AWS services:

- Amazon EC2 and AWS Lambda – application hosting
- Amazon RDS Multi-AZ – database availability
- Amazon S3 – storage and backup
- Amazon CloudWatch – monitoring and alerts
- AWS IAM – identity and access management
- AWS CloudTrail – activity logging
- Amazon Route 53 – DNS routing and failover

### Secondary Region – Melbourne

The secondary region is designed to maintain a Warm Standby environment.

Proposed components:

- Amazon S3 Cross-Region Replication
- Amazon RDS read replica or snapshot-based recovery
- Preconfigured EC2 and Lambda components
- Amazon Route 53 failover routing
- AWS CloudFormation templates for infrastructure recovery

## Backup and Security Strategy

The proposed plan includes:

- Daily automated cloud backups
- Incremental database backups
- Cross-region backup replication
- 90-day backup retention
- Long-term archival using Amazon S3 Glacier
- Encryption of data in transit and at rest
- IAM role-based access controls
- Multi-factor authentication (MFA)
- Monitoring through Amazon CloudWatch

## Risk Assessment

Three major disaster scenarios were considered:

1. Cyberattack or malware
2. AWS regional or data centre outage
3. Application or software failure

The plan includes recovery procedures for each scenario, including system isolation, database restoration, application recovery, DNS failover and validation.

## Disaster Recovery Process

The proposed recovery workflow is:

1. Detect and assess the incident.
2. Identify affected systems and determine the recovery priority.
3. Activate the disaster recovery environment if required.
4. Restore or promote database resources.
5. Redirect traffic to the secondary region.
6. Validate applications and business operations.
7. Synchronise data and plan failback when the primary region is restored.

## Skills Demonstrated

- AWS cloud architecture planning
- Multi-region disaster recovery design
- Recovery Time Objective (RTO) and Recovery Point Objective (RPO)
- Backup and recovery strategies
- AWS storage and database services
- Identity and access management concepts
- Cloud security and monitoring
- Risk assessment and business continuity documentation

## Learning Outcomes

This project helped develop an understanding of how AWS services can be combined to design a resilient cloud environment, protect business-critical information and support recovery from technology disruptions.

## Disclaimer

This is an educational project completed as part of TAFE NSW Cloud Architecture studies. The architecture and recovery procedures represent a proposed design for a simulated café business. Service configurations and recovery performance have not been independently validated through a complete production deployment.
