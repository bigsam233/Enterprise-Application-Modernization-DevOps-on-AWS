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

# Phase 1 – Foundation & Governance

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

# Phase 2 – Hybrid Migration & Connectivity

## Overview

The second phase of the project focused on extending the AWS environment beyond cloud-native networking by simulating a traditional on-premises data center and establishing hybrid connectivity between the on-premises environment and AWS.

The primary objectives were:

- Simulate a legacy on-premises environment
- Establish hybrid network connectivity using AWS Transit Gateway
- Validate communication between on-premises and AWS workloads
- Configure AWS Application Migration Service (MGN)
- Replicate and migrate a legacy server into AWS
- Validate successful application migration

This phase demonstrates a common enterprise migration pattern where organizations move workloads from traditional data centers into AWS while maintaining connectivity during the migration process.

---

# Step 1: Create Production EC2 Instance

## Objective

Deploy an application server in the Production VPC to simulate an enterprise workload hosted in AWS.

## Implementation

An EC2 instance was launched within the Production VPC in the primary region (us-east-1).

#### *Production ec2 instance created*

<img width="1698" height="951" alt="01-production-ec2-instance-created" src="https://github.com/user-attachments/assets/f5dea4af-e375-4ba5-ab54-5abcd8ab1513" />


## Outcome

- Production workload deployed
- AWS-hosted application environment established

---

# Step 2: Create Disaster Recovery EC2 Instance

## Objective

Deploy a secondary application server in the Disaster Recovery region.

## Implementation

An EC2 instance was provisioned within the Disaster Recovery VPC in us-west-2.

#### *Disaster recovery ec2 instance created*

<img width="1698" height="955" alt="02-disaster-recovery-ec2-instance-created png" src="https://github.com/user-attachments/assets/618f3bd6-d4fd-4511-8315-a022aacc95ad" />


## Outcome

- Disaster recovery compute environment established
- Cross-region workload architecture implemented

---

# Step 3: Attach SSM Role to EC2 Instance

## Objective

Enable secure instance management without requiring SSH access.

## Implementation

An IAM role with AWS Systems Manager (SSM) permissions was attached to the EC2 instance.

#### *SSM role attached to ec2*

<img width="1707" height="471" alt="03-ssm-role-attached-to-ec2" src="https://github.com/user-attachments/assets/888836d8-62ab-4c7e-beb5-d2029c0c223a" />


## Outcome

- Secure instance administration enabled
- Reduced dependency on SSH access

---

# Step 4: Validate Cross-Region Connectivity

## Objective

Verify communication between the Production and Disaster Recovery environments.

## Implementation

Connectivity tests were performed between EC2 instances hosted in us-east-1 and us-west-2.

#### *cross region connectivity validated*

<img width="1707" height="272" alt="04-cross-region-connectivity-validated" src="https://github.com/user-attachments/assets/95982059-0352-406a-b156-3c80988a2be8" />


## Outcome

- Successful communication confirmed
- VPC Peering configuration validated

---

# Step 5: Create Simulated On-Premises VPC

## Objective

Simulate a traditional enterprise data center environment.

## Implementation

A dedicated VPC was created to represent the organization's on-premises network.

#### *Onprem vpc created*

<img width="1684" height="1057" alt="05-onprem-vpc-created" src="https://github.com/user-attachments/assets/745362bd-474e-43e4-9b8e-94f3a6cd4e0c" />


## Outcome

- Simulated corporate data center established
- Foundation created for hybrid cloud connectivity

---

# Step 6: Create Legacy Application Server

## Objective

Deploy a legacy application server that will later be migrated to AWS.

## Implementation

An EC2 instance was launched within the simulated on-premises VPC to represent a legacy application workload.

#### *Legacy server created*

<img width="1684" height="1057" alt="06-legacy-server-created" src="https://github.com/user-attachments/assets/887ce62c-5103-4384-8144-51991ac7d9fd" />


## Outcome

- Legacy workload deployed
- Migration source environment established

---

# Step 7: Validate Legacy Server

## Objective

Confirm that the simulated on-premises server is functioning correctly before migration.

## Implementation

Application and instance validation tests were performed.

#### *Legacy server validation*

<img width="1695" height="206" alt="07-legacy-server-validation" src="https://github.com/user-attachments/assets/bd63fa62-fe61-4f94-93b5-e3b44e935714" />


## Outcome

- Source workload verified
- Migration readiness confirmed

---

# Step 8: Create On-Premises Transit Gateway Attachment

## Objective

Connect the simulated on-premises network to the AWS Transit Gateway.

