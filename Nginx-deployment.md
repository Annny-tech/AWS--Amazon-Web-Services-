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

![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/0dea3da2ee3a49912d1b83ca0598f5f0a352cbd9/Screenshot%202026-03-05%20152610.png)


Example:
```bash
ssh -i aws-key.pem ubuntu@13.233.xxx.xxx
```
