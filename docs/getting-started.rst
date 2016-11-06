Getting started
===============

.. contents::
   :local:

.. include:: includes/all.rst


.. _paedml_linux__section_paedml_linux_servers:

paedML Linux servers
--------------------

``main``
  The "main" server has by default the hostname "server".
  It is responsible for the following services: DNS, DHCP, LDAP, print server
  and providing user profiles and network file shares.
  Targeted by this role.

``opsi``
  The "opsi" server has by default the hostname "backup".
  It is responsible for software distribution and management system using
  Opsi_.
  Targeted by this role and by ypid.opsi_.

``adminvm``
  `Microsoft Windows 7`_ server for various management tasks.
  Not yet targeted by this role.

``firewall``
  Based on `PfSense`_. Not yet targeted by this role.


Example inventory
-----------------

To run the role on both servers, you can add them either directly to the
``ypid_service_paedml_linux`` Ansible inventory group:

.. code:: ini

   [debops_service_paedml_linux_setup]
   server.paedml-linux.lokal
   backup.paedml-linux.lokal

Or use a slightly more flexible approach like this:

.. code:: ini

   [paedml_linux:children]
   ypid_service_paedml_linux

   [paedml_linux_server_main]
   server.paedml-linux.lokal

   [paedml_linux_server_opsi]
   backup.paedml-linux.lokal

   [ypid_service_paedml_linux:children]
   paedml_linux_server_main
   paedml_linux_server_opsi

   ## In case you also want to run the `ypid.opsi` role.
   # [ypid_service_opsi:children]
   # paedml_linux_server_opsi

Note that you will need to use unique hostnames if you intent to manage more
than one `paedML Linux`_ environment.
ypid is wondering if the LMZ_ does support that :)

Example playbook
----------------

Here's an example playbook that uses the ``ypid.paedml_linux`` role:

.. literalinclude:: playbooks/paedml_linux.yml
   :language: yaml

The playbooks is shipped with this role under
:file:`docs/playbooks/paedml_linux.yml` from which you can symlink it to your
playbook directory.
In case you use multiple roles maintained by ypid_, consider
using the `ypid-ansible-common`_.

Ansible tags
------------

You can use Ansible ``--tags`` or ``--skip-tags`` parameters to limit what
tasks are performed during Ansible run. This can be used after a host was first
configured to speed up playbook execution, when you are sure that most of the
configuration is already in the desired state.

Available role tags:

``role::paedml_linux``
  Main role tag, should be used in the playbook to execute all of the role
  tasks as well as role dependencies.

``role::paedml_linux:pkgs``
  Tasks related to system package management like installing, upgrading or
  removing packages.
