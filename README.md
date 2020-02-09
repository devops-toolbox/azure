Role Name
=========

azure: Azure

[![Build Status](https://travis-ci.org/cmihai-ansible/azure.svg?branch=master)](https://travis-ci.org/cmihai-ansible/azure)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.azure](https://galaxy.ansible.com/devopstoolbox.azure)

```bash
ansible-galaxy install devopstoolbox.azure
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
azure_packages_state: present
azure_remove_packages: true
azure_enable_service: true
azure_enable_selinux: true
azure_copy_templates: true
azure_firewall_configure: true
azure_firewall_rules:
  - service: ssh
  - port: 3389
azure_users:
  - user: devops
    group: docker
azure_selinux_booleans:
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
- name: Install azure on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: azure is configured
      import_role:
        name: devopstoolbox.azure
      vars:
        azure_packages_state: present
        azure_remove_packages: true
        azure_enable_service: true
        azure_enable_selinux: true
        azure_copy_templates: true
        azure_firewall_configure: true
        azure_firewall_rules:
          - service: ssh
          - port: 3389
        azure_users:
          - user: devops
            group: docker
        azure_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: azure
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
