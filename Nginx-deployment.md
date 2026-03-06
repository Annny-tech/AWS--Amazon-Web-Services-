# 🚀 AWS EC2 + NGINX Setup (Step-by-Step Guide)
## STEP 1️⃣ – Launch EC2 Instance

- Go to AWS Console

- Open EC2

- Click Launch Instance

- Choose:

   -AMI → Ubuntu 22.04

   -Instance Type → t2.micro (Free tier)

   -Create / Select Key Pair

- In Security Group:

  - Allow SSH (22) from your IP

  - Allow HTTP (80) from Anywhere (0.0.0.0/0)

- Launch Instance

## Step 2 - Connect to Ec2 server via terminal
From your local terminal:
```bash
ssh -i your-key.pem ubuntu@your-public-ip
```
Example:
```bash
ssh -i aws-key.pem ubuntu@13.233.xxx.xxx
```
