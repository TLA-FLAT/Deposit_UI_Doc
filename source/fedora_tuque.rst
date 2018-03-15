.. _fedora:

===================
Fedora /Tuque Links
===================

`Tuque <https://github.com/Islandora/islandora/wiki/Working-With-Fedora-Objects-Programmatically-Via-Tuque#common-predicate-uris>`_
`Fedora REST API <https://wiki.duraspace.org/display/FEDORA38/REST+API>`_



---------------------
Fedora metadata query
---------------------

Fedora meta data can be queried in two different way, either using the SPARQL or iTQL query language. iTQL is more in the MySQL fashion, but
the Islandora programmers prefer the SPARQL language. There is a interface on the fedora server, which can be reached by entering <fedora_host>/risearch.

There you can play with the queries and test them before they you implement them. Here are two example queries

SPARQL::

    PREFIX fm: <info:fedora/fedora-system:def/model#>
    PREFIX fv: <info:fedora/fedora-system:def/view#>
    SELECT ?label ?created FROM <#ri>
    WHERE {
    ?object <http://purl.org/dc/elements/1.1/identifier> ?pid.
    ?object fm:state fm:Active.
    ?object fm:label ?label.
    ?object fm:createdDate ?created.
    ?object fm:ownerId 'admin'.
    ?object fv:disseminates ?dis
    Filter REGEX (STR(?dis),'OBJ')
    }




iTQL::

    SELECT $object $created from <#ri>
    WHERE  $object <info:fedora/fedora-system:def/model#hasModel> <info:fedora/islandora:sp_cmdiCModel>
    AND <info:fedora/fedora-system:def/model#createdDate> $created



Useful links for this resource:

* `Fedora Research index <https://wiki.duraspace.org/display/FEDORA36/Resource+Index+Search>`_
* `Islandora Tuque documentation <https://github.com/Islandora/islandora/wiki/Working-With-Fedora-Objects-Programmatically-Via-Tuque#using-the-resource-index>`_
* `Sparql tutorial <http://rdf.myexperiment.org/howtosparql?>`_
* `W3.org sparql site <https://www.w3.org/TR/rdf-sparql-query/>`_
* linkedin spreadsheets

===============
API-A and API-M
===============

Retrieval and modification of data/info stored on the fedora server is quite easy using tuque. For reading actions the API-A has been programmed, for writing the API-M.
All actions are stored in methods that are bound to fedora object classes. Here are two examples for running a simple query (A) and changing the ownership of a file (M)::

    $tuque = islandora_get_tuque_connection();
    #API-A
    $api_a = $tuque->repository->api->a;
    $condition = "ownerId=" . $GLOBALS['user']->name;
    $results =  $api_a->findObjects('query',$condition);

    #API-A
    $api_m = $tuque->repository->api->m;
    $pid = $result2['pid'];
    $commit = $api_m->modifyObject($pid, array('ownerId' => 'admin', 'logMessage' => 'Daniels api-m test' ));

