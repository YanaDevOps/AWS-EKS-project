# AWS EKS Pet Project
## 🌟 Overview
This project automates the provisioning of an Amazon EKS (Elastic Kubernetes Service) cluster and its supporting infrastructure using Terraform. It sets up networking, IAM roles, managed node groups, and cluster configurations for a production-ready Kubernetes environment.

## 🛠️ Technologies Used
* Terraform: Infrastructure as Code (IaC) tool for managing cloud infrastructure.
* Amazon EKS: Managed Kubernetes Service on AWS.
* Amazon VPC: Networking for the EKS cluster.
* AWS IAM: Access management for the cluster and nodes.

## 📂 Project Structure
```
├── eks-cluster.tf    # Defines the EKS cluster configuration
├── main.tf           # Entry point for Terraform resources
├── outputs.tf        # Outputs information after deployment
├── terraform.tf      # Terraform settings and backend configuration
├── variables.tf      # Variables used across Terraform modules
├── vpc.tf            # Virtual Private Cloud (VPC) configuration for EKS
└── README.md         # Project documentation (this file)
```

## 🚀 Getting Started
### 📦 Prerequisites
* Terraform (v1.3 or higher)
* AWS CLI installed and configured
* IAM user/role with Administrator Access
* Kubernetes CLI (kubectl) installed

### ⚙️ Setup Steps
1. Clone the repository:
```
git clone https://github.com/YanaDevOps/AWS-EKS-project.git
cd AWS-EKS-project
```
2. Initialize Terraform:
```
terraform init
```
3. Validate Terraform files:
```
terraform validate
```
4. Plan the Infrastructure:
```
terraform plan
```
5. Apply Terraform configuration:
```
terraform apply
```
6. Update kubeconfig for EKS access:
```
aws eks update-kubeconfig --region <region> --name <cluster-name>
```
7. Verify Cluster Access:
```
kubectl get nodes
```

## 📊 Terraform Outputs
After deployment, Terraform will output key information:

* Cluster Endpoint: The API server endpoint for kubectl.
* Node Group Details: Information about node groups and instances.
* VPC Details: VPC ID, subnet IDs, and route tables.

## 📘 Variables
----------------------------------------------------------------------
| **Variable**       | **Description**               | **Default**   |
|--------------------|-------------------------------|---------------|
| `cluster_name`     | Name of the EKS cluster       | `eks-cluster` |
| `cluster_version`  | Kubernetes version for the EKS| `1.27`        |
| `region`           | AWS region for deployment     | `us-east-1`   |
| `node_instance`    | EC2 instance type for nodes   | `t3.small`    |
| `desired_capacity` | Desired number of nodes       | `2`           |
| `max_capacity`     | Maximum number of nodes       | `3`           |
| `min_capacity`     | Minimum number of nodes       | `1`           |
----------------------------------------------------------------------

## 🔧 Troubleshooting
1. Nodes not showing up in kubectl get nodes:
  *Check IAM roles and permissions.
  * Verify aws-auth ConfigMap exists.

2. Authentication Errors:
  * Ensure AWS credentials are set in ~/.aws/credentials.
  * Verify the correct kubectl context is selected:
  ```
  kubectl config current-context
  ```

### 🤝 Contributing
Contributions are welcome! Feel free to fork this repository and submit pull requests.

### 👤 Author
Name: Yana Lysenko

GitHub: [YanaDevOps](https://github.com/YanaDevOps)