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

Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/186ea812cce0b767779b698736a39621ad4711fe/Images/Screenshot%202026-03-06%20234245.png)

## Step 2 - Connect to Ec2 server via terminal
From your local terminal:
```bash
ssh -i your-key.pem ubuntu@your-public-ip
```
Example:
```bash
ssh -i aws-key.pem ubuntu@13.233.xxx.xxx
```

## Step 3 - Now update the system and install the nginx package
```bash
apt update && apt install nginx -y
```
This command will update the ubuntu server and inorder to update the amazon linux (ec2) server we have to use yum command , after that we have installed the nginx package in the ubuntu server.

Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/ea18dc9d225018f109b96d3bbe35071ce11f298d/Images/Screenshot%202026-03-06%20235250.png)

## Step 4 - Start and Enable NGINX

Start the service:
``` bash
sudo systemctl start nginx
```

Enable auto start on boot:
``` bash 
sudo systemctl enable nginx
```

Check status:
```bash
sudo systemctl status nginx
```
## Step 5 - Move Website Files to NGINX Directory

Default NGINX website folder:
```bash
/var/www/html
```

## Step 6 _🔟 Open Website in Browser

- Go to:

http://your-server-public-ip

Example:

http://13.234.xx.xx

Your website should now load.

Implementation Example:
![image alt]()
