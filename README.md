# Ansible Playbook for Deploying TP-Link Omada SDN Controller

[![lint](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml/badge.svg)](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml)

Playbook tested on follwoing host distributions

* Debian 8, 9 & 10
* CentOS 6, 7
* Ubuntu 18.04, 20.04

Tested on Control Node Ubuntu 20.04 LTS. Ansible 2.11.6.

## Setup Ansible

* Install pip `sudo apt install python3-pip -y`
* install ansible with pip `pip install ansible`
* Install requirements `ansible-galaxy collection install -r requirements.yml`

## Installed Packages

* `OpenJDK 1.8 Headless`   -- Omada only supports Java 8
* `MongoDB 3.6`    -- Omada Supports 3.4 to 3.6
* `curl`
* `jsvc`
* `tar`

## Run

* Clone the repo  `git clone https://github.com/kdpuvvadi/Omada-Ansible.git omada-ansible`.
* copy `inventory.ini.j2` to `inventory.ini`.
* Change necessary changes to inventory
* copy `vars.yml.j2` to `vars.yml`.
* Change the variable based on your preferences.

## Release

* For log4j fixed [release v4.4.6 Log4j Fix Latest](../../releases/v4.4.6-log4j-fix)
* For latest [Latest release](../../releases/latest)
* For version 4.4.4 go to [release 4.4.4](../../releases/v4.4.4-23092021)
* For version 4.3.5 go to [release 4.3.5](../../releases/v4.3.5-020921)



## Run the playbook

* Run `ansible-playbook main.yml` append `-K`
* if you need password for `sudo` for root access on your host. `ansible-playbook main.yml -K`

## Post Install

* Omada controller will be avaiable on `https://HOST-IP:8088/`  or `https://HOST-IP:8043/`.

To work properly  ports `8088, 8043, 27001, 27002, 29810, 29811, 29812 and 29813` should be open.

## Omada Service on host

* `sudo tpeap status`     -- show the status of Controller;
* `sudo tpeap start`     -- start the Omada Controller;
* `sudo tpeap stop`     --stop running the Omada Controller.

## Limitation

* Does not work on CentOS 8 based linux distribution.
