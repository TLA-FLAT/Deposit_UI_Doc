.. _owncloud:

=====
Setup
=====

#. Get packages
#. set rights of owncloud files to HTTP user
#. create owncloud database (on mysql or postgres server)
#. Use owncloud console as HTTP user (sudo -u www-data php /var/www/owncloud/occ)
#. Change rights of all files in folder as recommended on the site
#. Add domain through which owncloud can be assessed to the config.php file


===========================
OwnCloud Command line (OCC)
===========================
adding a user::

    sudo -u www-data php occ user:add --display-name="Daniel von Rhein" --group="users" --group="TLA" danrhe




=======
OC APIs
=======

`Ref <https://doc.owncloud.org/server/8.0/admin_manual/configuration_user/user_provisioning_api.html>`_

==========
References
==========

`Server manual <https://doc.owncloud.org/server/9.0/admin_manual/installation/index.html>`_
`owncloud console <https://doc.owncloud.org/server/9.0/admin_manual/configuration_server/occ_command.html#http-user-label>`_


.. todo::

https://doc.owncloud.org/server/8.0/admin_manual/configuration_files/files_locking_enabling.html

`developers api <https://github.com/owncloud/ocdev>`_

`git drupal repository <https://github.com/sshtmc/owncloud-user-drupal>`_

http://admin:admin@192.168.99.100/owncloud/ocs/v1.php/cloud/users?search=Frank
