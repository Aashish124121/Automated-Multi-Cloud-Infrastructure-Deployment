# 🌍 Terraform Multi-Cloud Infrastructure Project

**Stack:** Terraform · AWS · Azure · GCP · GitHub Actions (CI/CD)

---

[![Terraform](https://img.shields.io/badge/IaC-Terraform-blueviolet?logo=terraform)](https://www.terraform.io/)  
[![CI/CD](https://img.shields.io/badge/CI/CD-GitHub%20Actions-black?logo=github-actions)]  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)  
[![Made with ❤️](https://img.shields.io/badge/Made%20with-❤️-red)](#)  

**Cloud Providers:**  
[![AWS](https://img.shields.io/badge/AWS-232F3E?logo=amazon-aws&logoColor=white)](https://aws.amazon.com/)  
[![Azure](https://img.shields.io/badge/Azure-0078D4?logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)  
[![GCP](https://img.shields.io/badge/GCP-4285F4?logo=google-cloud&logoColor=white)](https://cloud.google.com/)  

**Languages & Tools:**  
![HCL](https://img.shields.io/badge/Code-HCL-5C2D91?logo=hashicorp)  
![GitHub Actions](https://img.shields.io/badge/CI/CD-GitHub%20Actions-black?logo=github-actions)  

---

## 📌 Project Overview

This project demonstrates how to manage **multi-cloud infrastructure** using **Terraform** with modular design, environment isolation, and a CI/CD-driven governance workflow.

The goal: **Provision & manage resources across AWS, Azure, and GCP** while enforcing automation, reusability, and collaboration best practices.

####  [Project Guide Documentation (PDF)](docs/Project%20Guide.pdf)

---

## 🏗️ Architecture

![Architecture Diagram](docs/Architecture%20Diagram.png)

### Layers

1. **Foundational Layer**

   * Base network setup (`base-network/`) across clouds
   * Global variables (`global-variables.tf`) for naming, tags, and standards

2. **Abstraction Layer**

   * Reusable modules:

     * `aws_vm/` → EC2 instances
     * `azure_storage/` → Storage accounts
     * `gcp_vm/` → GCE instances

3. **Deployment & Governance Layer**

   * Environments: `dev/`, `staging/`, `prod/`
   * CI/CD pipeline via GitHub Actions:

     * **Plan** → Pull request validation
     * **Apply** → Triggered on main branch merge

---
## 📂 Repository Structure

```
terraform-multicloud/
├── backend.tf              # Remote backend config
├── base-network/           # Shared base networking setup
├── docs/                   # Documentation & diagrams
├── envs/                   # Dev, staging, prod environment configs
├── modules/                # Cloud-specific reusable modules
│   ├── aws_vm/
│   ├── azure_storage/
│   └── gcp_vm/
├── global-variables.tf     # Shared tagging & standards
├── provider.tf             # Multi-cloud provider setup
├── versions.tf             # Terraform version constraints
└── .github/workflows/      # CI/CD pipeline
```

---

## ⚙️ Setup & Usage

### 1️⃣ Clone Repo

```bash
git clone https://github.com/your-username/terraform-multicloud.git
cd terraform-multicloud
```

### 2️⃣ Configure Backend & Secrets

* Setup **remote state** in AWS S3, GCS, or Azure Blob (see `backend.tf`).
* Store cloud credentials in **GitHub Actions secrets**:

  * `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`
  * `AZURE_CLIENT_ID`, `AZURE_CLIENT_SECRET`, `AZURE_TENANT_ID`, `AZURE_SUBSCRIPTION_ID`
  * `GOOGLE_CREDENTIALS` (JSON service account)

### 3️⃣ Deploy Infrastructure

Run Terraform manually (for testing):

```bash
cd envs/dev
terraform init
terraform plan
terraform apply
```

Or via GitHub Actions (preferred):

* Open a PR → triggers `terraform plan`
* Merge to main → triggers `terraform apply`

---

## 🔒 Governance & Security

* **CI/CD pipeline** enforces code review (Plan stage).
* **Environment isolation** ensures dev/staging/prod separation.
* **Secrets managed in GitHub** instead of hardcoded credentials.
* **Remote state backend** prevents drift & enables team collaboration.

---

## 📈 Outcomes

* Unified way to manage **AWS, Azure, and GCP** with a single codebase.
* Reduced manual cloud management → faster deployments.
* Improved security via **GitHub Secrets + remote state backends**.
* Reusable modules make it easy to scale & extend.

---

## ✅ Skills Demonstrated

* Multi-cloud Terraform provisioning
* Infrastructure modularization
* GitHub Actions for IaC CI/CD
* Environment isolation & governance
* Cloud provider interoperability

---
