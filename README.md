# Terraform Cluster

## Overview

This project defines and manages an **Amazon Web Services (AWS)** infrastructure using **Terraform**. The infrastructure includes a **VPC**, **subnets**, an **EKS cluster**, **IAM roles**, **security groups**, and **CloudWatch logs**. Terraform is used to automate the creation and management of these resources, ensuring reproducibility and consistency across environments.

## Infrastructure Overview

**1. VPC (Virtual Private Cloud):**
   * A virtual network defined in AWS to isolate resources and securely manage communication between them.
   * CIDR block is provided dynamically through a Terraform variable.

**2. Subnets:**
   * Two public subnets are created, each in different availability zones to ensure high availability.
   * Public IPs are assigned automatically to instances in these subnets.
  
**3. Internet Gateway:**
   * Allows resources in the VPC to access the internet and receive incoming traffic from external networks.

**4. Route Tables:**
   * The route table directs internet-bound traffic (0.0.0.0/0) to the internet gateway for external communication.
   
**5. Security Group:**
   * A security group is created to control inbound and outbound traffic for the resources in the VPC.

**6. IAM Roles and Policies:**
   * IAM Role for EKS Cluster: Allows EKS to interact with other AWS services.
   * IAM Role for EC2 Instances: Provides permissions to EC2 instances within the node group to communicate with AWS services like ECR and CloudWatch.

**7. Amazon EKS Cluster:**
   * Managed Kubernetes cluster that runs containerized applications. The EKS cluster is set up with logging enabled for API and audit events.

**8. CloudWatch Logs:**
   * Logs for the EKS cluster are sent to CloudWatch for monitoring and troubleshooting.
   
**9. Node Group:**
   * A node group consists of EC2 instances that serve as worker nodes in the Kubernetes cluster. The instances are automatically managed by EKS for scaling and lifecycle management.

![diagram-export-27-12-2024-15_52_05](https://github.com/user-attachments/assets/2bd8440c-60ca-4a73-bb79-e625aab6291b)

## How to run

To run Terraform and apply the infrastructure defined in this project, follow these steps:

**1. Initialize Terraform**
   
Before running any Terraform commands, you need to initialize the project directory. This downloads the necessary provider plugins and prepares the environment.

```bash
terraform init
```

**2. Validate the Configuration**

Check whether the configuration files are syntactically correct and valid.

```bash
terraform validate
```

**3. Preview the Infrastructure Changes**
   
Generate an execution plan to see what changes Terraform will make to the infrastructure. This is an important step to ensure that the changes align with expectations before applying them.

```bash
terraform plan
```

**4. Apply the Configuration**
   
Apply the changes to create or update the infrastructure based on the configuration files. Terraform will prompt for confirmation before proceeding.

```bash
terraform apply
```

You can confirm by typing yes when prompted.

**5. Destroy the Infrastructure**
   
If you want to tear down all the resources created by Terraform, you can run the following command:

```bash
terraform destroy
```

This will remove all the resources from your AWS account based on the Terraform configuration.

**6. View the Current Infrastructure State**
   
If you want to check the current state of your infrastructure, you can use:

```bash
terraform show
```
