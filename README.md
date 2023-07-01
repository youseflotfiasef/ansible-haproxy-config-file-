
Installs high available Edalat-Proxy (Haproxy and Keepalived) on two instances.

Install ansible define edalat_proxies in hosts file:

```
startup_proxy:
  hosts:
    192.168.1.20


```
set roles Keepalived and Haproxy in Edalat-Proxy.yaml file:

Example Playbook
----------------

```
- hosts: startup_proxies
  become: true
  roles:
   - Haproxy
```

run playbook:

`ansible-playbook Edalat-Proxy.yaml`


Role Names
=========
```
Keepalived
Haproxy
```
Installs haproxy and keepalived as reverse proxy on two ubuntu servers for high availablity.

Requirements
------------
Two Clean instances of Ubuntu


Role Variables
--------------
Default Variables are at Haproxy/defaults/main.yaml that on default installs haproxy version 2.4 and they are:

```
haproxy:
  config_file_name: "haproxy-config"
  version: 2.4

```
Default Variables are at Keepalived/defaults/main.yaml that on default installs keepalived version 2.2.4 and they are:


```
keepalived_version: 2.2.4
keepalived_source_url: "http://www.keepalived.org/software/keepalived-{{ keepalived_version }}.tar.gz"
keepalived_install_dir: "/tmp/keepalived-{{ keepalived_version }}"
keepalived_conf_path: "/etc/keepalived/keepalived.conf"

```

Keepalived config file and systemd service file are at Keepalived/templates/ :

```
keepalived.conf.j2
keepalived.service.j2

```

Haproxy config file is at Haproxy/templates/ :

```
haproxy-config.cfg.j2
```



Variables for Keepalived are at Keepalived/vars/main.yaml and they are:

```
load_balancer:
  name: Edalat-lb
  floating_ip: "192.168.2.11"
  master_server_ip: "192.168.2.12"
  backup_server_ip: "192.168.2.13"
  keepalived_password: "Mm@123"

```

192.168.220.11 is set to be float ip that by default will be set on master server and if the master server or haproxy service on master server going down the float ip will be set on backup server and if the master server goes back online then the float ip will set on that server again.




SSL certificate files for all domains for haproxy are at Haproxy/files/ssl-certs/ and if you want to add any new certs put them in Haproxy/files/ssl-certs/ path. they are:

```


```


Dependencies
----
