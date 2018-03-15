.. _install_module:


************
Setup Module
************

.. _installing-docdir:

Installing the FLAT module
=============================

In principle, installing the module works as for every other module. Git clone repository to sites/all/modules/custom/<module_name>, log in as admin
(admin:admin) and then activate module. However, several extra modules are required:

* Drupal modules
    * `imce <https://www.drupal.org/project/imce>`_
    * `wysiwyg <https://www.drupal.org/project/wysiwyg>`_
    * `The imce_wysiwyg bridge <https://www.drupal.org/project/imce_wysiwyg>`_

* Libraries
    * a WYSIWYG editor (e.g. `CKEditor <http://ckeditor.com/download>`_) (side note: version 3.6.2 works with the current version)


All this software is added to the dockerfile **add-flat-ui** .



Drupal settings
===============

Following settings need to be done:

* Set CKEditor for
* Set IMCE


IMCE works with profiles. Here you can specify general settings per user type. Next to that you can specify a path for
private files. For now I will use the public accessible directory


workspaces/user%uid
    Check settings IMCE




.. todo::

    Set settings IMCE automatically
