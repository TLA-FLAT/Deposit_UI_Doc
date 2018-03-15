.. _commandline_cheats:

******************
Commandline cheats
******************

1. Search folder for files with certain string in it::

    egrep -Ric --color $str $folder


2. Access postgres database interactive shell / export data::

    pg_dump -U fedora -W -h localhost -d postgres -f /lat/dump1.sql
    psql -U fedora -W -h localhost -d postgres -f /lat/dump1.sql

