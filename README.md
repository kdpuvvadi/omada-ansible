# Ansible Playbook for Deploying TP-Link Omada SDN Controller

Playbook tested on following host distributions

* Ubuntu 18.04, 20.04
* Debian 12

## Instructions for Ubuntu 22.04 / Debian 12 

Manual instalation instructions for installing Omada SDN on Ubuntu 22.04 or Debian 12
https://blog.puvvadi.me/posts/omada-sdn-controller-ubuntu-22-04/

## Setup Ansible

* Install pip `sudo apt install python3-pip -y`
* install ansible with pip `pip install -i requirements.txt`

## Installed Packages

* `OpenJDK 8 Headless`
* `MongoDB 4.0`    -- Omada Supports 3.4 to 4.0
* `curl`
* `jsvc`
* `tar`

## Testing

Test the playbook before running it. You can use [geerlingguy](https://github.com/geerlingguy)'s Docker images such as `Debian 12` to test . 

- Clone the repo  `git clone https://github.com/kdpuvvadi/omada-ansible.git omada-ansible`.
- `cd omada-ansible`
- Pull docker image `docker pull geerlingguy/docker-debian12-ansible:latest`
- Run the container `docker run -d --privileged --name omada --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --volume ${PWD}:/var/omada:ro -p 8088:8088 -p 8043:8043 --cgroupns=host geerlingguy/docker-debian12-ansible:latest`
- Test the playbook with `docker exec --tty omada env TERM=xterm ansible-playbook /var/omada/main.yml`

if everything was executed as expected, you should be able to visit controller at `https://localhost:8043`. Now install omada controller on VM/VPS with ths playybook.

## Run

* Clone the repo  `git clone https://github.com/kdpuvvadi/omada-ansible.git omada-ansible`.
* Install requirements `ansible-galaxy collection install -r requirements.yml`.
* Inventory with `cp  inventory.ini.j2 inventory.ini`.
* Add IP and username of the server to the inventory.
* Variables with `cp vars.yml.j2 vars.yml`.

## Release

* For latest(5.13.30.8) [latest release](../../releases/v5.13.30.8)
* For version 5.13.22 [release 5.13.22](../../releases/v5.13.22)
* For version 5.12.7 [release 5.12.7](../../releases/v5.12.7)
* For version 5.9.31 [release 5.9.31](../../releases/v5.9.31)
* For verion 5.9.9 [release 5.9.9](../../releases/v5.9.9)
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

* Run `ansible-playbook main.yml`
* if you need password for `sudo` for root access on your host. `ansible-playbook main.yml -K`

## Post Install

* Omada controller will be available on `http://HOST-IP:8088/`  or `https://HOST-IP:8043/`.
* From v5.0.29 Adoption port has been changed to `29814/tcp`.

To work properly  ports `8088, 8043, 27001, 27002, 29810, 29811, 29812, 29813 and 29814` should be open.

## Omada Service on host

* `sudo tpeap status`     -- show the status of Controller;
* `sudo tpeap start`     -- start the Omada Controller;
* `sudo tpeap stop`     --stop running the Omada Controller.
