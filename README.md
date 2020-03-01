# libvirt-exporter
=========
[![Build Status](https://travis-ci.org/patrickjahns/ansible-role-libvirt-exporter.svg?branch=master)](https://travis-ci.org/patrickjahns/ansible-role-libvirt-exporter)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-patrickjahns.libvirt_exporter-blue.svg)](https://galaxy.ansible.com/patrickjahns/libvirt_exporter)
[![GitHub tag](https://img.shields.io/github/tag/patrickjahns/ansible-role-libvirt-exporter.svg)](https://github.com/patrickjahns/ansible-role-libvirt-exporter/tags)

A ansible role that installs and configures [libvirt-prometheus-exporter](https://github.com/patrickjahns/libvirt-prometheus-exporter) as system service

## Requirements

None.

## Role Variables

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


## Dependencies

None.

## Example Playbook

```
- hosts: all
  roles:
    - role: patrickjahns.libvirt_exporter
      vars:
        libvirt_exporter_system_group: libvirt
        libvirt_exporter_system_user: libvirt-exp
```

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/metacloud/molecule) (v3.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system.
We are using tox to simplify process of testing on multiple ansible versions. To install tox execute:
```sh
pip3 install tox
```
To run tests on all ansible versions (WARNING: this can take some time)
```sh
tox
```
To run a custom molecule command on custom environment with only default test scenario:
```sh
tox -e ansible29 -- molecule test -s default
```
For more information about molecule go to their [docs](http://molecule.readthedocs.io/en/latest/).

If you would like to run tests on remote docker host just specify `DOCKER_HOST` variable before running tox tests.

## Travis CI

Combining molecule and travis CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which will take more time than local testing, so please be patient.


## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.

## Maintainers and Contributors

- [Patrick Jahns](https://github.com/patrickjahns)

