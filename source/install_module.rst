.. _install_module:


************
Setup Module
************

.. _installing-docdir:

Installing the FLAT module
=============================

In principle, installing the module works as for every other module. Git clone repository to sites/all/modules/custom/<module_name>, log in as admin
(admin:admin) and then activate module. However, several extra modules are required. An overview of all dependencies is listed in the moduleName.info file.

On install, hook_install (in myModule.install) and hook_enable (in myModule.module) is being called. If the name of the module is flat_deposit search for function `flat_deposit_install`.

The most important elements added by the base module are different field types, field instances, two node types (flat_bundle and flat_collections), that contain these field types and the modules variables.


For every field, a table is created in the drupal database with the name field_data_{fieldInstanceName}. Variables are saved as serialized string in th4e variables table


