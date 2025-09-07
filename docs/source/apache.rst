Install Apache
==============

.. code:: Bash

   sudo apt update
   sudo apt install apache2 -y
   apachectl -v
   sudo ufw allow 80/tcp

How to install PHP on Ubuntu 22.04 in 5 steps
---------------------------------------------

.. code:: Bash

   sudo apt update
   sudo apt install software-properties-common apt-transport-https ca-certificates lsb-release
   sudo apt install php
   php --version

.. code:: Bash

   sudo nano  /var/www/html/info.php

   <?php
   phpinfo();
   ?>

   sudo systemctl restart apache2

   http://server-ip/info.php

