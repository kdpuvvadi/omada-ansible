# Ansible Playbook for Deploying TP-Link Omada SDN Controller

Playbook tested on following host distributions

* Debian 10, 11
* RHEL 8
* Ubuntu 18.04, 20.04

> for [rhel 7](#support-for-rhel7) support try [rhel branch](../../tree/rhel7)

Tested on Control Node Ubuntu 20.04 LTS. Ansible 2.11.6.

## Setup Ansible

* Install pip `sudo apt install python3-pip -y`
* install ansible with pip `pip install -i requirements.txt`

## Installed Packages

* `OpenJDK 8 Headless`   -- Omada only supports Java 8 (from 5.4 java 17 is supported, check [java-17-branch](../../tree/java-17))
* `MongoDB 4.0`    -- Omada Supports 3.4 to 4.0
* `curl`
* `jsvc`
* `tar`

## Run

* Clone the repo  `git clone https://github.com/kdpuvvadi/omada-ansible.git omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* Inventory with `cp  inventory.ini.j2 inventory.ini`.
* Add IP and username of the server to the inventory.
* Variables with `cp vars.yml.j2 vars.yml`.

## Release

* For latest(5.9.31) [latest release](../../releases/v5.9.31)
* For verion 5.9.9 [latest release](../../releases/v5.9.9)
* For version 5.8.4 [release 5.8.4](../../releases/v5.8.4)
* For version 5.7.4 [release 5.7.4](../../releases/5.7.4)
* For version 5.6.3 [release 5.6.3](../../releases/v5.6.3)
* For version 5.5.6 [release 5.5.6](../../releases/v5.5.6)
* For version 5.4.6 [release 5.4.6](../../releases/v5.4.6)
* For version 5.3.1 [release 5.3.1](../../releases/v5.3.1)
* For version 5.1.7 [release 5.1.7](../../releases/v5.1.7)
* For version 5.0.30 [release 5.0.30](../../releases/v5.0.30)
* For version 5.0.29 [release 5.0.29](../../releases/v5.0.29)
* For version v4.4.6 (log4j-fix-CVE-2021-45046) [release 4.4.6](../../releases/v4.4.6-log4j-fix-CVE-2021-45046)
* For version 4.4.6 [release 4.4.4](../../releases/v4.4.6)
* For version 4.4.4 [release 4.4.4](../../releases/v4.4.4)
* For version 4.3.5 [release 4.3.5](../../releases/v4.3.5-020921)

## Run the playbook

* Run `ansible-playbook main.yml` append `-K`
* if you need password for `sudo` for root access on your host. `ansible-playbook main.yml -K`

## Post Install

* Omada controller will be available on `http://HOST-IP:8088/`  or `https://HOST-IP:8043/`.
* From v5.0.29 Adoption port has been changed to `29814/tcp`.

To work properly  ports `8088, 8043, 27001, 27002, 29810, 29811, 29812, 29813 and 29814` should be open.

## Omada Service on host

* `sudo tpeap status`     -- show the status of Controller;
* `sudo tpeap start`     -- start the Omada Controller;
* `sudo tpeap stop`     --stop running the Omada Controller.

## Support for rhel7

Support for rhel 7 ended(from [Red Hat](https://www.redhat.com/)) but you still want to install on one, here are the instructions

* Clone the repo  `git clone -b rhel7 https://github.com/kdpuvvadi/Omada-Ansible.git --single-branch omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* Inventory with `cp  inventory.ini.j2 inventory.ini`.
* Add IP and username of the server to the inventory.
* Variables with `cp vars.yml.j2 vars.yml`.
