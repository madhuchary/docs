---
id: ansible_examples
title: Ansible By Example
---
## User Module Examples 
## Creating a user

```
---
- hosts:
  become: yes
  tasks:
    - name: Creating user
      user:
        name: rootedu
        state: present
```

## Creating user with password
### Passwords should be encrypted before using in playbook
### passwords can be encrypted using mkpasswd command or passlib
```
mkpasswd 12345678
J6TBr/jBb3iiY
```

```
--- 
- hosts:
  become: yes
  tasks:
    - name: Creating user
      user:
        name: rootedu
        state: present
        password: J6TBr/jBb3iiY
```

## Creating user and modifing user profile
```
---
- hosts:
  become: yes
  tasks:
    - name: Creating user
      user:
        name: rootedu
        state: present
        password: J6TBr/jBb3iiY
    - name: add env to you user madhu profile
      lineinfile:
              path: /home/rootedu/.profile
              insertafter: BOF
              line: 'export a=10'

```

## Installing a package

```
---
- hosts:
  become: yes
  tasks:
    - name: Installing a package
      package: 
        name: apahce2
```

## Installing a package in ubuntu

```
---
- hosts:
  become: yes
  tasks:
    - name: Installing a package
      apt: 
        name: apahce2
```

## Installing a package redhat

```
---
- hosts:
  become: yes
  tasks:
    - name: Installing a package
      yum: 
        name: apahce2
```

## Restart a service

```
---
- hosts:
  become: yes
  tasks:
    - name: Restarting service
      service:
        name: apache2
        state: restarted
```

##### Reference
###### Modules: [user](https://docs.ansible.com/ansible/latest/modules/user_module.html) | [lineinfile](https://docs.ansible.com/ansible/latest/modules/lineinfile_module.html) | [package](https://docs.ansible.com/ansible/latest/modules/package_module.html) | [service](https://docs.ansible.com/ansible/latest/modules/service_module.html) | [systemd](https://docs.ansible.com/ansible/latest/modules/systemd_module.html)
