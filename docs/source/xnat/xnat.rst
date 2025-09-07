xnat
====

Installing

Start by cloning the xnat-docker-compose repository and checking out the features/dependency-mgmt branch:

.. code:: Bash

   $ git clone https://github.com/NrgXnat/xnat-docker-compose
   $ cd xnat-docker-compose
   $ git checkout features/dependency-mgmt

Launching

At this point, you can start XNAT with a basic configuration just by building and launching the docker-compose configuration:
CODE

.. code:: Bash

   $ ./gradlew composeBuild composeUp


