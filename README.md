# Enterprise Application Modernization DevOps on AWS

Enterprise application modernization and DevOps project on AWS featuring governance, hybrid migration, Aurora Global Database, Kubernetes (Amazon EKS), CI/CD automation, disaster recovery, and compliance monitoring.

AWS
Amazon EKS
Aurora Global Database
AWS Organizations
Transit Gateway
GitHub Actions
AWS Config

---

# Project Overview

This project demonstrates the end-to-end modernization of a legacy enterprise application environment on Amazon Web Services (AWS). The solution was designed to simulate a real-world cloud transformation initiative involving governance, hybrid cloud connectivity, application migration, high availability, disaster recovery, containerization, CI/CD automation, and compliance monitoring.

The project follows a phased implementation approach that begins with establishing a secure and governed AWS foundation, extends into hybrid migration from a simulated on-premises environment, evolves into a highly available application architecture using Auto Scaling and Aurora Global Database, and culminates in application modernization through Amazon EKS and automated deployment pipelines.

By combining traditional infrastructure with cloud-native technologies, the project demonstrates how organizations can migrate, modernize, secure, and operate enterprise workloads at scale on AWS.

---

# Business Scenario

A fictional enterprise is undertaking a large-scale digital transformation initiative to modernize its aging application infrastructure and improve operational resilience.

The organization currently operates a legacy application hosted in an on-premises environment and faces several business challenges:

- Limited scalability of existing infrastructure
- Lack of centralized governance and access management
- Absence of automated deployment processes
- Single-region architecture with no disaster recovery strategy
- Manual operational processes that increase risk and deployment time
- Limited visibility into security and compliance posture

To address these challenges, the organization has decided to migrate and modernize its workloads on AWS while implementing enterprise-grade governance, hybrid connectivity, disaster recovery, DevOps automation, and continuous compliance monitoring.

The target solution must provide:

- Multi-account governance and centralized identity management
- Hybrid connectivity between on-premises and AWS environments
- Highly available application infrastructure
- Cross-region disaster recovery capabilities
- Kubernetes-based application modernization
- Automated CI/CD pipelines
- Continuous security and compliance monitoring

---

# Solution Architecture

The solution is implemented across four major phases:

## Phase 1 – Foundation & Governance

Establishes the enterprise landing zone by implementing:

- AWS Organizations
- Organizational Units (OUs)
- Service Control Policies (SCPs)
- AWS IAM Identity Center
- Production VPC (us-east-1)
- Disaster Recovery VPC (us-west-2)
- VPC Peering
- Transit Gateway

This phase provides centralized governance, network segmentation, and secure access management.

---

## Phase 2 – Hybrid Migration & Connectivity

Simulates a traditional on-premises environment and establishes hybrid connectivity with AWS.

Key components include:

- Simulated On-Premises Network
- Legacy Application Server
- AWS Transit Gateway
- AWS Application Migration Service (MGN)

This phase demonstrates workload migration and hybrid cloud architecture patterns commonly used by enterprises.

---

## Phase 3 – Application Tiers

Builds a highly available and resilient application platform.

Key components include:

- Application Load Balancer (ALB)
- Auto Scaling Group (ASG)
- Amazon EC2 Application Servers
- Amazon Aurora MySQL
- Aurora Global Database
- Cross-Region Read Replica (us-west-2)

This phase delivers application scalability, fault tolerance, and disaster recovery capabilities.

---

## Phase 4 – Modernization & DevOps

Modernizes application components and automates software delivery.

Key components include:

- Docker
- Amazon Elastic Container Registry (ECR)
- Amazon Elastic Kubernetes Service (EKS)
- GitHub Actions
- AWS CodeArtifact
- AWS CodePipeline
- AWS Config

This phase introduces cloud-native application deployment, CI/CD automation, and compliance monitoring.

---

## Architecture Diagrams

### Enterprise Transformation Roadmap

<img width="1692" height="929" alt="enterprise-transformation-roadmap png" src="https://github.com/user-attachments/assets/60999b8f-bcc5-4bfb-8e6b-59b1cfc229a0" />

### Final Technical Architecture

<img width="1536" height="1024" alt="final-technical-architecture png" src="https://github.com/user-attachments/assets/0a8efb60-4e07-4379-aa2d-0abe6b00811a" />


