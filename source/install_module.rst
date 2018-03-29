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

The most important elements added by the base module are different field types, field instances, two node types (Bundles (machine name:flat_bundle) and Collection machine name: flat_collections)), that contain these field types and the modules variables.


For every field, a table is created in the drupal database with the name field_data_{fieldInstanceName}. Variables are saved as serialized string in the variables table


Fields for a Bundle are:
*   title:                  Node module element
*   flat_parent_nid:        Drupal node id (nid) of the parent collection
*   flat_policies
*   flat_cmdi_file          (managed) metadata file attached to bundle
*   flat_bundle_status      processing status of bundle
*   flat_exception          (deprecated) Text containining the error message of a failed upload
*   flat_parent_title       Name of the parent
*   flat_source             source for Resource files (external or local workspaces)
*   flat_original_path      path of the files on file system (uses stream wrappers)
*   flat_location           current location where files should be found
*   flat_external           (deprecated) info if file location is external
*   flat_type               kind of upload. Can be either completely new or update
*   flat_fid                the fedora commons ID associated with the bundle. If empty bundle is new.



Fields for a Collection are:
*   title:                  Node module element
*   flat_fid                the fedora commons ID associated with the collection. This is never empty as a collection is a kind of shortcut to a fedora commons object
*   flat_collection_status      processing status of bundle
*   flat_exception              (deprecated) Text containining the error message of a failed upload
*   flat_parent_nid             (deprecated) Drupal node id (nid) of the parent collection
*   flat_fid_super              Fedora commons ID of the parent of the collection (IsMemberOf property)




