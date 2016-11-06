Additonal automation
====================

.. include:: includes/all.rst

What more can be automated using other Ansible roles?

* Opsi management using ypid.opsi_.

* Copying the documentation to the directory share of the teachers with debops.resources_.
  Example configuration:

  .. code:: yaml

     resources__group_files:

       - src: '/path/to/docs/dir/on/your/local/machine'
         dest: '/home/groups/klassen/lehrer-schule/'
         owner: 'Administrator'
         group: 'Domain Admins'
         mode: 'u=rwX,g=rwX,o=rX'
         # directory_mode: 'u=rwX,g=rwX,o=rwX'
