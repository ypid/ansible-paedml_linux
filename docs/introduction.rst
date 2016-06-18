Introduction
============

.. include:: includes/all.rst

The ``ypid.paedml_linux`` role allows you to automate the deployment of a
`paedML Linux`_ environment.

The role targets the two servers which are running `Univention
Corporate Server`_ (which is based on Debian_ GNU_/Linux_).

To manage Opsi, there is a separate Ansible role which you are encouraged to
checkout called `ypid.opsi`_.


Short overview of IT school solutions
-------------------------------------

``paedML Windows``
  Based on `Microsoft Windows`_ servers and clients.

.. _paedml_linux__section_item_paedml_linux:

``paedML Linux (>= 6.0)``
  Based on GNU_/Linux_, FreeBSD_ servers and `Microsoft Windows`_ clients.
  Although it has the word Linux_ in the name (where is the GNU_ btw ;)? ), this solution does not really
  allow to run GNU_/Linux_ on clients which is a shame and can be confusing.
  TODO: There is a way to install Debian 8 using Opsi, configure it with
  Ansible and then deploy it to clients using Opsi capture. This needs to be
  checked out :)

``linuxmuster.net``
  Was called ``paedML Linux`` up until 5.1. Then it was decided to let
  the project die and develop something new (refer to :ref:`paedML Linux
  <paedml_linux__section_item_paedml_linux>`).
  Luckily, the project is quite alive and being lead by the original developer
  team and the community. If you want to support GNU_/Linux_ and `Microsoft
  Windows`_ clients then checkout `linuxmuster.net`_.

  The author of this Ansible role has written several roles to manage
  `linuxmuster.net`_ environments too.
  See `Erfahrungsbericht Epoptes Einrichtung/Ansible
  <https://mail.lehrerpost.de/pipermail/linuxmuster-user/2015-July/007093.html>`_
  (language: German).

For more details, checkout: `Vergleich der Musterlösungen: Linux - Windows - Novell <https://www.linuxmuster.net/wiki/anwenderwiki:vergleichdermusterloesungen>`_ (language: German).

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
  Targeted by this role and by `ypid.opsi`_.

``adminvm``
  `Microsoft Windows 7`_ server for various management tasks.
  Not yet targeted by this role.

``firewall``
  Based on `PfSense`_. Not yet targeted by this role.


Installation
------------

This role requires at least Ansible ``v1.9.0``. To install it, run::

    ansible-galaxy install ypid.paedml_linux

..
 Local Variables:
 mode: rst
 ispell-local-dictionary: "american"
 End:
