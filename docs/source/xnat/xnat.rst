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

https://wiki.xnat.org/documentation/running-xnat-in-a-dockerized-container-with-config


https://alexcastel.wordpress.com/2023/09/22/instalacion-y-configuracion-de-tomcat-9-en-ubuntu-22/

.. code:: Bash

   sudo apt-cache search tomcat

   apt install tomcat9 tomcat9-admin

   service tomcat9 start

https://docs.vultr.com/how-to-install-postgresql-on-ubuntu-2204

.. code:: Bash

   sudo apt install -y postgresql-common -y

   sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh

   sudo apt install -y postgresql

   sudo systemctl start postgresql

   sudo systemctl status postgresql

Secure the PostgreSQL Database Server

.. code:: Bash

   psql --version
   
   sudo -u postgres psql

   postgres=# ALTER USER postgres WITH ENCRYPTED PASSWORD 'carlos12';
  
   # Create a new user db_manager with a new strong password.

   postgres=# CREATE USER santosg ENCRYPTED PASSWORD 'carlos12';

   postgres=# quit;


