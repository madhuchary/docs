---
id: playbooks
title: Ansible Playbooks
---
Playbooks are a YAML definition of automation tasks that describe how a particular piece of automation should be done. 

Ansible performs automation and orchestration of IT environments via Playbooks. 

Each ‘play’ consists of multiple ‘tasks,’ that can target one, many, or all of the hosts in the inventory

Each task is a module which is written in python and stored in /usr/lib/python2.7/dist-packages/ansible/modules

For more info on modules click [here](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)
