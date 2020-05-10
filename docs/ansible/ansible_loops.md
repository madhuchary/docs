---
id: ansible_loops
title: Ansible Loops
---

## Loops

* Adding multiple users

```
- name: add several users
  user:
    name: "{{ item }}"
    state: present
    groups: "{{ item }}"
  loop:
     - apache
     - tomcat
     - docker
```

* Adding users in different groups

```
- name: add several users
  user:
    name: "{{ item.name }}"
    state: present
    groups: "{{ item.groups }}"
  loop:
    - { name: 'ubuntu', groups: 'docker' }
    - { name: 'apache', groups: 'nogroup' }
```