## Implementation

A Transit Gateway attachment was created for the on-premises VPC.

#### *Onprem transit gateway attachment created*

<img width="1695" height="1056" alt="08-onprem-transit-gateway-attachment-created" src="https://github.com/user-attachments/assets/fe8f813d-80fc-4a7c-98fa-77ebf3e98933" />


## Outcome

- Hybrid connectivity path established
- On-premises environment integrated into the AWS network architecture

---

# Step 9: Update Route Tables for Transit Gateway

## Objective

Enable traffic routing between AWS and the simulated on-premises network.

## Implementation

Route tables were updated to direct traffic through the Transit Gateway.

#### *Route table updated for transit gateway*

<img width="1695" height="757" alt="09-route-table-updated-for-transit-gateway" src="https://github.com/user-attachments/assets/e3a1d3ad-be8a-4d8d-b69b-05bd4ae5f24c" />


## Outcome

- Hybrid routing configured
- Network traffic successfully directed through Transit Gateway

---

# Step 10: Validate Hybrid Connectivity

## Objective

Verify communication between AWS-hosted workloads and the simulated on-premises environment.

## Implementation

Connectivity tests were performed across the Transit Gateway architecture.

#### *Hybrid connectivity validated*

<img width="1695" height="321" alt="10-hybrid-connectivity-validated" src="https://github.com/user-attachments/assets/20cc6684-9e49-4741-b3a5-c01b3c291cd7" />


## Outcome

- Successful hybrid communication confirmed
- Transit Gateway implementation validated

---

# Step 11: Configure MGN Replication Template

## Objective

Define replication settings for server migration.

## Implementation

AWS Application Migration Service (MGN) replication template settings were configured.

#### *Mgn replication template configured*

<img width="1701" height="956" alt="11-mgn-replication-template-configured" src="https://github.com/user-attachments/assets/eea13b7d-9fe1-4cc6-abe2-a7dd865d22ae" />


## Outcome

- Replication configuration completed
- Migration framework prepared

---

# Step 12: Install AWS MGN Replication Agent

## Objective

Enable continuous replication from the source server.

## Implementation

The AWS MGN replication agent was installed on the legacy server.

#### *MGN agent installed*

<img width="1701" height="956" alt="12-mgn-agent-installed" src="https://github.com/user-attachments/assets/6e53b221-bacf-4d87-9a9e-525b8c97d04a" />


## Outcome

- Source server connected to MGN
- Replication process enabled

---

# Step 13: Download MGN Replication Agent

## Objective

Obtain the migration agent package required for replication.

## Implementation

The AWS MGN replication agent installer was downloaded from the AWS console.

#### *MGN agent installed*

<img width="574" height="399" alt="13-mgn-agent-downloaded" src="https://github.com/user-attachments/assets/c2fc443c-9a13-4cd3-badf-7d995ec05db8" />


## Outcome

- Migration software acquired
- Installation prerequisites completed

---

# Step 14: Register Source Server

## Objective

Register the legacy server with AWS Application Migration Service.

## Implementation

The source server was registered and discovered by MGN.

#### *MGN source server registered*

<img width="1707" height="881" alt="14-mgn-source-server-registered" src="https://github.com/user-attachments/assets/f9aed974-a340-4eb4-ae6d-b0ffd2ef92ac" />


## Outcome

- Source server recognized by AWS
- Replication tracking initiated

---

# Step 15: Configure Launch Settings

## Objective

Define the target infrastructure configuration for migrated workloads.

## Implementation

MGN launch settings were configured to determine how migrated instances would be launched within AWS.

#### *mgn launch settings configured*

<img width="1707" height="881" alt="15-mgn-launch-settings-configured" src="https://github.com/user-attachments/assets/f4d916a0-be02-4019-bf39-07d542c65bcf" />


## Outcome

- Target deployment configuration established
- Migration readiness completed

---

# Step 16: Launch Test Instance

## Objective

Validate migration readiness before cutover.

## Implementation

A test instance was launched from the replicated server data.

#### *MGN test instance launched*

<img width="1707" height="881" alt="16-mgn-test-instance-launched" src="https://github.com/user-attachments/assets/475d1ba0-c392-4d73-b097-394d04d761f0" />


## Outcome

- Migration testing completed
- Replication integrity verified

---

# Step 17: Review Migrated Instance Details

## Objective

Inspect the migrated server deployed within AWS.

## Implementation

The migrated EC2 instance was reviewed to verify configuration, networking, and operational status.

#### *Migrated instance details*

