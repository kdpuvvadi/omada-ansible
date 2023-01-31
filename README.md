# Ansible Playbook for Deploying TP-Link Omada SDN Controller

[![lint](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml/badge.svg)](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml)

Playbook tested on follwoing host distributions

* RHEL 7

Tested on Control Node Ubuntu 20.04 LTS. Ansible 2.11.6.

## Setup Ansible

* Install pip `sudo apt install python3-pip -y`
* install ansible with pip `pip install ansible`

## Installed Packages

* `OpenJDK 1.8 Headless`   -- Omada only supports Java 8
* `MongoDB 3.6`    -- Omada Supports 3.4 to 4.0
* `curl`
* `jsvc`
* `tar`

## Run

Support for rhel ended(from [Red Hat](https://www.redhat.com/)) but you still want to install on one, here are the instructions

* Clone the repo  `git clone -b rhel7 https://github.com/kdpuvvadi/Omada-Ansible.git --single-branch omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* copy `inventory.ini.j2` to `inventory.ini`.
* Change necessary changes to inventory.
* copy `vars.yml.j2` to `vars.yml`.
* Change the variable based on your preferences.

## Run the playbook

* Run `ansible-playbook main.yml` append `-K`
* if you need password for `sudo` for root access on your host. `ansible-playbook main.yml -K`

## Post Install

* Omada controller will be avaiable on `https://HOST-IP:8088/`  or `https://HOST-IP:8043/`.
* From v5.0.29 Adoption port has been changed to `29814/tcp`.

To work properly  ports `8088, 8043, 27001, 27002, 29810, 29811, 29812, 29813 and 29814` should be open.

## Omada Service on host

* `sudo tpeap status`     -- show the status of Controller;
* `sudo tpeap start`     -- start the Omada Controller;
* `sudo tpeap stop`     --stop running the Omada Controller.
