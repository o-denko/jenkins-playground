# Jenkins Apache Automation Lab

This project demonstrates a modern CI/CD approach to infrastructure management using Jenkins Pipelines.

## 📋 Task Requirements
1. **Automated Deployment**: Install and configure Apache2 (`httpd`) on a remote Ubuntu server.
2. **Log Monitoring**: Scan system logs for HTTP 4xx and 5xx errors.
3. **Pipeline as Code**: Use a `Jenkinsfile` stored in GitHub.

## 🛠 Project Architecture
* **Orchestration**: Jenkins (running in Docker)
* **Virtualization**: Proxmox 7 (hosting the Ubuntu 24.04 VM)
* **Connectivity**: SSH with Key-based authentication (Ed25519)

## 💡 Why this is a "Better Solution"
Compared to a standard Freestyle project, this implementation offers:
* **Version Control**: The entire deployment logic is stored in Git, allowing for easy audits and rollbacks.
* **Security**: Utilizes `ssh-agent` and Jenkins Credentials. No passwords are stored in the script.
* **Non-interactive Automation**: Configured `NOPASSWD` in sudoers for seamless execution.
* **Scalability**: Declarative syntax makes it easy to add more stages (e.g., testing or staging).

## 🚀 How to Run
1. Create a **Pipeline** job in Jenkins.
2. Link it to this GitHub repository.
3. Configure SSH credentials with ID `ubuntu-ssh-creds` in Jenkins.
4. Run the build.

---
*Created as part of the SoftServe Academy DevOps course.*
