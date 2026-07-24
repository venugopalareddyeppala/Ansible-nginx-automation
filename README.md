<h1 align="center">🚀 Ansible Nginx Automation</h1>

<p align="center">
Automating Nginx Installation and Configuration on AWS EC2 using Ansible
</p>

<p align="center">
<img src="https://img.shields.io/badge/Ansible-Automation-red?style=for-the-badge&logo=ansible">
<img src="https://img.shields.io/badge/AWS-EC2-orange?style=for-the-badge&logo=amazonaws">
<img src="https://img.shields.io/badge/Nginx-Web_Server-green?style=for-the-badge&logo=nginx">
<img src="https://img.shields.io/badge/Ubuntu-24.04-E95420?style=for-the-badge&logo=ubuntu">
</p>

## 📌 Project Overview

This project automates the installation and configuration of **Nginx** on three Ubuntu EC2 instances using **Ansible**. A single Ansible Control Node manages all remote servers through SSH, installs Nginx, deploys customized web pages, and verifies that the service is running successfully.

---

## 🎯 Objective

- Configure an Ansible Control Node.
- Automate Nginx installation on multiple servers.
- Deploy unique HTML pages to each server.
- Restart Nginx automatically using Ansible Handlers.
- Validate the deployment and service status.

---

## 🛠️ Technologies Used

- Ansible
- AWS EC2
- Ubuntu 24.04 LTS
- Nginx
- SSH
- YAML
- Jinja2 Templates
- Git
- GitHub

---

## 📁 Project Structure

```text
ansible-nginx/
│
├── ansible.cfg
├── inventory
├── playbook.yml
├── group_vars/
├── host_vars/
├── templates/
│   ├── web1.html.j2
│   ├── web2.html.j2
│   └── web3.html.j2
├── .gitignore
└── README.md
```

---

## ⚙️ Prerequisites

- AWS Account
- Four Ubuntu EC2 Instances
  - 1 Ansible Control Node
  - 3 Managed Nodes
- AWS PEM Key Pair
- Git
- Internet Connection

---

## 🖥️ Environment

| Server | Purpose |
|---------|---------|
| Control Node | Ansible Control Node |
| Web1 | Managed Node |
| Web2 | Managed Node |
| Web3 | Managed Node |

---

# 🚀 Installation Guide

## Step 1: Connect to the Control Node

```bash
ssh -i venu.pem ubuntu@<CONTROL-NODE-IP>
```

---

## Step 2: Update the Server

```bash
sudo apt update -y
sudo apt upgrade -y
```

---

## Step 3: Install Ansible

```bash
sudo apt install software-properties-common -y

sudo add-apt-repository --yes --update ppa:ansible/ansible

sudo apt install ansible -y
```

Verify the installation:

```bash
ansible --version
```

---

## Step 4: Configure SSH Access

Create a PEM file on the Control Node.

```bash
nano venu.pem
```

Paste your AWS private key into the file.

Set the required permissions.

```bash
chmod 400 venu.pem
```

Verify SSH connectivity.

```bash
ssh -i venu.pem ubuntu@<WEB1-IP>

ssh -i venu.pem ubuntu@<WEB2-IP>

ssh -i venu.pem ubuntu@<WEB3-IP>
```

---

## Step 5: Clone the Repository

```bash
git clone https://github.com/venugopalareddyeppala/ansible-nginx-automation.git

cd ansible-nginx-automation
```

---

## Step 6: Verify Ansible Connectivity

```bash
ansible all -m ping
```

Expected Output

```text
web1 | SUCCESS
web2 | SUCCESS
web3 | SUCCESS
```

---

## ▶️ Execute the Playbook

```bash
ansible-playbook playbook.yml
```

or

```bash
ansible-playbook -i inventory playbook.yml
```

---

## 🌐 Verify Deployment

Open the following URLs in your browser.

```text
http://<WEB1-IP>
http://<WEB2-IP>
http://<WEB3-IP>
```

Expected Output

### Web Server 1

```
Welcome to Web Server 1
```

### Web Server 2

```
Welcome to Web Server 2
```

### Web Server 3

```
Welcome to Web Server 3
```

---

## ✅ Validate the Deployment

Check Nginx status.

```bash
ansible all -m shell -a "systemctl status nginx"
```

Check whether Nginx is enabled.

```bash
ansible all -m shell -a "systemctl is-enabled nginx"
```

Check if Port 80 is listening.

```bash
ansible all -m shell -a "ss -tuln | grep :80"
```

---

## ✨ Features

- Automated Nginx Installation
- Multi-Server Management
- Passwordless SSH Access
- Inventory-Based Configuration
- YAML Playbooks
- Jinja2 Templates
- Ansible Handlers
- Automated Service Restart
- Infrastructure Automation

---

## 📷 Expected Screenshots

- AWS EC2 Instances
- Ansible Installation
- PEM File Configuration
- SSH Connection
- Inventory File
- ansible.cfg
- Ansible Ping
- Playbook Execution
- Nginx Status
- Web Server 1
- Web Server 2
- Web Server 3
- Project Structure

---

## 📚 Learning Outcomes

- Learned Ansible Architecture
- Configured Passwordless SSH
- Created Inventory Files
- Executed Ad-hoc Commands
- Developed YAML Playbooks
- Automated Nginx Installation
- Used Jinja2 Templates
- Implemented Ansible Handlers
- Managed Multiple Servers from a Single Control Node

---

## 👨‍💻 Author

**Eppala Venu Gopala Reddy**

- **GitHub:** https://github.com/venugopalareddyeppala
- **LinkedIn:** https://www.linkedin.com/in/venugopalareddyeppala

---

## 📄 License

This project was developed as part of a **DevOps Internship Assignment** to demonstrate **Ansible-based automation and configuration management** on AWS EC2.
