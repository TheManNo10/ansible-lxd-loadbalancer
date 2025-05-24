# Ansible LXD Nginx Load Balancer Project

This project demonstrates how to set up a simple load balancing environment using **LXD containers** and **Ansible** automation. It includes:

- Two web server containers running Nginx
- One load balancer container running Nginx configured as a reverse proxy

## 🚀 Project Overview

### Containers
- `web1` — Nginx web server
- `web2` — Nginx web server
- `loadbalancer` — Nginx acting as a load balancer

### Tools Used
- Ubuntu 20.04 LTS containers
- LXD for container management
- Ansible for automation and orchestration

## 🛠️ Setup Instructions

### Step 1: Create Containers
```bash
lxc launch images:ubuntu/20.04 web1
lxc launch images:ubuntu/20.04 web2
lxc launch images:ubuntu/20.04 loadbalancer



#Step 2: Prepare the Inventory file (hosts.ini)
List your container IPs and group them for Ansible.

#Step 3: Configure Web Servers (web.yml)
Install Nginx and start the service on web1 and web2.

#Step 4: Configure Load Balancer (loadbalancer.yml)
Install Nginx on loadbalancer

#Deploy a Jinja2 template for the Nginx load balancer config

#Enable the load balancer site and restart Nginx

#Step 5: Run Playbooks
ansible-playbook -i hosts.ini web.yml -u root
ansible-playbook -i hosts.ini loadbalancer.yml -u root


##Verify Setup
##Access the load balancer IP via browser or curl

##You should see content served from web1 and web2 alternately (round-robin)


##Project Structure
ansible-lxd-loadbalancer/
├── files/
│   └── loadbalancer.conf.j2         # Nginx load balancer config template
├── group_vars/
│   └── loadbalancer.yml             # Backend server IP list
├── hosts.ini                        # Ansible inventory file
├── web.yml                         # Playbook to configure web servers
├── loadbalancer.yml                # Playbook to configure load balancer
└── README.md                       # This documentation

#License
This project is open-source and free to use.
