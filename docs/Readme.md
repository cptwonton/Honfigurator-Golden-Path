layout: page
title: "Readme.md"
permalink: /

# Server Setup on AWS

## Introduction

Welcome to the enchanting journey of setting up your very own Project Kongor Heroes of Newerth server, adorned with the magical touch of HonFigurator, on the illustrious realm of Amazon Web Services. This guide beckons to you if:
- You aspire to be a steadfast ally of Project Kongor.
- Your heart yearns to bring game servers closer to your realm or a cherished region of the world.
- You are prepared to bestow as little as ~$20 USD per month to cover the AWS costs of orchestrating this wondrous server symphony.

Embark on this adventure with caution, for while AWS costs carry no commitment, the dance of provisioning holds a dual-edged charm. With careful steps, your bill can remain as elusive as a wisp in the night, but missteps may summon a towering AWS bill. Fear not, for this guide is your trusted companion, pointing out the treacherous turns and whispering, "BE CAREFUL" as you traverse the ethereal landscapes of cloud hosting. May your journey be both whimsical and prosperous! 🚀🔮

## Acronyms:
- Project Kongor (PK)
- HonFigurator (HF)
- Heroes of Newerth (HoN)
- Amazon Web Services (AWS)
  - Elastic Compute Cloud (EC2)
  - Security Group (SG)

## Prerequisites

Before you begin, ensure you have the following:
- [AWS account](/docs/aws-account.md)
- [PK account](/docs/project-kongor-account.md)
  - Note: You cannot use the account you play on while also using that same account to run this server. 
  - You must use a new email that has not been used before to create a PK account

## Step 1: Set Up AWS Resources
### 1.1 EC2 Instances
- [Launching EC2 instances for game servers](/docs/ec2-instances.md)
- [Configuring security groups](/docs/security-groups.md)

## Step 2: Configure Server Environment
### 2.1 Operating System Setup
- Choosing a suitable OS (e.g., Amazon Linux)
- Installing necessary dependencies

### 2.2 Game Server Installation
- Downloading and installing Heroes of Newerth server files
- Configuring server settings and options

### 2.3 Automating Deployments
- Scripting deployment processes for ease of use
- Version control and rollback strategies

## Step 3: Monitoring and Maintenance
### 3.1 AWS CloudWatch
- Setting up monitoring and alerts for instances
- Monitoring resource utilization

### 3.2 Backups and Recovery
- Implementing regular backups for game data
- Strategies for server recovery

## Step 4: Community Management
### 4.1 Setting Up Communication Channels
- Establishing communication platforms for the community (Discord, forums, etc.)

### 4.2 Moderation and Support
- Guidelines for moderation and support
- Handling user issues and escalations

## Conclusion
Summarize key points and provide encouragement for community contributions and improvements.

## Additional Resources
- Links to AWS documentation
- Links to relevant Project Kongor resources
- References for further learning


```markdown
![AWS Console](/docs/images/aws_console.png)