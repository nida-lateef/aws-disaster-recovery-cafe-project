# AWS Disaster Recovery Architecture

The following diagram illustrates the proposed multi-region Warm Standby architecture for the café business.

```mermaid
flowchart TB
    Users["Café staff and customers"]
    DNS["Amazon Route 53"]

    subgraph Sydney["Primary Region - Sydney"]
        APP["EC2 / Lambda"]
        DB["RDS Multi-AZ"]
        S3["Amazon S3"]
        CW["CloudWatch"]
    end

    subgraph Melbourne["Secondary Region - Melbourne"]
        APP2["Warm Standby EC2 / Lambda"]
        DB2["RDS Replica / Snapshot"]
        S32["S3 Cross-Region Replication"]
    end

    Users --> DNS
    DNS --> APP
    APP --> DB
    APP --> S3
    S3 -.-> S32
    DB -.-> DB2
    CW -.-> DNS
    DNS -. Failover .-> APP2

# AWS Café Disaster Recovery Architecture

## Project Overview

This project was completed as part of my TAFE NSW Cloud Architecture studies.

The project focuses on designing a proposed AWS disaster recovery solution for a café business that depends on point-of-sale systems, customer records, inventory management and online ordering.

The objective was to improve business continuity, reduce downtime and protect business data during unexpected disruptions.

## Proposed Architecture

The solution uses a multi-region Warm Standby approach:

- **Primary Region:** Sydney (ap-southeast-2)
- **Secondary Region:** Melbourne (ap-southeast-4)

The proposed architecture includes backup, replication, monitoring and failover strategies to support business recovery.

## Architecture Diagram

![AWS Disaster Recovery Architecture](architecture/disaster-recovery-architecture.mmd)

For the full architecture documentation, see [Architecture Details](architecture/architecture.md).

## AWS Services Considered

- Amazon EC2
- Amazon RDS Multi-AZ
- Amazon S3
- Amazon Route 53
- Amazon CloudWatch
- AWS IAM
- AWS CloudFormation
- AWS Lambda

## Recovery Objectives

| Business System | RTO | RPO |
|---|---:|---:|
| Point of Sale | 2 hours | 1 hour |
| Customer Database | 1 hour | 15 minutes |
| Inventory Management | 4 hours | 1 hour |
| Online Ordering | 2 hours | 30 minutes |

## Disaster Scenarios

- AWS regional outage
- Cyberattack or malware
- Application failure
- Data loss or corruption

## Skills Demonstrated

- AWS cloud architecture concepts
- Disaster recovery planning
- High availability and business continuity
- Backup and recovery strategies
- Risk assessment
- Technical documentation

## Project Documentation

- [Project Details](project-details.md)
- [AWS Architecture](architecture/architecture.md)
- [Mermaid Architecture Source](architecture/disaster-recovery-architecture.mmd)

## Project Status

This is an educational architecture and disaster recovery planning project. The multi-region architecture represents a proposed design and is not a claim of a fully deployed production environment.
