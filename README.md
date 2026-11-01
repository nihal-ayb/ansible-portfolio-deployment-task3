# Ansible-Based Portfolio Website Deployment

## Project Overview

This project demonstrates the automated deployment of a static portfolio website on an AWS EC2 Ubuntu server using Ansible and Nginx.

Ansible is used to configure the target server, install and start Nginx, and deploy the website files through a reusable Ansible role.

## Technologies Used

- **AWS EC2** — Cloud infrastructure
- **Ubuntu Linux** — Operating system
- **Ansible** — Configuration management and deployment automation
- **Nginx** — Web server
- **HTML5** — Website structure
- **CSS3** — Website styling
- **Git and GitHub** — Version control and source-code hosting

## Project Structure

```text
ansible-portfolio-deployment-task3/
├── inventory/
│   └── inventory.ini
├── roles/
│   └── portfolio/
│       ├── files/
│       │   ├── index.html
│       │   ├── about.html
│       │   ├── projects.html
│       │   ├── contact.html
│       │   └── style.css
│       └── tasks/
│           └── main.yml
├── screenshots/
├── site.yml
└── README.md
```

## Infrastructure

The deployment uses two AWS EC2 instances:

- **Control Node:** Runs Ansible and initiates the deployment.
- **Target Node:** Receives the configuration and hosts the website using Nginx.

Ansible connects to the target node over SSH to execute the deployment tasks.

## Deployment Process

### 1. Configure the Inventory

The inventory file, `inventory/inventory.ini`, identifies the target server and specifies the SSH connection details.

### 2. Define the Ansible Role

The role is located at `roles/portfolio/`.

Its task file, `roles/portfolio/tasks/main.yml`, automates the following operations:

- Installs Nginx.
- Starts Nginx and enables it to start automatically at boot.
- Copies the portfolio website files into `/var/www/html/`.

### 3. Configure the Playbook

The root-level `site.yml` targets the `web` host group, enables privilege escalation, and executes the `portfolio` role.

### 4. Execute the Deployment

Run the following command from the project root on the Ansible control node:

```bash
ansible-playbook -i inventory/inventory.ini site.yml
```

### 5. Verify the Deployment

After a successful playbook execution, access the target EC2 instance's public IP address using a web browser:

```text
http://<TARGET-PUBLIC-IP>
```

The target instance's security group must allow inbound HTTP traffic on TCP port 80.

## Screenshots

The `screenshots/` directory contains visual evidence of the project setup and deployment, including:

- AWS EC2 instances
- Ansible project structure
- Successful Ansible deployment
- Live portfolio website

## Deployment Result

The playbook executed successfully, with all tasks completing and zero failed or unreachable hosts.

The portfolio website was deployed and verified in a browser.

## Repository

GitHub: https://github.com/nihal-ayb/ansible-portfolio-deployment-task3

---

**Project:** Portfolio Website Deployment Using Ansible Roles  
**Platform:** AWS EC2  
**Web Server:** Nginx
