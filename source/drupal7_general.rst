.. _drupal7_general:

****************
Drupal 7 General
****************

.. _resources-books:

-----
Books
-----

* `The programmer’s guide to drupal <http://proquest.tech.safaribooksonline.de/book/web-development/drupal/9781491911457>`_ by Jennifer Hodgon (also with a `git repository <https://github.com/oreillymedia/programmers_guide_to_drupal.git>`_)
* `Drupal 7 Development by Example <http://proquest.tech.safaribooksonline.de/book/web-development/drupal/9781849516808>`_ by Kurt Madel
* `Drupal 7 Module Development <http://proquest.tech.safaribooksonline.de/book/web-development/drupal/9781849511162>`_ by Matt Butcher
* Maybe interesting Drupal 7 Themes by Ric Shreves

----------
Hompepages
----------

* `Drupal Example Project <https://www.drupal.org/project/examples>`_ with a well documented `API <https://api.drupal.org/api/examples/7>`_
* `Site for evaluating drupal modules <https://simplytest.me/>`_

--------------
Useful Modules
--------------

* `Drupal Examples <https://www.drupal.org/project/examples>`_
* `Admin_menu <https://www.drupal.org/project/admin_menu>`_
* `Devel <https://www.drupal.org/project/devel>`_


.. _drupal7_module_building:


************************
Drupal 7 Module Building
************************

.. _resources-module-building:

* `Drupal 7 Custom Module Development <http://www.lynda.com/Drupal-tutorials/Drupal-7-Module-Development/110715-2.html>`_ with Jon Peck
* `Drupal 7 Essential Training <http://www.lynda.com/Drupal-7-tutorials/essential-training/73655-2.html>`_ with Tom Geller
* `Drupal 7: Reporting and Visualizing Data <http://www.lynda.com/Drupal-7-tutorials/Reporting-and-Visualizing-Data/85758-2.html>`_ with Tom Geller




.. _drupal7_cookbook:

***************
Drupal Receipes
***************

.. _rendered_page:

-------------
Rendered page
-------------

Make in your module an implementation of hook_menu, specifying the path of your page. Here you can define a function call (e.g. page_call_info()), specifying what and how to render::

    # Item of hook_menu
    $items['commitchanges'] = array(
        'title' => 'Commit changes',
        'page callback' => 'flat_deposit_ui_view_info',
        'access callback' => TRUE,
        'page arguments' => array(
            'content' => 'Under construction'),




.. _drupal7_theming:


****************
Drupal 7 Theming
****************

Theming is one of the major issues of the drupal framework, particular if you think of this framework as a gigantic wrapper.
For sure, Drupal does much more than that, but in the end, what you see is a in HTML-rendered homepage, so it is good to know something about rendering

.. _render_arrays:

*************
Render arrays
*************

Render arrays are arrays containing fields that are used to render different content. The most basis type is the markup type, containing with hard coded content.
You can specify the output as it is shown on a HTML-page. ::

    'link_upload' => array(
            '#type' => 'markup',
            '#prefix' => '<div>',
            '#markup' => '<a href="/drupal/user/' . $GLOBALS['user']->uid  . '/imce" title="Upload data"><img title="Upload data" alt="Upload data" src="/drupal/sites/default/files/Upload.png"/></a><br/>',
            '#suffix' => </div>')


But there are also a lot of other types. Depending on the type of element which needs to be rendered (e.g. tables) these may have an theme function that can be called to wrap the content of the array
in a certain format. An overview of all available functions are `here <https://api.drupal.org/api/drupal/modules!system!theme.api.php/group/themeable/7>`_

Videos (google render arrays drupal 7 tutorial):

* `Themes tutorial <https://www.youtube.com/watch?v=oRnXLXFjNdo)>`_ by Heather James
* `Drupal 7 renderable arrays <https://www.youtube.com/watch?v=zizupA-PWZY>`_ by Code Carate

Pages:

* `Themery.com <http://themery.com/dgd7>`_

Books:



all the resources mentioned here :ref:`resources-books`)


********
Form API
********

The form api is an important means to interact with the user. You can define for example action buttons and use them to trigger certain events.
Normally, this procedure involves several steps.

#. Create a function containing your form
#. Call this form from your menu
#. Create an additional form_validate function
#. Create a form_submit function


Resources:

* `Form API reference <https://api.drupal.org/api/drupal/developer%21topics%21forms_api_reference.html/7>`_
