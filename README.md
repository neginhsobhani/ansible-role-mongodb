# Ansible role to install and setup mongodb cluster with 3 nodes
This ansible role installs version 7.0.1 of mongo_org package by default and is customized for this version.
The cluster should have exactly one primary node, at least one and at most two seconderies and at most one arbiter. 

## Mongodb cluster with three nodes
This ansible role installs version 7.0.1 of mongo_org package by default and is customized for this version.


### Example Playbook & Inventory

--------------

playbook.yaml:

```yaml playbook.yaml
- name: mongodb-cluster-setup
  hosts: all
  become: true
  become_user: root
  roles:
    - mongodb
```
inventory.yaml: 

```yaml inventory.yaml
mongod:
  hosts:
    mongo0:
      ansible_host: 172.16.21.11
      mongo_replication_role: primary
      mongo_arbiter: false
      
    mongo1:
      ansible_host: 172.16.21.12
      mongo_replication_role: secondary
      mongo_arbiter: false
      
    mongo2:
      ansible_host: 172.16.21.13
      mongo_replication_role: secondary
      mongo_arbiter: false
      
  vars:
    ansible_user: root
    ansible_connection: ssh
    ansible_ssh_port: 22
```
