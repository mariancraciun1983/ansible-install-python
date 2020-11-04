<h1 align="center">Python Installer Ansible Role</h1>
<br />

<div align="center">
  <a href="https://travis-ci.org/mariancraciun1983/ansible-install-python">
    <img src="https://travis-ci.org/mariancraciun1983/ansible-install-python.svg?branch=master" alt="Build Status" />
  </a>
  <a href="https://galaxy.ansible.com/mariancraciun1983/ansible-hetzner-installimage">
    <img src="https://img.shields.io/ansible/role/51632" alt="Ansible Galaxy" />
  </a>
  <a href="https://galaxy.ansible.com/mariancraciun1983/ansible-hetzner-installimage">
    <img src="https://img.shields.io/ansible/quality/51632" alt="Ansible Quality Score" />
  </a>
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License" />
  </a>
</div>

<br />

Ansible role for installing python 2 or 3 on the remote host.


## Introduction

If python is not installed on the host, most of Ansible's functionality and modules aren't available. For example modules like yum, apt and set_fact rely on python being already installed. This module takes advantage of the raw module to detect and install python.

### Ansible
This role was tested against Ansible version 2.7 2.8 2.9 2.10 .
The supported platforms are
  - Debian
    - buster
    - stretch
  - Ubuntu
    - focal
    - bionic
    - xenial
  - Centos
    - 8
    - 7

## Variables
There is only one variable called `install_python_package`:
```yaml
install_python_package: python3
```

For python2 however, since the package names vary, the following are suggested:
```yml
group_vars:
  all:
    install_python_package: python2
host_vars:
  stretch:
    install_python_package: python
  bionic:
    install_python_package: python
  xenial:
    install_python_package: python
```

## Example
```ini
# inventory
[servers]
focal.example.com install_python_package=python2
stretch.example.com install_python_package=python
```

```yaml
# playbook.yml
- hosts: servers
  roles:
    - mariancraciun1983.install_python
```

```bash
# install the role
ansible-galaxy install mariancraciun1983.install_python
```

```bash
# run the playbook
ansible-playbook -i inventory playbook.yml
```

## License
MIT License