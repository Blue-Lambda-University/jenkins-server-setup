
# Jenkins Infrastructure Setup (Cross-Distro, Ansible Automated)

This project automates the provisioning and configuration of a Jenkins CI/CD server on **Ubuntu**, **Amazon Linux**, **Debian**, or **RHEL-based** systems.

It installs:

- ✅ [Jenkins](https://www.jenkins.io/)
- ✅ [Terraform](https://www.terraform.io/)
- ✅ [Ansible](https://www.ansible.com/)
- ✅ Core Jenkins plugins (including Job DSL, without seed job auto-creation)

Provisioning is handled via an [Ansible](https://docs.ansible.com/) playbook that pushes and runs a universal `setup.sh` script.

---

## Prerequisites

- [Ansible installed](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on your local machine
- SSH access to your Jenkins server (EC2 or other Linux instance)
- `.pem` private key used for access
- Jenkins server must allow port **22 (SSH)** and **8080 (Jenkins)**
```bash
  sudo apt install ansible
```

---

## Configuration

### 1. Edit `inventory.ini`

```ini
[jenkins]
<your-server-ip> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/your-key.pem
```
- Replace <your-server-ip> with your actual public IP
- Use the correct ansible_user (ubuntu, ec2-user, etc.)
- Update the path to your private key

---

## Run the Playbook
Run this from the project root:
```angular2html
ansible-playbook -i inventory.ini playbook.yml
```
This will:
- Upload setup.sh to the server
- Install Terraform, Ansible, Jenkins
- Install core Jenkins plugins, including job-dsl

---
## Access Jenkins
Once complete, visit:
```angular2html
http://<your-server-ip>:8080
```
Use this to unlock Jenkins:
```angular2html
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---
## Author
- Jenkins Server Setup Automation by **Omolewa Adaramola** [![LinkedIn](https://img.shields.io/badge/LinkedIn-@OmolewaAdaramola-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/omolewa-adaramola/)


