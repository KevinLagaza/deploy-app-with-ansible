# Deploy an app via Ansible

## Getting started

.

## Prerequisites

- 1) Create an **AWS account** if not done yet.
- 2) Create a AWS key PEM to allow communication between the ansible instance and both staging and production servers.
- 3) Create an EC2 VM, then install both **Docker** and **Ansible** on the machine.

**![Installation of prerequisites](./imgs/ansible-and-docker-install.png)**

- 4) Create two EC2 VMs for both staging and production environments.

```bash
# Install sshpass
sudo apt update
sudo apt install sshpass
# Copy the AWS key PEM used
vi ~/.ssh/aws-key.pem
# Define the right permissions
chmod 400 ~/.ssh/aws-key.pem

# Définir les bonnes permissions
chmod 400 ~/.ssh/aws-key.pem
# Generate an SSH key (if not done yet)
ssh-keygen -t rsa -b 4096 -f ~/.ssh/ansible_key -N ""

# Copy the public key to the target servers
sshpass -p 'password_user' ssh-copy-id -o StrictHostKeyChecking=no -i ~/.ssh/ansible_key.pub user_ansible@<IP_STAGING>
sshpass -p 'password_user' ssh-copy-id -o StrictHostKeyChecking=no -i ~/.ssh/ansible_key.pub user_ansible@<IP_PRODUCTION>

# Test connectivity
ansible all -m ping
```

## Part 1: Deploy the app with a simple playbook file

Note that we will be using the app-init folder.