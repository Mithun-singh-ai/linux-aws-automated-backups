# End-to-End Secure Cloud Infrastructure & Automated Backup Pipeline (AWS + Linux)

## 🚀 Project Overview
This project combines **Cloud Networking** and **Linux System Administration**. It demonstrates how to provision a secure, isolated cloud environment from scratch and build an automated production backup workflow using Bash scripting, the AWS CLI, IAM roles, and Linux cron jobs.

---

## 🏗️ Architecture & Network Design 
Before deploying workloads, a production-grade networking environment was engineered manually:
- **Custom VPC:** Provisioned a custom Virtual Private Cloud (`10.0.0.0/24`) to isolate all resources.
- **Subnets:** Created multi-AZ **Public Subnets** to host public-facing components securely.
- **Internet Gateway (IGW) & Route Tables:** Attached an IGW and configured custom route tables to control external traffic flow.
- **Security Groups:** Engineered strict virtual firewall rules to allow secure inbound access (SSH, HTTP on Port 80).

---

## ⚙️ Automation & Storage Pipeline
Inside this custom network environment, an automated backup pipeline was deployed:
1. **Web Server Layer:** Launched an EC2 instance inside the custom public subnet, installed Nginx, and deployed a custom web page.
2. **Cloud Security (IAM):** Attached an IAM Role with S3 write permissions directly to the EC2 instance, avoiding the security risk of hardcoded credentials.
3. **Bash Scripting (`backup.sh`):** Wrote a custom shell script that dynamically timestamps website files, compresses them into a `.tar.gz` archive, uploads them to Amazon S3 via the AWS CLI, and cleans up local temporary files.
4. **Cloud Storage (Amazon S3):** Provisioned a dedicated S3 bucket acting as the secure off-site backup destination.
5. **Cron Automation:** Scheduled a Linux **Cron Job** to execute the backup script automatically every day at midnight.

---

## 🛠️ Tech Stack & Skills Demonstrated
- **AWS Networking:** VPCs, Subnets, Internet Gateways, Route Tables, Security Groups
- **AWS Core Services:** EC2, S3, IAM Roles & Policies, AWS CLI
- **Linux Administration:** File permissions, directory management, Nginx setup, Cron job scheduling
- **Automation:** Bash Shell Scripting (`tar` compression, variable management, error handling)
