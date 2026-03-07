# Amazon EFS Setup and Shared Storage Demonstration -
This project demonstrates the implementation of Amazon Elastic File System (EFS) in AWS. The objective is to create a shared file storage system that can be mounted on multiple EC2 instances within a VPC. By using EFS, different servers can access, read, and write data from the same storage location simultaneously.

In this demonstration, an EFS file system is created, configured with the required networking and security settings, and mounted on Ubuntu EC2 instances. The setup verifies that files created on one server are accessible from another, showing how EFS provides scalable and centralized storage for cloud-based applications.

## Implementation Steps

### 1. Create a VPC

- Go to the AWS Console → VPC Dashboard.

- Create a new VPC or use the default one.

- Create two subnets in different Availability Zones.
  
### Implementation Example:
![image alt]()
  
### 2. Create a Security Group for EFS

- Create a new security group.

- Allow NFS (port 2049) inbound.

- Set the source as the EC2 instances security group.
  
### Implementation Example:
![image alt]()

### 3. Launch EC2 Instances using same security group>

- Go to EC2 → Launch Instance.

- Select Ubuntu Server.

- Launch two EC2 instances in the created subnets.

- Assign a security group .

### Implementation Example:
![image alt]()

### 4. Create an EFS File System

- Go to AWS EFS → Create File System.

- Select the same VPC used by the EC2 instances.

- Create mount targets in both subnets.

- Attach the EFS security group.

### Implementation Example:
![image alt]()

### 5. Connect to EC2 Instances

- Use SSH to connect to your instances:
```
ssh -i key.pem ubuntu@public-ip
```

### 6. Install NFS Client

- Run the following command on both instances:
```
sudo apt update
```
```
sudo apt install nfs-common -y
```
### Implementation Example:
![image alt]()

### 7. Create a Mount Directory
```
sudo mkdir /efs
```
### 8. Mount the EFS File System
```
sudo mount -t nfs4 -o nfsvers=4.1 fs-xxxxxx:/ /efs
```

### Implementation Example:
![image alt]()

(Replace fs-xxxxxx with your EFS File System ID.)

### 9. Test Shared Storage

- Create a file on the first instance:
```
cd /efs
```
```
sudo touch testfile
```
- Now check the same directory on the second instance:
```
cd /efs
```

### Implementation Example:
![image alt]()

You will see the same file, confirming that EFS is successfully shared between instances.
