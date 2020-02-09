Role Name
=========

postgresql: Postgresql

[![Build Status](https://travis-ci.org/cmihai-ansible/postgresql.svg?branch=master)](https://travis-ci.org/cmihai-ansible/postgresql)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.postgresql](https://galaxy.ansible.com/devopstoolbox.postgresql)

```bash
ansible-galaxy install devopstoolbox.postgresql
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
postgresql_packages_state: present
postgresql_remove_packages: true
postgresql_enable_service: true
postgresql_enable_selinux: true
postgresql_copy_templates: true
postgresql_firewall_configure: true
postgresql_firewall_rules:
  - service: ssh
  - port: 3389
postgresql_users:
  - user: devops
    group: docker
postgresql_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install postgresql on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: postgresql is configured
      import_role:
        name: devopstoolbox.postgresql
      vars:
        postgresql_packages_state: present
        postgresql_remove_packages: true
        postgresql_enable_service: true
        postgresql_enable_selinux: true
        postgresql_copy_templates: true
        postgresql_firewall_configure: true
        postgresql_firewall_rules:
          - service: ssh
          - port: 3389
        postgresql_users:
          - user: devops
            group: docker
        postgresql_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: postgresql
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
