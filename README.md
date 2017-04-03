# Ansible role: php

[![Build Status](https://travis-ci.org/jodyboucher/ansible-role-php.svg?branch=master)](https://travis-ci.org/jodyboucher/ansible-role-php)

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

The available variables of this role are listed here along with default values:
```
# The PHP packages to install
php_packages:
  - libpcre3-dev
  - php7.0-cli
  - php7.0-common
  - php7.0-curl
  - php7.0-fpm
  - php7.0-gd
  - php7.0-json
  - php7.0-mbstring
  - php7.0-mcrypt
  - php7.0-mysql
  - php7.0-opcache
  - php7.0-readline
  - php7.0-xml
  - php7.0-xmlrpc

# The server APIs to configure
php_server_apis:
  - cli
  - fpm

# The path to the PHP configuration
php_conf_path: /etc/php/7.0

# The user/group used by the PHP-FPM pool
php_fpm_pool_user: "www-data"
php_fpm_pool_group: "www-data"

# Set to true if you're using PHP with a web server (Apache/Nginx/etc)
# Otherwise set to false
php_enable_webserver: true

# If using PHP with a web server, set to the name of the web server daemon
php_webserver_daemon: "nginx"

# PHP settings
# PHP.ini - Language Options
php_engine: "Off"
php_short_open_tag: "Off"
php_output_buffering: "4096"
php_disable_functions:
  - pcntl_alarm
  - pcntl_fork
  - pcntl_waitpid
  - pcntl_wait
  - pcntl_wifexited
  - pcntl_wifstopped
  - pcntl_wifsignaled
  - pcntl_wifcontinued
  - pcntl_wexitstatus
  - pcntl_wtermsig
  - pcntl_wstopsig
  - pcntl_signal
  - pcntl_signal_dispatch
  - pcntl_get_last_error
  - pcntl_strerror
  - pcntl_sigprocmask
  - pcntl_sigwaitinfo
  - pcntl_sigtimedwait
  - pcntl_exec
  - pcntl_getpriority
  - pcntl_setpriority
php_realpath_cache_size: "16K"

# PHP.ini - Miscellaneous
php_expose_php: "Off"

# PHP.ini - Resource Limits
php_max_execution_time: "30"
php_max_input_time: "60"
php_memory_limit: "128M"

# PHP.ini - Error handling and logging
php_error_reporting: "E_ALL & ~E_DEPRECATED & ~E_STRICT"
php_display_errors: "Off"
php_display_startup_errors: "Off"

# PHP.ini - Data Handling
php_post_max_size: "8M"

# PHP.ini - Paths and Directories
php_cgi_fix_pathinfo: "0"

# PHP.ini - File Uploads
php_file_uploads: "On"
php_upload_max_filesize: "4M"
php_max_file_uploads: "20"

# PHP.ini - Module Settings
php_date_timezone: "America/New_York"
php_session_save_handler: "files"
php_session_save_path: "/var/lib/php/sessions"

# PHP-FPM settings
php_fpm_pid: "/run/php/php7.0-fpm.pid"
php_fpm_error_log: "/var/log/php7.0-fpm.log"
php_fpm_pool_conf_path: "{{ php_conf_path }}/fpm/pool.d"
php_fpm_pool_name: "www"
php_fpm_listen: "/run/php/php7.0-fpm.sock"
php_fpm_pm_max_children: 5
php_fpm_pm_start_servers: 2
php_fpm_pm_min_spare_servers: 1
php_fpm_pm_max_spare_servers: 3

# OpCache settings.
php_opcache_conf_filename: 10-opcache.ini
php_opcache_zend_extension: "opcache.so"
php_opcache_enable: "1"
php_opcache_enable_cli: "0"
php_opcache_memory_consumption: "64"
php_opcache_interned_strings_buffer: "4"
php_opcache_max_accelerated_files: "4096"
php_opcache_max_wasted_percentage: "5"
php_opcache_validate_timestamps: "1"
php_opcache_revalidate_path: "0"
php_opcache_revalidate_freq: "120"
php_opcache_max_file_size: "0"
php_opcache_blacklist_filename: ""

```

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
