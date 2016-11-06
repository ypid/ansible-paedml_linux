## paedml_linux

<!-- This file was generated by Ansigenome. Do not edit this file directly but
     instead have a look at the files in the ./meta/ directory. -->

[![Travis CI](http://img.shields.io/travis/ypid/ansible-paedml_linux.svg?style=flat)](http://travis-ci.org/ypid/ansible-paedml_linux)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-ypid.paedml_linux-660198.svg?style=flat)](https://galaxy.ansible.com/ypid/paedml_linux)
[![Platforms](http://img.shields.io/badge/platforms-univention-lightgrey.svg?style=flat)](#)
[![GitHub Tags](https://img.shields.io/github/tag/ypid/ansible-paedml_linux.svg)](https://github.com/ypid/ansible-paedml_linux)
[![GitHub Stars](https://img.shields.io/github/stars/ypid/ansible-paedml_linux.svg)](https://github.com/ypid/ansible-paedml_linux)

### Warning, this is a Beta role

This role has been marked by the author as a beta role, which means that it
might be significantly changed in the future. Be careful while using this role
in a production environment.

***

Manage paedML Linux using Ansible

The `ypid.paedml_linux` role allows you to automate the deployment of a
[paedML Linux][] environment.

The role targets the two servers which are running [Univention Corporate Server][]
(which is based on Debian GNU/Linux).

To manage Opsi, there is a separate Ansible role which you are encouraged to
checkout called [ypid.opsi][].

[paedML Linux]: https://www.lmz-bw.de/technische-unterstuetzung/kundenportal/linux.html
[Univention Corporate Server]: https://en.wikipedia.org/wiki/Univention_Corporate_Server
[ypid.opsi]: https://github.com/ypid/ansible-opsi

### Installation

This role requires at least Ansible `v2.1.3`. To install it, run:

```Shell
ansible-galaxy install ypid.paedml_linux
```

To install via git, run either:

```Shell
git clone https://github.com/ypid/ansible-paedml_linux.git ypid.paedml_linux
git submodule add https://github.com/ypid/ansible-paedml_linux.git ypid.paedml_linux
```

### Documentation

More information about `ypid.paedml_linux` can be found in the
[official ypid.paedml_linux documentation](https://ypid-ansible-roles.readthedocs.io/en/latest/ansible/roles/ansible-paedml_linux/docs/).






### Authors and license

`paedml_linux` role was written by:

- [Robin Schneider](https://me.ypid.de/) | [e-mail](mailto:ypid@riseup.net) | [GitHub](https://github.com/ypid)

License: [AGPLv3](https://tldrlegal.com/license/gnu-affero-general-public-license-v3-%28agpl-3.0%29)

***

README generated by [Ansigenome](https://github.com/nickjj/ansigenome/).
