Ansible Role NGINX
=========

Ansible role allows to manage nginx on ubuntu / debian server


Role Variables
--------------
```yaml
---
# defaults file for nginx
nginx_user_group: www-data
nginx_worker_processes: "1"
nginx_worker_connections: "1024"
nginx_multi_accept: "off"

nginx_error_log: "/var/log/nginx/error.log warn"
nginx_access_log: "/var/log/nginx/access.log main buffer=16k"

nginx_vhosts_folder: /etc/nginx/conf.d

nginx_vhosts:
  - name: default
    listen_port: 80
    server_name: localhost
    access_log: /var/log/nginx/host.access.log  main
    locations:
      - name: root
        mask: /
        root: /usr/share/nginx/html
        file_index: index.html index.htm


nginx_upstreams: []
nginx_fpm_endpoint: unix:/var/run/php5-fpm.sock
os_distribution: ubuntu
os_distribution_release: trusty
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: all
  become: true
  roles:
     - { role: nginx }
```     


License
-------

Apache

Author Information
------------------

Aleksandr Ivanov (avic.ivanov@gmail.com)