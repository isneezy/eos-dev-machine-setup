# Elementary OS & Ubuntu dev machine setup

This repo contains Ansible playbooks to configure your system as a development machine upon a clean install. The playbooks should run in Debian based system but was only tested with Elementary OS 5.0

## Pre-requisites

On the system which you are going to setup using Ansible, perform these steps.

You need to install Ansible before running the playbooks. You can either install it using pip or though `apt`.

```bash
# install ansible
sudo apt install ansible
# clone/downlaod this repo
```

## Running the playbooks to configure your system

Invoke the following as yourself, the primary use. Not root.

```bash
ansible-playbook setup.yml -e "local_username=$USER" -K
```

## What gets installed and cofigured?

I am a Linux Systems Engineer and Software developer and my daily job include working with various config management using Ansible. So if you are in a similar profession the installed system will suit your needs. It is also easy to extend using Ansible roles.

Summary of packages that get installed and configured:

- Developer tools like awscli, docker, etc
- Firefox Web Browser
- Enable ufw firewall and configure for incoming ssh
- IDEs (PhpStorm)
- Languages and Framworks (NodeJs, Yarn, vue-cli, Php, Composer)
