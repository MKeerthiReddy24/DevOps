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



