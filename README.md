# php

## Description
Ansible role to install and configure php.

## Example Playbook
```YAML
---
- name: PHP
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: bubebyte.php
```

## Role Variables
These are the role default which are set in default/main.yml:
```YAML
---
php_install_epel_repository: true
php_install_remi_repository: true
php_extra_packages: []
php_fpm_enable: true
php_fpm_pools:
  - name: www
    options:
      user: apache
      group: apache
      listen: /var/run/php-fpm/www.sock
      listen.mode: "0660"
      listen.acl_users: apache
      listen.allowed_clients: 127.0.0.1
      pm: dynamic
      pm.max_children: 50
      pm.start_servers: 5
      pm.min_spare_servers: 5
      pm.max_spare_servers: 35
      slowlog: "/var/log/php-fpm/www-slow.log"
      php_admin_value[error_log]: "/var/log/php-fpm/www-error.log"
      php_admin_flag[log_errors]: "on"
      php_value[session.save_handler]: files
      php_value[session.save_path]: /var/lib/php/session
      php_value[soap.wsdl_cache_dir]: /var/lib/php/wsdlcache
```

## Requirements

### Roles
none

### Collections
- community.general

## License
MIT License

## Author Information
[Armin Bube](https://bubebyte.de)
