ansible-role-ferm-route-lxc-through-host-tor
=====

This role configures [ferm](http://ferm.foo-projects.org/) and [tor](https://www.torproject.org/) to route [lxc](https://linuxcontainers.org/) containers (or virtual machines using a bridge interface) traffic to the Internet through Tor. 
This role has only been tested in Debian.

Requirements
------------

This role requires Ansible 1.6 or higher.


Role Variables
--------------

All these variables are defined in vars/main.yml and will be used by default.

    ## for lxc-create-container
    bridge_name: "lxcbr0"
    bridge_network: 172.16.0.0
    bridge_cidr: 24
    bridge_address: 172.16.0.1
    bridge_netmask: 255.255.255.0


Dependencies
------------

The following roles are needed:
* ansible-role-tor-basic
* ansible-role-ferm-basic
* ansible-role-ferm-tor

It's not needed to setup any arguments.

Example Playbook
----------

```
- hosts: localhost

  roles:

    - { role: ansible-role-tor-basic
      }
    - { role: ansible-role-ferm-basic
      }
    - { role: ansible-role-ferm-tor
      }
    - { role: ansible-role-ferm-route-lxc-through-host-tor
      }
```

License
-------

GPLv3

Author Information
------------------

Lee Woboo

