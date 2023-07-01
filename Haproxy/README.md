
Installs haproxy and your configuration template on your ubuntu instance.
Install ansible define hosts that you want to install and set role in haproxy.yaml file.
Put all your haproxy properties in templates/haproxy-config.cfg.j2 and then run:

ansible-playbook  haproxy.yaml

Role Name
=========

Haproxy
Installs Haproxy and configures that.

Requirements
------------
A Clean instance of Ubuntu18.04


Role Variables
--------------
Variables are at vars/main.yaml and they are:

"config_file_name" : name of the config file (without .cfg.j2 part) that is in templates directory. default is "haproxy-config".

"version" : version number of haproxy package that would like to install default is "2.4.0-1ppa1~bionic".


Dependencies
------------


Example Playbook
----------------

- hosts: haproxy_server
  roles:
     - Haproxy


License
-------
BSD


Author Information
------------------

Azam Ahmadloo