<img width="1707" height="962" alt="17-migrated-instance-details" src="https://github.com/user-attachments/assets/0bff03fc-bfd1-44f1-8d48-59035cdf2998" />


## Outcome

- Successful migration confirmed
- Target workload validated

---

# Step 18: Validate Migrated Application

## Objective

Verify application functionality after migration.

## Implementation

Post-migration application testing was performed against the migrated workload.

#### *Migrated application validated*

<img width="1707" height="222" alt="18-migrated-application-validated" src="https://github.com/user-attachments/assets/da25c26d-3790-48ac-8475-591552abe934" />


## Outcome

- Application functionality confirmed
- Migration success validated
- Legacy workload successfully modernized into AWS

---

# Phase 2 Summary

## Key Deliverables

- Simulated On-Premises Environment
- Hybrid Connectivity Architecture
- Transit Gateway Integration
- Legacy Application Server
- AWS Application Migration Service (MGN) Configuration
- Server Replication and Migration
- Application Validation

## Skills Demonstrated

- Hybrid Cloud Architecture
- Network Routing
- AWS Transit Gateway
- Cross-Region Connectivity
- Migration Planning
- Server Replication
- AWS Application Migration Service
- Workload Validation

## Business Value

This phase demonstrated how enterprises can securely connect existing on-premises environments to AWS and migrate legacy workloads with minimal disruption. By implementing hybrid connectivity and AWS Application Migration Service, the organization established a repeatable migration strategy that supports future cloud adoption initiatives.  

# Phase 3 – Application Tiers

## Overview

The third phase of the project focused on designing and deploying a highly available, scalable, and resilient application architecture capable of supporting enterprise workloads in production.

The primary objectives were:

- Deploy a scalable web application tier
- Implement load balancing across multiple instances
- Configure automatic scaling based on demand
- Validate self-healing capabilities
- Replace the legacy database architecture with Amazon Aurora
- Implement cross-region database replication for disaster recovery

This phase demonstrates how modern enterprises design application platforms that can automatically scale, recover from failures, and maintain business continuity across regions.

---

# Step 1: Create EC2 Launch Template

## Objective

Create a reusable configuration template for application instances that will be managed by Auto Scaling.

## Implementation

An EC2 Launch Template was created containing:

- Amazon Machine Image (AMI)
- Instance type
- Security Group configuration
- User Data scripts
- Application startup configuration

The Launch Template serves as the blueprint used by the Auto Scaling Group whenever a new instance is launched.

#### *Launch template created*

<img width="1576" height="1058" alt="01-launch-template-created" src="https://github.com/user-attachments/assets/bb76ffc8-7e2f-418a-a351-4a9d8c70dd8b" />


## Outcome

- Standardized EC2 deployment configuration established
- Automated instance provisioning enabled
- Foundation prepared for Auto Scaling

---

# Step 2: Create Target Group

## Objective

Create a Target Group to register and manage application instances behind the Application Load Balancer.

## Implementation

A Target Group was created to:

- Receive traffic from the ALB
- Route requests to healthy EC2 instances
- Perform health checks against application endpoints

#### *Target group created*

<img width="1707" height="958" alt="02-target-group-created" src="https://github.com/user-attachments/assets/07becada-3996-496d-af0a-5339f5b175de" />


## Outcome

- Traffic routing layer established
- Health monitoring configured
- Load balancing integration prepared

---

# Step 3: Create Application Load Balancer Security Group

## Objective

Define network security controls for inbound traffic reaching the load balancer.

## Implementation

A dedicated security group was created for the Application Load Balancer.

Configured rules included:

- HTTP access
- Application traffic management
- Controlled communication with backend application servers

#### *Alb security group created*

<img width="1707" height="958" alt="03-alb-security-group-created" src="https://github.com/user-attachments/assets/224d4236-86d0-4523-8e89-4c6b23dfaa43" />


## Outcome

- Secure ingress traffic configuration established
- Load balancer access controls implemented

---

# Step 4: Create Application Load Balancer (ALB)

## Objective

Provide a highly available entry point for application traffic.

## Implementation

An Application Load Balancer was deployed across multiple Availability Zones.

The ALB was configured to:

- Accept client requests
- Distribute traffic across healthy instances
- Perform health checks
- Improve application availability

#### *Application load balancer created*

<img width="1707" height="958" alt="04-application-load-balancer-created" src="https://github.com/user-attachments/assets/722d5aa4-4498-4491-b11d-5dbe9dc01834" />


## Outcome

- Highly available application endpoint established
- Traffic distribution enabled
- Single point of entry created for users

