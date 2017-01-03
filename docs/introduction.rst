Introduction
============

.. include:: includes/all.rst

The ``ypid.paedml_linux`` role allows you to automate the deployment of a
`paedML Linux`_ environment.

The role targets the two servers which are running `Univention
Corporate Server`_ (which is based on Debian_ GNU_/Linux_).

To manage Opsi, there is a separate Ansible role which you are encouraged to
checkout called ypid.opsi_.


Short overview of IT school solutions*
--------------------------------------

| * That ypid_ has worked with or that are otherwise common in Germany.

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
  Windows`_ clients then checkout linuxmuster.net_.

  The author of this Ansible role has written several roles to manage
  linuxmuster.net_ environments too.
  See `Erfahrungsbericht Epoptes Einrichtung/Ansible
  <https://mail.lehrerpost.de/pipermail/linuxmuster-user/2015-July/007093.html>`_
  (language: German).

For more details, checkout: `Vergleich der Musterlösungen: Linux - Windows - Novell <https://www.linuxmuster.net/wiki/anwenderwiki:vergleichdermusterloesungen>`_ (language: German).

Installation
------------

This role requires at least Ansible ``v2.1.3``. To install it, run::

    ansible-galaxy install ypid.paedml_linux

..
 Local Variables:
 mode: rst
 ispell-local-dictionary: "american"
 End:
