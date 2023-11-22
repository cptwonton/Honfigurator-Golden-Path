---
layout: default
---

# EC2 Instances

In this section, we will walk through the process of setting up EC2 instances on Amazon Web Services (AWS) for hosting your Project Kongor Heroes of Newerth server.

## 1. Launching EC2 Instances

### 1.1. Sign in to AWS Console

Begin by logging in to the [AWS Management Console](https://aws.amazon.com/) with your AWS account credentials.

### 1.2. Select a Region

Choose the AWS region where you want to launch your EC2 instances. Consider factors such as latency, data residency, and cost. Click the region selector in the top-right corner of the AWS Management Console and choose your preferred region.

For example, if you are located in South America, you may want to select "South America (Sao Paulo)".

### 1.3. Navigate to EC2 Dashboard

Go to the EC2 Dashboard by clicking on "Services" in the top left corner and selecting "EC2" under the "Compute" section.

### 1.4. Launch Instance

Click on the "Instances" in the left navigation pane and then click the "Launch Instances" button.

### 1.5. Choose an Amazon Machine Image (AMI)

- Under "Quick Start", Select Ubuntu. This should populate the "AMI" dropdown with Ubuntu Server 22.04 LTS (HVM), SSD Volune Type AMI
- 

As of this writing, Ubuntu Linux is the only option confirmed tested and working on AWS. If you are a power-user and are feeling adventurous, feel free to try out another option. Otherwise, stick with Ubuntu Linux.

### 1.6. Choose an Instance Type - BE CAREFUL

This is a very important step as it directly affects

- how much lag players will experience
- cost of your server
- how many games your server can simultaneously handle

While there are many categories of EC2 server, only two make sense for hosting HoN.

1. General Purpose (t2, t3)
   1. these EC2 instances are general purpose, and cost effective
   2. the players may rarely experience server side lag, but it is hardly noticable
2. Compute Optimized (c5, c6, c7)
   1. these EC2 instances are compute optimized. While they are cost effective for what they are, they are more expensive than General Purpose

When comparing your options, take note of the Linux price-per-hour as that is the one that applies when you select Ubuntu. Windows is generally much more expensive.
When you select a server with 4 or fewer vCPUs, 1 will be dedicated to the OS, leaving #vCPU-1 avialable for running HoN servers.

- For example, if you pick an option with 4vCPUs, 1 will be dedicated to the OS, leaving 3 available for running HoN servers. You can expect this option to be able to handle 3 games simultaneously without issue.

When you select a server with more than 4 vCPUs, 2 will be dedicated to the OS, leaving #vCPU-2 available for running HoN servers.

- For example, if you pick an option with 8vCPUs, 2 will be dedicated to the OS, leaving 6 available for running HoN servers. You can expect this option to be able to handle 6 games simultaneously without issue.

As vCPUs are expensive and RAM is cheap, AWS does not give you high vCPU + low RAM options.

Pick an instance type that suits your performance needs and budget. It is recommended to start with something small, like a t3.small (2 vCPU + 2GB ram)
You can easily switch out the instance later.

### 1.7. Configure Instance Details

- Key Pair (login): you do this once per region.
  - If you have done this step before, select the key pair you already created. Otherwise, proceed. 
  - Click "Create new key pair"
  - Key pair name: kongor
  - Key pair type: RSA
  - Private key file format: .pem
  - "Create Key Pair"
  - Under the Key pair name dropdown, select kongor.pem
- Network Settings -> Keep defaults, ensuring you allow ssh from anywhere. You can restrict this later if you wish.

### 1.8. Add Storage

Change the storage from its default of 8GiB to 30GiB. gp2 is fine.

### 1.9. Add Tags (Optional)

Assign tags to your instances for better organization and identification.

### 1.11. Review and Launch

Double-check your configuration settings and click "Launch."

## 2. Connecting to Your EC2 Instance

### 2.1. Access Instances

Once your instances are launched, go back to the EC2 Dashboard and navigate to "Instances."

### 2.2. Connect

Select your instance, click "Connect," and follow the provided instructions to connect to your EC2 instance.
