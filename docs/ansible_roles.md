---
id: ansible_roles
title: Ansibel Roles
---
Ansible roles are structured way of organizing your playbooks and related files

Example of ansible webserver role
```
roles/
   webserer/
        tasks/
        handlers/
        files/
        templates/
        vars/
        defaults/
        meta/
```

## Roles path

Roles can be placed in roles folder in your current directory (relative path) ./roles/ or in /etc/ansible/roles folder

## Creating Roles

ansible-galaxy init rolename - To create a webserver role

``` 
ansible-galaxy init webserver
```

## Lets understand purpose of each folder

* tasks - contains the main list of tasks to be executed by the role.
* handlers - contains handlers, which may be used by this role or even anywhere outside this role.
* defaults - default variables for the role (see Using Variables for more information).
* vars - other variables for the role (see Using Variables for more information).
* files - contains files which can be deployed via this role.
* templates - contains templates which can be deployed via this role.
* meta - defines some meta data for this role. See below for more details.