---

# Technology Stack

| Category | AWS Services / Technologies |
|-----------|-----------|
| Governance & Identity | AWS Organizations, Organizational Units (OUs), Service Control Policies (SCPs), AWS IAM Identity Center |
| Networking | Amazon VPC, VPC Peering, AWS Transit Gateway, Route Tables, Security Groups |
| Hybrid Connectivity | Simulated On-Premises Network, AWS Transit Gateway |
| Migration | AWS Application Migration Service (MGN) |
| Compute | Amazon EC2, Auto Scaling Group (ASG) |
| Load Balancing | Application Load Balancer (ALB) |
| Database | Amazon Aurora MySQL, Aurora Global Database |
| Containers | Docker, Amazon Elastic Container Registry (ECR), Amazon Elastic Kubernetes Service (EKS) |
| CI/CD & DevOps | GitHub Actions, AWS CodeArtifact, AWS CodePipeline |
| Security & Compliance | AWS Config, AWS Config Rules |
| Monitoring & Logging | Amazon CloudWatch |
| Disaster Recovery | Aurora Global Database Cross-Region Replication, Disaster Recovery VPC |  

---
#  Implementation Phases  

## Phase 1 – Foundation & Governance

## Overview

The first phase of the project focused on establishing a secure, scalable, and governed AWS foundation capable of supporting enterprise workloads across multiple regions.

The primary objectives were:

- Build a production network in the primary AWS region (us-east-1)
- Build a Disaster Recovery (DR) network in a secondary AWS region (us-west-2)
- Establish secure connectivity between both environments
- Implement centralized governance using AWS Organizations
- Enforce compliance controls using Service Control Policies (SCPs)
- Prepare the environment for hybrid connectivity and application migration in later phases

---

## Step 1: Create the Primary Production VPC

### Objective

Provision a dedicated Virtual Private Cloud (VPC) in the primary AWS region (us-east-1) to host production workloads.

### Implementation

A production VPC was created in the us-east-1 region to provide network isolation for enterprise applications and services.

#### *Production VPC created*

<img width="1700" height="1039" alt="01-production-vpc-created" src="https://github.com/user-attachments/assets/66e056c5-92b2-4839-b02c-7945e537a976" />


### Outcome

- Production network established
- Isolated cloud environment created
- Foundation prepared for application deployment

---

## Step 2: Create the Disaster Recovery VPC

### Objective

Provision a secondary VPC in the disaster recovery region (us-west-2).

### Implementation

A dedicated Disaster Recovery VPC was created to support business continuity and future disaster recovery scenarios.

#### *Disaster recovery VPC created*

<img width="1700" height="1039" alt="02-disaster-recovery-vpc-created" src="https://github.com/user-attachments/assets/3158889f-16dd-4b72-804e-e4b045793927" />


### Outcome

- Secondary environment established
- Cross-region architecture initiated
- Disaster recovery foundation created

---

## Step 3: Create VPC Peering Connection

### Objective

Enable private communication between the Production and Disaster Recovery VPCs.

### Implementation

A VPC Peering request was initiated between the Production VPC in us-east-1 and the Disaster Recovery VPC in us-west-2.

#### *VPC peering request created*

<img width="1700" height="1039" alt="03-vpc-peering-request-created" src="https://github.com/user-attachments/assets/d5061230-b83c-4cba-8b81-edcf59ba39cd" />


### Outcome

- Peering request successfully created
- Network connectivity process initiated

---

## Step 4: Establish VPC Peering

### Objective

Activate the VPC Peering connection.

### Implementation

The peering request was accepted, creating a private network connection between the two VPCs.

#### *VPC peering established*

<img width="1700" height="401" alt="04-vpc-peering-established" src="https://github.com/user-attachments/assets/0b40a5a3-e1e1-44e2-8ec4-0bb04db195c3" />


### Outcome

- Cross-region VPC connectivity established
- Private routing path enabled

---

## Step 5: Update Route Tables for VPC Peering

### Objective

Enable traffic routing between both VPCs.

### Implementation

Private route tables were updated to direct traffic through the VPC Peering connection.

### *Route table updated for VPC peering*

<img width="1700" height="731" alt="05-route-table-updated-for-vpc-peering" src="https://github.com/user-attachments/assets/c5c97c17-6085-439b-9c8d-eeb2a8d9be2a" />


