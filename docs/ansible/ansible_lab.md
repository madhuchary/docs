---
id: ansible_lab
title: Installing and configuring ansible
---
## In our lab we will install one master and two nodes
* Master: Ubuntu
* Nodes: One RedHat and One Ubuntu

## Master steps
Step 1. Install ansible 

```bash
sudo apt update
sudo apt install software-properties-common -y
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y
```
Installation document for other OS click [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu)

Step 2. Generate ssh keys and add to nodes authorized_keys file for passwor less connection

```
ssh-keygen -q -t rsa -N '' -f ansible_key
```
output:
ansible_key
ansible_key.pub

Step 3. Add ansible keys to agent (By default ssh reads ~/.ssh/id_rsa to override use below commands)

```bash
eval `ssh-agent`
ssh-add ansible_key
```
Step 4. Copy the output of ansible_key.pub and append to remote ~/.ssh/authorized_keys file 

```bash
cat ansible_key.pub 
```
Check the connectivity to nodes from master, it should not ask for password


## Node steps
Disable sudo password in all nodes

change user with system username

```
sudo cp /etc/sudoers /etc/sudoers.bak
vi /etc/sudoers

user ALL=(ALL) NOPASSWD:ALL
```
