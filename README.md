redops.varnish
=============

Provision a varnish server with nginx reverse proxy.

Role Variables
--------------
 - server_name (Domain Name System) of the target website (required)
 - backend_host ip address of the backend web server (required)
 - backend_port port of the backend web server (required)
 - mem_size memory allocation size for varnish runtime (required)

Example Playbook
----------------
Example Playbook for varnish provisioning behind the nginx proxy:
```
    - hosts: Ubuntu_Server_Focal
      gather_facts: yes
      become: yes
      vars:
        server_name: goadminops.com
        backend_host: 192.168.0.1
        backend_port: 80
        mem_size: 1GB
      roles:
         - redops.varnish
      ignore_errors: '{{ ansible_check_mode }}'
```
Execution
----------
```
ansible-playbook -i inventories.ini main.yml -f 1 --diff -vv
```

For provisioning only with existing nginx and varnish
------------------------------------------------------
```
ansible-playbook -i inventories.ini main.yml -f 1 --diff -vv --skip-tag installation
```
License
-------

BSD

Author Information
------------------

Name: Alfred Valderrama
Email: alfred98valderrama@gmail.com
Github Repository: https://github.com/redopsbay
Website: https://goadminops.com