### Outcome

- Routing configured successfully
- Production and DR VPCs can exchange traffic

---

## Step 6: Create Application Security Group in us-east-1

### Objective

Define security boundaries for production application resources.

### Implementation

An application security group was created within the Production VPC.

#### *App security group created us-east-1*

<img width="1698" height="951" alt="06-app-security-group-created-us-east-1" src="https://github.com/user-attachments/assets/87d047d3-00ea-44a5-80cb-f8da0763968a" />


### Outcome

- Network access controls established
- Application traffic secured

---

## Step 7: Create Application Security Group in us-west-2

### Objective

Mirror security controls in the Disaster Recovery region.

### Implementation

A corresponding application security group was created in the DR VPC.

#### *App security group created us-west-2*

<img width="1698" height="955" alt="07-app-security-group-created-us-west-2" src="https://github.com/user-attachments/assets/60483fa0-a6e0-4461-9ad8-2bb5f493fa54" />


### Outcome

- Consistent security posture maintained across regions

---

## Step 8: Create AWS Transit Gateway

### Objective

Prepare for scalable network connectivity and future hybrid cloud integration.

### Implementation

An AWS Transit Gateway was created to serve as the central network hub.

#### *Transit-gateway-created*

<img width="1707" height="1061" alt="08-transit-gateway-created" src="https://github.com/user-attachments/assets/9f667a74-89ac-4c35-9a5d-b2e8bd1eeb99" />


### Outcome

- Centralized network routing architecture established
- Foundation prepared for hybrid networking

---

## Step 9: Create Transit Gateway Attachments

### Objective

Connect VPCs to the Transit Gateway.

### Implementation

Transit Gateway attachments were created to integrate the VPCs into the centralized network architecture.

#### *Transit gateway attachment created*

<img width="1707" height="1061" alt="09-transit-gateway-attachment-created" src="https://github.com/user-attachments/assets/3cbccb90-c74c-40bd-843c-222f0a92ad75" />


### Outcome

- VPC connectivity simplified
- Scalable routing architecture implemented

---

## Step 10: Create Organizational Units and Member Account

### Objective

Implement enterprise governance using AWS Organizations.

### Implementation

AWS Organizations was configured with Organizational Units (OUs) and member accounts to support centralized account management.

#### *Organizational units and member account created*

<img width="1709" height="1065" alt="10-organizational-units-and-member-account-created" src="https://github.com/user-attachments/assets/be70afe0-5ba8-4433-89d5-3386f304591f" />


### Outcome

- Multi-account structure established
- Governance boundaries defined

---

## Step 11: Create Service Control Policy (SCP)

### Objective

Enforce organization-wide compliance controls.

### Implementation

A Service Control Policy was created to restrict actions that violate organizational standards.

#### *Service control policy created*

<img width="1684" height="1057" alt="11-service-control-policy-created" src="https://github.com/user-attachments/assets/ba777400-7a6e-43e0-8861-41fcba31e932" />


### Outcome

- Preventive security controls implemented
- Compliance guardrails established

---

## Step 12: Attach SCP to Development OU

### Objective

Apply governance controls to organizational resources.

### Implementation

The Service Control Policy was attached to the Development Organizational Unit.

#### *Scp attached to development ou*

<img width="1684" height="1057" alt="12-scp-attached-to-development-ou" src="https://github.com/user-attachments/assets/aa3373d7-c5f6-4ec1-9c0a-d53b1c0c91a7" />


### Outcome

- Governance policy enforcement activated
- Development accounts protected from non-compliant actions

---

## Phase 1 Summary

### Key Deliverables

- Production VPC (us-east-1)
- Disaster Recovery VPC (us-west-2)
- Cross-region VPC Peering
- Transit Gateway Architecture
- Application Security Groups
- AWS Organizations
- Organizational Units
- Service Control Policies (SCPs)

### Skills Demonstrated

- AWS Networking
- Multi-Region Architecture
- Network Routing
- VPC Peering
- AWS Transit Gateway
- AWS Organizations
- Governance & Compliance
- Security Architecture

### Business Value

This phase established the enterprise landing zone and governance foundation required to support secure application migration, disaster recovery, modernization, and DevOps automation in subsequent phases.  

## Phase 2 – Foundation & Governance
