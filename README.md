# Ansible role: php

An [Ansible](https://www.ansible.com/) role that installs and configures php.

This role is designed for Ubuntu 16.04 Xenial.

## Requirements

This role requires `root` access so be sure to enable privilege escalation:

```
# privilege escalation of play
- hosts: webservers
  become: true
  roles:
    -role: php

# escalation of single role only
- hosts: webservers
  roles:
    - role: php
      become: true
```

## Role Variables


## Dependencies

None.

## Example Playbook

```
---
- hosts: webservers
  become: true
  vars_files:
    - vars/main.yml
  roles:
    - { role: php }
```

Inside `vars/main.yml`:

```
---
```

## Installation

On the command-line:
```
$ ansible-galaxy install git+https://github.com/jodyboucher/ansible-role-php.git
```

or in a role file (requirements.yml):

```
- name: php
  src: https://github.com/jodyboucher/ansible-role-php
  version: master
```

## License

MIT

## Author Information

This role was created by [Jody Boucher](https://jodyboucher.com/).
