dns
===

Configure DNS setup for a Linux server.

Uses `systemd-resolved` or `network-manager` if installed, else it removes `resolvconf` package and configures `/etc/resolv.conf` directly.


Version
-------

* `2.0.1` --- bug fix, ansible-lint
* `2.0.0` --- updated for ansible 2.12.9
* `1.5.0` --- add RHEL9 + CentOS Stream 8 support
* `1.4.0` --- add jammy support + remove centos8 support
* `1.3.0` --- add rhel8 support + remove trusty and centos6
* `1.2.0` --- remove ubuntu precise from testing
* `1.1.1` --- fixed lint warnings
* `1.1.0` --- added ubuntu focal, 20.04
* `1.0.4` --- tested with Ansible 2.9.11
* `1.0.3` --- prepare for github
* `1.0.2` --- fixed always reload of network manger
* `1.0.1` --- fix run in `--check`
* `1.0.0` --- initial version
* `master` --- latest development version

Requirements
------------

This role is limited to:

* Ubuntu 16.04
* Ubuntu 18.04
* Ubuntu 20.04
* Ubuntu 22.04
* CentOS 7
* CentOS Stream 8
* RHEL 8
* RHEL 9

Role Variables
--------------

* `dns_servers` --- list of IPs for DNS servers, default `['8.8.8.8', '1.1.1.1']`
* `dns_dnssec` --- boolean value to enable DNSSEC, default `false`.
    DNSSEC is only configured for `systemd-resolved`.
* `dns_domains` --- list of search domains, default `[]`

Dependencies
------------

None

Example Playbook
----------------

Variables are kept in the `host_vars` or `group_vars` folder usually. Defining everything in playbook is not recommended. This is just an example.

    - hosts: servers
      vars:
      roles:
      - role: dns
        dns_servers:
          - 8.8.8.8
          - 1.1.1.1
        dns_dnssec: true
        dns_domains:
          - foo.lan
          - bar.lan


Testing
-------

Testing the role with Vagrant running on VirtualBox.

    cd tests
    vagrant up

Rerun tests.

    vagrant provision

Remove test VMs.

    vagrant destroy -f

License
-------

GPLv2

Author Information
------------------

Arnulf Heimsbakk <aheimsbakk@met.no>

###### set vim: spell spelllang=en:
