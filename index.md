[![lint](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml/badge.svg)](https://github.com/kdpuvvadi/Omada-Ansible/actions/workflows/lint.yml)

Playbook tested on follwoing host distributions

* Debian 10, 11
* RHEL 8
* Ubuntu 18.04, 20.04

> for [rhel7](#support-for-rhel7) support try [rhel7 branch]([../../tree/rhel7](https://github.com/kdpuvvadi/Omada-Ansible/tree/rhel7))

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

* Clone the repo  `git clone https://github.com/kdpuvvadi/Omada-Ansible.git omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* copy `inventory.ini.j2` to `inventory.ini`.
* Change necessary changes to inventory.
* copy `vars.yml.j2` to `vars.yml`.
* Change the variable based on your preferences.

## Release

* For latest(5.4.6) [Latest release](../../releases/latest)
* For version(5.3.1) [release 5.3.1](../../releases/v5.3.1)
* For version 5.1.7 [release 5.1.7](../../releases/v5.1.7)
* For version 5.0.30 [release 5.0.30](../../releases/v5.0.30)
* For version 5.0.29 go to [release 5.0.29](../../releases/v5.0.29)
* For version v4.4.6 (log4j-fix-CVE-2021-45046) go to [release 4.4.6](../../releases/v4.4.6-log4j-fix-CVE-2021-45046)
* For version 4.4.6 go to [release 4.4.4](../../releases/v4.4.6)
* For version 4.4.4 go to [release 4.4.4](../../releases/v4.4.4)
* For version 4.3.5 go to [release 4.3.5](../../releases/v4.3.5-020921)

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

## Support for rhel7

Support for rhel ended(from [Red Hat](https://www.redhat.com/)) but you still want to install on one, here are the instructions

* Clone the repo  `git clone -b rhel7 https://github.com/kdpuvvadi/Omada-Ansible.git --single-branch omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* copy `inventory.ini.j2` to `inventory.ini`.
* Change necessary changes to inventory.
* copy `vars.yml.j2` to `vars.yml`.
* Change the variable based on your preferences.
