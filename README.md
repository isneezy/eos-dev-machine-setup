# Elementary OS & Ubuntu dev machine setup

This repo contains Ansible playbooks to configure your system as a development machine upon a clean install. The playbooks should run in Debian based system but was only tested with Elementary OS 5.1

## Pre-requisites

On the system which you are going to setup, perform the following steps.

You need to install Ansible before running the playbooks. You can either install it using pip or though `apt`.  
You need to sure you have at least ansible version 2.8.

```bash
# install ansible
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
# clone/downlaod this repo
```

## Running the playbook to configure your system

Before running the playbook and configure your system, update `group_vars/all/all.yml` file to suit your needs, by disabling things you don't want and enabling the ones you want.  
Don't forget to chnage `local_username` variable to your own username or pass it as env var `-e "local_username=$USER"` whe running the playbook.

Invoke the following commad as yourself, the primary user. Not root.
`ansible-playbook setup.yml` or `ansible-playbook setup.yml -e "local_username=$USER" -K` if you want to override the `local_username` variable in `group_vars/all/all.yml` file.

## What gets installed and cofigured?

I am a Linux Systems Engineer and Software developer and my daily job include working with various config management using Ansible. So if you are in a similar profession the installed system will suit your needs. It is also easy to extend using Ansible roles.

### Summary of packages that get installed and configured by default  

Every thing is optional and it can be chnaged in `group_vars/all/all.yml` file.

- Firefox Web Browser and removes Epiphany Browser if installed
- Enable ufw firewall and configure for incoming http & https connections only
- Gnome Disk Utility
- snapd
- Mailspring and removes pantheon-mail if installed **(Snapd required)**
- Git, GitKraken **(Snapd required)**
- IDEs (PhpStorm, IDEA Community/Ultimate)
- Languages and Framworks (NodeJs, Yarn, vue-cli, Php, Composer, OpenJDK)
- Developer tools like docker, pip, docker-compose, yarn, vue-cli
- Increase the amount of inotify watchers to 524288

## Issues and Todos

- You probably will have to run it twice because yarn command installation will fail with missing nodejs
- GitKraken icon missing https://forum.snapcraft.io/t/gitkraken-icon-missing/11276/12, I've installed AppEditor to fix it manualy
