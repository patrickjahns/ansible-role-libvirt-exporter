Role Name
=========
[![Build Status](https://travis-ci.org/patrickjahns/ansible-role-libvirt-exporter.svg?branch=master)](https://travis-ci.org/patrickjahns/ansible-role-libvirt-exporter)

A ansible role that installs and configures [libvirt-prometheus-exporter](https://github.com/patrickjahns/libvirt-prometheus-exporter) as system service

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):   
  
    
    
```
libvirt_exporter_version: 1.0.1
```
Install a specific version of libvirt-prometheus-exporter. Available versions are listered [here](https://github.com/patrickjahns/libvirt-prometheus-exporter/releases). 
  
  
  
```
libvirt_exporter_web_listen_address: "0.0.0.0:9233"
```

Address and port where the libvirt-prometheus-exporter service will listen on. 
  
  

```
libvirt_exporter_uri: "qemu:///system"
```
The qemu/libvirt connection string - please refer to the [official libvirt documentation](https://libvirt.org/uri.html) for possible values  
  
  
```
libvirt_exporter_system_group: "libvirt-exp"
libvirt_exporter_system_user: "{{ libvirt_exporter_system_group }}"
```

The user and group for the service. Please ensure that this group has access to libvirt socket if a local socket is used.


Dependencies
------------

None.

Example Playbook
----------------

```
- hosts: all
  roles:
    - role: patrickjahns.libvirt_exporter
      vars:
        libvirt_exporter_system_group: libvirt
        libvirt_exporter_system_user: libvirt-exp
```

License
-------

MIT / BSD

Author Information
------------------

This role was create in 2019 by [Patrick Jahns](http://github.com/patrickjahns)

