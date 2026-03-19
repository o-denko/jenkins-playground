# jenkins-playground
Practical assignment focusing on Jenkins CI/CD pipeline automation.

# Jenkins Apache Automation Lab

A Declarative Jenkins Pipeline for automated deployment and monitoring of the Apache2 web server.

## 🚀 Pipeline Features
* **Automated Installation**: Installs `apache2` on a remote Ubuntu 24.04 host using SSH.
* **Log Monitoring**: Scans `/var/log/apache2/access.log` for **4xx** and **5xx** HTTP errors.
* **Secure Access**: Uses Jenkins Credentials and `ssh-agent` for secure remote execution.

## 🛠 Tech Stack
* **Jenkins** (LTS JDK17)
* **Docker** (Jenkins running as a container)
* **Proxmox 7** (Virtualization platform)
* **Ubuntu 24.04** (Target OS)

## 📋 How to Run
1. Create a **Pipeline Job** in Jenkins.
2. Select **Pipeline script from SCM**.
3. Point to this repository URL and the `main` branch.
4. Ensure Jenkins has SSH Credentials configured with ID `ubuntu-ssh-creds` for access to the target VM.

---
*Created as part of the SoftServe Academy DevOps course.*
