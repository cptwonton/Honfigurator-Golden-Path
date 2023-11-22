---
layout: default
---

# Server Setup on AWS

## Introduction

Welcome to the enchanting journey of setting up your very own Project Kongor Heroes of Newerth server, adorned with the magical touch of HonFigurator, on the illustrious realm of Amazon Web Services. This guide beckons to you if:

- You aspire to be a steadfast ally of Project Kongor.
- Your heart yearns to bring game servers closer to your realm or a cherished region of the world.
- You are prepared to bestow as little as ~$20 USD per month to cover the AWS costs of orchestrating this wondrous server symphony.

Embark on this adventure with caution, for while AWS costs carry no commitment, the dance of provisioning holds a dual-edged charm. With careful steps, your bill can remain as elusive as a wisp in the night, but missteps may summon a towering AWS bill. Fear not, for this guide is your trusted companion, pointing out the treacherous turns and whispering, "BE CAREFUL" as you traverse the ethereal landscapes of cloud hosting. May your journey be both whimsical and prosperous! 🚀🔮

## Acronyms

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

For information on launching EC2 instances, refer to the [EC2 Instances Guide](/docs/ec2-instances.md)

### 1.2 Security Groups

For information on configuring security groups and opening the necessary ports, refer to the [Security Groups Guide](/docs/security-groups.md).

### 1.3 Public IP

By this point in the guide, you should have successfully launched your EC2 instance and configured the necessary security groups. Now, let's note the Public IP address assigned to your instance.

Follow these steps:

1. Navigate to the [AWS Management Console](https://aws.amazon.com/) and log in with your AWS account credentials.

2. In the top-right corner, click on "Services" and select "EC2" under the "Compute" section.

3. In the EC2 Dashboard, click on "Instances" in the left navigation pane.

4. Locate your recently spun-up instance in the Instances list. The "Public IP" column will display the public IP address assigned to your instance.

   - If the "Public IP" column is not visible, click the gear icon at the top right of the Instances table, select "Columns," and ensure "Public IP" is checked.

Note this Public IP - it will not change unless you terminate your instance. You will need it later when setting up HonFigurator

## Step 2: Configure Server Environment

### 2.1 Initial Ubuntu Setup

Now that your instance is running, we need to set up HoN. This is a very straightforward, no frills approach. Simply run these commands exactly as they are shown, and you will win.

- `sudo passwd ubuntu` -> set your password. This ensures noone can SSH into your server without your password.
- `echo -e '\nif [ -z "$TMUX" ]; then\ntmux attach-session -t default || tmux new-session -s default\nfi' >> ~/.bashrc && source ~/.bashrc`
- `sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt install curl sudo screen -y`

### 2.2 Game Server Installation

- `curl https://honfigurator.app/hon/server/las/installer.sh | sudo bash -`
- `chown +x /opt/hon/app/launcher`
- `sudo ./opt/hon/app/launcher`
- `sudo reboot`

Give your server a moment to respawn. It should not take long!

### 2.3 Launch and Configure HonFigurator

Once it is back up again:

- `cd /opt/hon/honfigurator`
- `sudo python3 main.py`

HonFigurator will prompt you for some information. Provide it your username that you created solely for hosting, alongside the password, discord ID, etc...
[See details](https://github.com/HoNfigurator/HoNfigurator-Central)

Ensure your server name follows convention! This is what players see when they type in /gi.

`<hon region>-<locality> <name>`

where...

- `<hon region>` is your server's location (AU/BR/EU/RU/SEA/TH/USE/USW), all caps
- `<locality>` is country dependent, so in america it would be the state, in other places like EU it would be the country. normal capitalization
- `<name>` would be the first 4-6 letters of your discord handle/hon username, normal capitalization

no special characters!

so for example:

- AU-Adelaide Derp
- USE-NewYork Grinsp
- USW-Arizona Honor

Your server should be running, perhaps with some warning messages about having a hosts role. Don't worry, just leave the server running.

### 2.4: Acquire Necessary Roles

Go to the #hosting channel in Project Kongor's discord channel. Copy paste this message:

> Would someone please provide \<your project kongor hosting account\> permissions to host, as well as the "Host" role for me in discord?

Both of these are required for your server to work!

Once someone grants you those permissions, your server will automatically pick that up and your servers will be available for players to connect to.

## Step 3: Monitoring

### 3.1 AWS Cost Explorer

Please see [AWS Cost Explorer](/docs/aws-cost-explorer.md)

### 3.2 HonFigurator Management Portal

Navigate to the [HonFigurator Management Portal](https://management.honfigurator.app/login)
Log in with your discord
Using the server name you created earlier in HonFigurator, and the public IP of your server, click Add Server at the top right and add your server to HonFigurator.

## Conclusion

Congratulations! You've successfully launched and configured your EC2 instance for hosting a Project Kongor Heroes of Newerth server on AWS.
Remmber to periodically check Cost Explorer to ensure your actual cost aligns with what you'd expect.

Thank you for hosting!
