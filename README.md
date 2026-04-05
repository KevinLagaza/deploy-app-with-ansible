# Deploy an app via Ansible

## Getting started

.

## Prerequisites

- 1) Create an **AWS account** if not done yet.
- 2) Create an EC2 VM, then install both **Docker** and **Ansible** on the machine.

**![Installation of prerequisites](./imgs/ansible-and-docker-install.png)**

- 3) Create two EC2 VMs for both staging and production environments.
- 4) Create a key-pai to allow communication between both staging and production environments.

## Part 1: Deploy the app with a simple playbook file

Note that we will be using the app-init folder.