Azure with Terraform

This project demonstrates the deployment of a fully functional Linux virtual machine on Microsoft Azure using Terraform. The VM is automatically provisioned to run [Open WebUI](https://github.com/open-webui/open-webui) in a Docker container, with optional support for OpenAI API keys. The system is provisioned using cloud-init and includes a service readiness check using [Terracurl](https://github.com/alphaflow/terracurl).

## 🔧 What It Does

- Sets up:
  - Azure Resource Group
  - Virtual Network and Subnet
  - Public IP and Network Interface
  - Linux Virtual Machine (Debian-based)
- Installs:
  - Docker
  - Open WebUI server
- Configures:
  - Custom admin credentials
  - Optional OpenAI API integration
  - Persistent systemd service for Open WebUI
  - Service health check using Terracurl

> ✅ GPU provisioning logic is included but **currently disabled by default**.

## 🛠️ Prerequisites

- [Terraform](https://developer.hashicorp.com/terraform/install)
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
- Azure subscription
- SSH key pair (`id_rsa`, `id_rsa.pub`)

## 🚀 Getting Started

1. **Clone the repository**

```bash
git clone https://github.com/Quazirafi1/azure_with_terraform.git
cd azure_with_terraform
```

2. Set environment variables

```bash
export ARM_CLIENT_ID="your-client-id"
export ARM_CLIENT_SECRET="your-client-secret"
export ARM_SUBSCRIPTION_ID="your-subscription-id"
export ARM_TENANT_ID="your-tenant-id"

export TF_VAR_open_webui_user="admin@demo.gs"
export TF_VAR_openai_key="your-openai-api-key"
export TF_VAR_ssh_pub_key="C:/Users/<You>/.ssh/id_rsa.pub"
```

3. Initialize Terraform, view plan, and apply

```bash
terraform init
terraform plan
terraform apply
```

4. Access the service
Once deployed, the public IP of your VM will be output.

5. View and use the randomly generated password to login to the dashboard
```bash
terraform output password
```

6. Destroy the resources once done using
```bash
terraform destroy
```

Note: This project is build following the official HashiCorp step by step tutorial for learning purposes. 
