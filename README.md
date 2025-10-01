dns
===

Configure DNS setup for a Linux server.

Uses `systemd-resolved` or `network-manager` if installed, else it removes `resolvconf` package and configures `/etc/resolv.conf` directly.


Version
-------

* `3.1.0` --- Added support for RHEL10. The role now supports os_family = redhat.
* `3.0.1` --- Changed testing to Ansible Molecule
* `3.0.0` --- Updated for ansible-core 2.16. Removed support for Ubuntu Xenial and Ubuntu Bionic.
* `2.2.0` --- Added support for Ubuntu 24.04
* `2.1.2` --- allow Fedora CoreOS 39
* `2.1.1` --- bug fix, ansible-lint
* `2.1.0` --- Initial support for Fedora CoreOS, but with no tests
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

This role supports

* RedHat Based OS, version 8, 9, 10
* Ubuntu 20.04, 22.04, and 24.04
* CentOS 7
* CentOS Stream 8
* Fedora CoreOS version 38, 39

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

Testing is done using Ansible Molecule. It uses Vagrant with libvirt as backend.

To run full test run:

```bash
molecule test
```

To run test step by step run:

```bash
molecule create
molecule converge
molecule verify
molecule destroy
```

To run toward specific scenario use `-s` option.
```
molecule test -s ubuntu
```

License
-------

GPLv2

Author Information
------------------

Created 2020 by IT Infrastructure at MET Norway

Contactpoint: [IT Infrastructure Basis Team](mailto:it-is-basis@met.no)

###### set vim: spell spelllang=en:
