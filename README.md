## Ansible Playbook for Deploying TP-Link Omada Controller

[![lint](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml/badge.svg)](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml)

Playbook tested on follwoing host distributions 
1. Debian 8, 9 & 10
2. CentOS 6, 7 & 8
3. Ubuntu 18.04, 20.04
4. Rocky Linux 8.4

Control Node is Ubuntu 20.04 LTS. Ansible 2.9 or higher required.

### Setup Ansible

1. Install pip `sudo apt install python3-pip -y`
2. install ansible with pip `pip install ansible` 
3. Install requirements `ansible-galaxy collection install -r requirements.yml`

### Installed Packages

1. `OpenJDK 1.8 Headless`   -- Omada only supports Java 8  
2. `MongoDB 3.6`    -- Omada Supports 3.4 to 3.6
3. `curl`
4. `jsvc`
5. `tar`

### Run

1. Clone the repo  `git clone https://github.com/kdpuvvadi/Omada-Ansible.git omada-ansible`. 
2. copy `example.inventory.ini` to `inventory.ini`.
3. Change necessary changes to inventory
4. copy `example.vars.yml` to `vars.yml`.
5. Change the variable based on your preferences.

### Run the playbook

Run `ansible-playbook main.yml` 

### Post Install

Omada controller will be avaiable on `https://HOST-IP:8088/`  or `https://HOST-IP:8043/`. For the Omada controller to work properly `8088, 8043, 27001, 27002, 29810, 29811, 29812 and 29813` ports should be open on the host. 


### Omada Service on host

*   `sudo tpeap status`     -- show the status of Controller;
*   `sudo tpeap start`     -- start the Omada Controller;
*   `sudo tpeap stop`     --stop running the Omada Controller.
