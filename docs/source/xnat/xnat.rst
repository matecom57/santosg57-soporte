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


Run the following command to change the default peer value in the scram-sha-256 field in the main PostgreSQL configuration file pg_hba.conf to enable password authentication on the server.


.. code:: Bash

   sudo sed -i '/^local/s/peer/scram-sha-256/' /etc/postgresql/17/main/pg_hba.conf

   # Replace 17 with your installed PostgreSQL version number if it's different.

   sudo systemctl restart postgresql


https://wiki.xnat.org/documentation/prerequisites-for-installing-xnat#PrerequisitesforInstallingXNAT-configuring-other-jvm-options

Prerequisites for Installing XNAT
----------------------------------

Notes on Installing Java 8

Notes on Installing and Configuring Apache Tomcat

There are a few configuration changes to prepare Tomcat for XNAT 1.8. We cover the required step of defining xnat.home for Tomcat in the XNAT Installation Guide. These others are optional.

    Set other JVM options
    Change the Tomcat service user and group
    Install the Tomcat manager application


Locating the Primary Tomcat Configuration File

Make changes to your Tomcat configuration by modifying the primary Tomcat configuration file:

    For Debian and Ubuntu systems, this is usually located in /etc/default/tomcat9.

https://wiki.xnat.org/documentation/configuring-postgresql-for-xnat

.. code:: Bash

   xnat:~$ sudo su - postgres 
   postgres:postgres$ createuser --createdb xnat
   postgres:postgres$ createdb --owner=xnat xnat;
   postgres:postgres$ psql
   psql (12.6)
   Type "help" for help.

   postgres=# \password xnat
   Enter new password:
   Enter it again:
   postgres=# \q
   postgres:~$ logout
   xnat:~$

