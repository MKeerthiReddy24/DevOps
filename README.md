# **🚀 Ansible EC2 Automation Project**
## **📌 Overview**
This project automates AWS EC2 instance creation and stopping using Ansible playbooks.  
All AWS credentials are securely stored using Ansible Vault.

## Setup EC2 Collection and Authentication
### Install boto3
```bash
pip install boto3
```
### Install AWS Collection
``` bash
ansible-galaxy collection install amazon.aws
```
### Setup Vault
1. Create a password for vault
```bash
openssl rand -base64 2048 > vault.pass
```
2. Add your AWS credentials using the below vault command
``` bash
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

### Execute the ec2 create instances yml file to create instances
```bash
ansible-playbook ec2_create.yml --vault-password-file vault.pass
```
## Setup passwordless authentication to all the instances by using below command
```bash
ssh-copy-id -f "-o  IdentityFile <key-pair-path>" ubuntu@<public-ipaddress>
```

##### If you want to check instances  details about the managed node (the target machine) then you can use ansible_facts module
##### Create the inventory.ini which contains the hosts details i.e servers hosts here.
### Execute the ec2 stop instances yml file to stop the instances
```bash
ansible -i inventory.ini ec2_stop.yml --vault-password-file vault.pass
```



