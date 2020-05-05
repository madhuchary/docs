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
* handlers - handlers are called by notify module when there is a change is state.
* defaults - default variables for the role
* vars - other variables for the role 
* files - contains static files like images, executable files, packages ...
* templates - Dynamic content is stored in templates.
* meta - defines some metadata for this role.

