Here's a creative and comprehensive `README.md` for provisioning an EKS (Elastic Kubernetes Service) cluster on AWS using Terraform. This template includes all the necessary steps, but also adds some flair to make it more engaging.

----

# Terraform EKS Cluster Provisioning

Welcome to the **EKS Cluster Provisioning** repository! Here, we use **Terraform** to provision a scalable and secure **Amazon EKS** (Elastic Kubernetes Service) cluster on **AWS**. This is your one-stop solution for easily setting up a Kubernetes cluster in the cloud, whether you're a developer, DevOps engineer, or cloud enthusiast.

---

## 🌐 Overview

This repository provides the Terraform code to create a fully managed **Amazon EKS cluster** in AWS, with the following features:

- **AWS IAM Roles & Policies**: Secure authentication and access control
- **VPC & Networking**: Custom Virtual Private Cloud (VPC) with subnets, internet gateway, and security groups
- **EKS Cluster**: Managed Kubernetes cluster with worker nodes
- **Node Groups**: EC2 Auto Scaling groups for Kubernetes worker nodes

All you need is your AWS account, Terraform installed, and a few simple commands to spin up your cloud-native infrastructure in minutes.

---

## 🚀 Getting Started

Follow these steps to deploy your own **EKS Cluster** using **Terraform**.

### Prerequisites

Before you get started, make sure you have the following installed:

1. **AWS CLI** - For interacting with your AWS account:
   - Install: https://aws.amazon.com/cli/
   - Set up your credentials:  
     ```bash
     aws configure
     ```

2. **Terraform** - The Infrastructure-as-Code tool to provision your resources:
   - Install: https://www.terraform.io/downloads.html

3. **kubectl** - Command-line tool for interacting with your Kubernetes cluster:
   - Install: https://kubernetes.io/docs/tasks/tools/install-kubectl/

---

### 1. Clone the Repository

Start by cloning this repository to your local machine:

```bash
git clone https://github.com/ssupshub/EKS-cluster-with-terraform.git
cd EKS-cluster-with-terraform
```

### 2. Configure AWS Credentials

Ensure that your AWS CLI is configured with the appropriate access and secret keys. Alternatively, use IAM roles if running on EC2 instances with the necessary permissions.

### 3. Set Up Terraform Variables

In the `variables.tf` file, configure your AWS region, EKS cluster name, and other variables such as node instance type and desired node count.

```hcl
# Example variables.tf
variable "region" {
  default = "us-west-2"
}

variable "cluster_name" {
  default = "my-eks-cluster"
}

variable "node_instance_type" {
  default = "t3.medium"
}

variable "desired_node_count" {
  default = 2
}
```

Feel free to adjust these parameters to suit your requirements.

### 4. Initialize Terraform

Run the following command to initialize Terraform and download the required providers:

```bash
terraform init
```

### 5. Plan and Apply Changes

Preview the resources Terraform will create using the `terraform plan` command:

```bash
terraform plan
```

If everything looks good, proceed to apply the configuration:

```bash
terraform apply
```

Terraform will prompt you for confirmation. Type `yes` to start provisioning the EKS cluster and related resources.

---

## 🧑‍💻 Access Your EKS Cluster

Once the resources are provisioned, you'll need to configure `kubectl` to interact with your new EKS cluster.

1. Install `aws-iam-authenticator` (if not already installed):
   - Follow the instructions here: https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html

2. Update your kubeconfig file to point to the new EKS cluster:

   ```bash
   aws eks --region <region> update-kubeconfig --name <cluster-name>
   ```

3. Verify the connection:

   ```bash
   kubectl get svc
   ```

If the connection is successful, you should see the Kubernetes services in your cluster.

---

## 🔨 Customization

- **Node Groups**: You can customize the EC2 instance type or the number of worker nodes in the cluster by modifying the variables in `variables.tf`.
- **Scaling**: Adjust the scaling settings for your node groups to automatically scale based on resource usage.
- **Kubernetes Add-ons**: You can integrate other tools like Helm, Prometheus, or Istio by installing them through `kubectl` or Terraform itself.

---

## 📄 Resource Breakdown

Here's an overview of what Terraform will create:

- **EKS Cluster**: A fully-managed Kubernetes cluster with an associated control plane.
- **VPC**: A custom Virtual Private Cloud with subnets, route tables, and security groups.
- **IAM Roles & Policies**: Proper roles and policies for EKS, worker nodes, and other resources.
- **Node Group**: EC2 Auto Scaling groups for worker nodes running Kubernetes workloads.

---

## 🔑 Clean Up

When you're done, make sure to destroy the resources to avoid unnecessary AWS charges:

```bash
terraform destroy
```

Terraform will prompt for confirmation before deleting all resources.



---

## 🙌 Contributing

We welcome contributions! If you have any improvements, bug fixes, or new features to add, feel free to fork the repository and create a pull request. Be sure to follow best practices for code style and include tests where appropriate.

---

## 🌟 Acknowledgements

- AWS for providing **EKS** and the related tools to manage Kubernetes in the cloud.
- Terraform for making infrastructure-as-code so easy and fun!
- The Kubernetes community for making Kubernetes the de facto container orchestration platform.

---

## 🚀 Happy Deploying!

You’re all set! With just a few commands, you’ve provisioned your very own EKS cluster. Now, it's time to deploy your containerized apps, monitor them, and take full advantage of Kubernetes on AWS.

Let the Kubernetes magic begin! ✨



---

