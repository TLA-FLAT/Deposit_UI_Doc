.. _script_ingest:


*************
Script Ingest
*************

.. _prepare_script_ingest:

------------
The pipeline
------------

De Hocank data is op verschillende MPI servers gemount, e.g., ssh.mpi.nl

.. code-block:: bash

    scp danrhe@ssh.mpi.nl:/home/menwin/tmp/hocank-data.tgz .
    tar xvfz /home/menwin/tmp/hocank-data.tgz

Je kunt de docker container opstarten met de Hocank data gemount

.. code-block:: bash

	docker run -p 80:80 -p 8443:8443 -v ../../hocank-data/:/lat -t -i flat

In de container bevindt je je direct in de /app/flat directory. Voer daar
de volgende commando’s uit

.. code-block:: bash

	mkdir src
	cd src
	ln -s /lat/Hocank .
	cd ..
	ln -s /lat/imdi-to-skip.txt .
	./do-0-convert.sh  # create empty directory structure resembling the origin; create cmdi meta data files in directory Metadata directory
	./do-1-fox.sh # create FOXML files for each specific file
	./do-2-import.sh # java script to ingest data based on FOXML file
	./do-3-config-cmd-gsearch.sh
	./do-4-index.sh

Nu kun je naar je browser en in FLAT grasduinen:

* http://192.168.99.100/drupal

De default login is:

* admin/admin


-----------------
Structure of CMDI
-----------------

In the CMDI file, you define the structure of your project. Thus, there is one CMDI per project/measure.
When ingesting a project, for all files plus the metadata files FOXML objects are created and ingested.

The structure of each CMDI is as follows


Header:
here you define the ID of your metadata file and maybe other important things.

.. code-block:: xml

    <MdCreator> I don"t know </MdCreator>
    <MdCreationDate>2007-11-26</MdCreationDate>
    <MdSelfLink> The part following the colon will become the PID (slash and score will become underscore </MdSelfLink>
    <MdProfile>clarin.eu:cr1:p_1407745712035</MdProfile>



Resources:
Here you specify the files associated with the meta file. Make sure to specify both resource and metadata file.

.. code-block:: xml

    <ResourceProxy id="d333e522"> //this id needs to be unique and will be used later on
        <ResourceType mimetype="audio/x-mpeg3">Resource</ResourceType> //important to render the file in the correct way
        <ResourceRef lat:localURI="/path/to/File.mp3">hdl:use-unique-PID</ResourceRef>
    <ResourceProxy id="landingpage"> //don|t know if the specific id name is necessary to qualify meta data files
        <ResourceType>LandingPage</ResourceType> //same is true for type and ref
        <ResourceRef>hdl:1839/00-0000-0000-0016-7DE4-4</ResourceRef>



We can customize a CMDI file and generate a FOXML file from it. Therefore, we need to link the users workspace in the
/app/flat/src directory and then run the scripts as indicated above.





In order to see the data on the fedora server, we need to change a parameter in our native fedora config file (/var/www/fedora/server/config/fedora.fcfg)::

    <param name="ENFORCE-MODE" value="permit-all-requests"/>


And, of course, restart the fedora server::

    /var/www/fedora/tomcat/bin/tomcat-fedora.sh start

