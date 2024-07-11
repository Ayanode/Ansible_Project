# Ansible_Project

## Creation 

Create an Ansible project to provision 2 Ubuntu and 1 Debian instances on AWS using the free tier, utilizing passwordless authentication via IAM.

## Setup

### Prerequisites

- Ansible installed locally
- Python installed on the local machine
- AWS IAM user with programmatic access and appropriate permissions

### Installing Dependencies

Install the following dependencies using pip:

```sh
pip install boto3
ansible-galaxy collection install amazon.aws

```
### Creating of Vault

```sh
openssl rand -base64 2048 > vault.pass
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass

```
### Running of Playbook
```sh
ansible-playbook -i inventory.ini ec2_create.yaml --vault-password-file vault.pass

```
### Passwordless authentication using ssh
```sh
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>

```

### Shutdown of ubuntu instance using when command

