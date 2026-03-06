# Key-Pair Authentication (Secure Login to EC2)

Instead of using passwords, AWS EC2 uses SSH key-pair authentication to securely connect to a Linux server.
This method is safer because the private key stays only on the user's computer and cannot be guessed like a password.

🧩 Steps Performed

## Step 1.Create Key Pair

1.While launching EC2 instance → Create new key pair

2.Downloaded .pem file

3.Stored securely on local machine

### Implementation Example:
![image alt](

## Step 2.Set Permission (Linux / Git Bash / MobaXterm) 
1.chmod 400 mykey.pem

2.This prevents other users from accessing the private key.

## Step 3. Connect to Instance via SSH

1.ssh -i mykey.pem ubuntu@<public-ip>

Example:

ssh -i awskey.pem ubuntu@3.110.xxx.xxx

## 🔒 How It Works (Concept)

AWS stores the public key inside the EC2 server

User keeps the private key

During login:

- Server verifies the key

- If matched → access granted

- No password required

This is called asymmetric cryptography authentication.

✅ Advantages

- More secure than passwords

- Prevents brute-force attacks

- Required for cloud production servers

- Used in DevOps automation

📌 Result

Successfully connected to the EC2 Linux instance securely using SSH key-pair authentication and performed remote server administration.
