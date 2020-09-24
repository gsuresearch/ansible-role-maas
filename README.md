Ansible MAAS Role
=========

An [Ansible] role to install/configure [MAAS].

Requirements
------------

None

Role Variables
--------------

```
---
# defaults file for ansible-maas
maas_adminusers:
  - username: 'root'
    email: 'admin@{{ maas_dns_domain }}'
    password: 'r00tm3'
maas_dns_domain: 'vagrant.local'
maas_region_controller: '192.168.250.10'
maas_region_controller_url: 'http://{{ maas_region_controller }}:5240/MAAS'
maas_repo: 'ppa:maas/stable'

# Defines if maas user should generate ssh keys
# Usable for remote KVM/libvirt power actions
maas_setup_user: false

maas_single_node_install: true
```

Dependencies
------------

Other roles are needed in order to run this playbook and they are listed below. A test requirements file is inside this repo.

    -ansible-role-pip
    -ansible-role-maas
    -ansible-role-nginx
    -ansible-role-generic-ssl


Example Playbook
----------------

```
---
- hosts: maas
  vars:
  roles:
    - role: ansible-role-maas
  tasks:
```

Testing
----------------

This repo provides a Vagrant test file which will launch an Ubuntu instance and configure MAAS on it with a reverse Nginx proxy with ssl in the front of it as well as a PxeBoot node for testing MAAS.
KVM is required and the libvirt provider must used when testing this role. Run the command below to test this role using Vagrant:

	vagrant up --provider-libvirt

Open a browser on a machine with access to the same network as the Vagrant boxes and open the following url to use MAAS:

	https://vagrant-maas-ip:9999

License
-------

BSD

Author Information
------------------
Modified and extended by:

John Duckett
- jduckett@gsu.edu

Original Fork and Author:

Larry Smith Jr.
- [@mrlesmithjr]
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
- https://github.com/mrlesmithjr/ansible-maas

[@mrlesmithjr]: <https://www.twitter.com/mrlesmithjr>
[Ansible]: <https://www.ansible.com>
[MAAS]: <https://maas.io/>
