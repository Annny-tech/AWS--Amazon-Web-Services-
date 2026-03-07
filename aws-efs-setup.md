# Amazon EFS Setup and Shared Storage Demonstration -
This project demonstrates the implementation of Amazon Elastic File System (EFS) in AWS. The objective is to create a shared file storage system that can be mounted on multiple EC2 instances within a VPC. By using EFS, different servers can access, read, and write data from the same storage location simultaneously.

In this demonstration, an EFS file system is created, configured with the required networking and security settings, and mounted on Ubuntu EC2 instances. The setup verifies that files created on one server are accessible from another, showing how EFS provides scalable and centralized storage for cloud-based applications.

## Architecture Overview:

- VPC

- 2 Subnets

- 2 EC2 Instances

- Amazon EFS

- Shared storage mounted using NFS

## Implementation Steps

### 1. Create a VPC

- Go to the AWS Console → VPC Dashboard.

- Create a new VPC or use the default one.

- Create two subnets in different Availability Zones.
  
### Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/4700c79eb42cc69d4451ddb55d2ef24b45cf6ca6/Images/vpc_efs.png)
  
### 2. Create a Security Group for EFS

- Create a new security group.

- Allow NFS (port 2049) inbound.

- Set the source as the EC2 instances security group.
  
### Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/5827ff2b779e8fc6c1386c5d57ca257eb6a65382/Images/sg_efs.png)

### 3. Launch EC2 Instances using same security group>

- Go to EC2 → Launch Instance.

- Select Ubuntu Server.

- Launch two EC2 instances in the created subnets.

- Assign a security group .

### Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/4616e941b0ac297f7f71e87eca7059e45d5e37d3/Images/efs-servers.png)

### 4. Create an EFS File System

- Go to AWS EFS → Create File System.

- Select the same VPC used by the EC2 instances.

- Create mount targets in both subnets.

- Attach the EFS security group.

### Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/4616e941b0ac297f7f71e87eca7059e45d5e37d3/Images/efs-servers.png)

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

### 7. Create a Mount Directory
```
sudo mkdir /efs
```
### 8. Mount the EFS File System
```
sudo mount -t nfs4 -o nfsvers=4.1 fs-xxxxxx:/ /efs
```

### Implementation Example:
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/f4ab0103d71a45dcbacb2d3c643b678eb898f676/Images/mkdir%20and%20mount.png)

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
![image alt](https://github.com/Annny-tech/AWS--Amazon-Web-Services-/blob/653865a009d14b102bfbc5fe65fba3391e947f5f/Images/textfile%20edit%20efs.png)

You will see the same file, confirming that EFS is successfully shared between instances.

### Conclusion:

This project demonstrates the setup and implementation of Amazon Elastic File System (EFS) in an AWS environment. The goal is to create a shared network file system that can be mounted on multiple EC2 instances within the same VPC.

In this setup, an EFS file system is created and configured with the required mount targets and security settings. Ubuntu EC2 instances are then connected to the file system using NFS and a mount directory is created to access the shared storage.

The demonstration verifies that files created on one server can be accessed from another server, proving that EFS provides scalable, centralized, and shared storage for multiple instances in the cloud. This type of architecture is commonly used in distributed applications, web servers, and environments where multiple systems need simultaneous access to the same data