---

# Step 5: Create Auto Scaling Group (ASG)

## Objective

Enable automatic provisioning and replacement of application servers.

## Implementation

An Auto Scaling Group was created using the Launch Template.

The Auto Scaling Group was configured to:

- Maintain desired capacity
- Launch replacement instances when failures occur
- Scale infrastructure based on demand

#### *Auto scaling group created*

<img width="1707" height="958" alt="05-auto-scaling-group-created" src="https://github.com/user-attachments/assets/6c733512-8b88-4a4e-9040-8e2a6db8251d" />


## Outcome

- Elastic compute platform established
- Automated infrastructure management enabled
- Improved application resilience

---

# Step 6: Validate Load Balancing

## Objective

Verify that traffic is successfully routed through the Application Load Balancer.

## Implementation

Application requests were sent through the ALB endpoint and successfully distributed to backend EC2 instances.

#### *Load balancing validated*

<img width="1271" height="332" alt="06-load-balancing-validated" src="https://github.com/user-attachments/assets/e8f64ef6-15e1-4248-97a0-007cc07bf7e2" />


## Outcome

- Load balancing functionality confirmed
- Application accessibility verified
- Traffic routing validated

---

# Step 7: Perform Auto Scaling Failure Test

## Objective

Test the resiliency of the application platform by simulating an instance failure.

## Implementation

One of the EC2 instances managed by the Auto Scaling Group was intentionally terminated.

This simulated:

- Infrastructure failure
- Server outage
- Unexpected instance loss

#### *ASG instance termination test*

<img width="1710" height="500" alt="07-asg-instance-termination-test" src="https://github.com/user-attachments/assets/78c90229-3252-49bb-ab12-f2fe2fd13f07" />


## Outcome

- Failure scenario successfully simulated
- Auto Scaling recovery process triggered

---

# Step 8: Validate Auto Scaling Self-Healing

## Objective

Confirm that the Auto Scaling Group automatically replaces failed instances.

## Implementation

After the instance termination test, the Auto Scaling Group automatically launched a replacement instance using the Launch Template.

#### *ASG self healing validated*

<img width="1710" height="500" alt="08-asg-self-healing-validated" src="https://github.com/user-attachments/assets/331d7bbb-6dfd-45a3-9372-9b1e5fa78acc" />


## Outcome

- Self-healing infrastructure validated
- Desired capacity automatically restored
- High availability objectives achieved

---

# Step 9: Create Aurora Primary Cluster

## Objective

Replace traditional database infrastructure with a managed cloud-native database service.

## Implementation

An Amazon Aurora MySQL cluster was deployed in the primary AWS region (us-east-1).

Aurora was selected because it provides:

- High availability
- Automated backups
- Managed database operations
- Improved scalability

#### *Aurora primary cluster created png*

<img width="1710" height="1018" alt="09-aurora-primary-cluster-created png" src="https://github.com/user-attachments/assets/9df860c0-02bf-460a-ba2e-d19722d6ec57" />


## Outcome

- Cloud-native database platform deployed
- Primary database environment established

---

# Step 10: Create Cross-Region Aurora Reader

## Objective

Implement disaster recovery and cross-region database replication.

## Implementation

An Aurora Read Replica was created in the Disaster Recovery region (us-west-2).

Replication was configured to continuously synchronize data from the primary Aurora cluster.

This architecture forms the basis of an Aurora Global Database deployment.

#### *Aurora cross-region reader created*

<img width="1710" height="563" alt="10-aurora-cross-region-reader-created" src="https://github.com/user-attachments/assets/33310dd8-0ac4-44d1-a1d2-968d24311e84" />


## Outcome

- Cross-region replication established
- Disaster recovery capability implemented
- Reduced Recovery Point Objective (RPO)
- Improved business continuity posture

---

# Phase 3 Summary

## Key Deliverables

- Launch Template
- Target Group
- Application Load Balancer
- Auto Scaling Group
- Automated Instance Recovery
- Aurora Primary Cluster
- Cross-Region Aurora Read Replica


## Skills Demonstrated

- High Availability Architecture
- Elastic Load Balancing
- Auto Scaling
- Infrastructure Resilience
- Self-Healing Systems
- Database Modernization
- Cross-Region Replication
- Disaster Recovery Design

## Business Value

This phase transformed the application environment into a highly available and resilient platform capable of automatically recovering from failures and scaling to meet demand. By implementing Application Load Balancing, Auto Scaling, and Aurora Global Database, the organization significantly improved application reliability, fault tolerance, and disaster recovery readiness.  


