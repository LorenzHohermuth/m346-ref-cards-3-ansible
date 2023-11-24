# Ansible Project Ref Cards

Dises Projekt ist von der Berufsschule für das Modul 346 um einen Webserver und eine DB zu Konfigurieren

## Install Ansible

Run the following commands:

```bash
sudo apt update
sudo apt install ansible
```

## Generate SSH key

Run the following commands and follow the instructions (enter click through):

```bash
ssh-keygen
```

## Configure cloud init

-   Adjust name
-   Copy SSH key (in `.ssh` folder in root directory) and paste it into `cloud-init.yml`

## Setup 2 MaaS VMs

-   Visit https://maas.bbw-it.ch/maas-user.php
-   Start 2 VMs with the configured `cloud-init.yml`

## Insert VMs into hosts file

-   Open the `hosts` file
-   Replace the two `<ip>` values with the VMs IP's
-   Replace the two `<user>` values your configured user in `cloud-init.yml`

## Final steps

### Test the configuration and VM connection

```bash
ansible-inventory --graph
ansible -m ping all
```

> ⚠️ If the ping fails remember to activate the VPN connection

### Apply playbook

```bash
ansible-playbook db.yml
ansible-playbook spring.yml
```
