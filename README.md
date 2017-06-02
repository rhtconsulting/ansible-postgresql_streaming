# ansible-postgresql_streaming_replication
This project can be used to setup streaming replication between two existing PostgreSQL servers.

Useful if setting up streaming replication between Ansible Tower PostgreSQL servers.

# Use
`ansible-playbook playbooks/postgresql_streaming_replication.yml -i INVENTORY`

# Required Inventory
Informationa bout the inveotry required to use this playbook.

## Groups
Groups required to be in the inventory.

* `[postgresql]`
  * must have 2 hosts
  * first host will be made primary
  * secondy host will be made secondary

## Varaiables

* `postgresql_replicator_user`     - User to create and use for replication.
* `postgresql_replicator_password` - User password to use for replication.

## Example
```
[postgresql]
postgresql-1 ansible_host=postgresql-1.example.com
postgresql-2 ansible_host=postgresql-2.example.com

[postgresql:vars]
postgresql_replicator_user=replicator
postgresql_replicator_password=secret1!
```

# Assumptions

* PostgreSQL 9.4 is already installed on all hosts.
* PostgreSQL user is `postgres`
