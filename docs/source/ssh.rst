SSH
===

.. code:: Bash

   (base) iMac-de-Fernando:ssh_maqquinas santosg$ ./drobo1.sh 
   kex_exchange_identification: read: Connection reset by peer
   Connection reset by 172.24.80.83 port 22
   (base) iMac-de-Fernando:ssh_maqquinas santosg$ 

.. code:: Bash

   (base) iMac-de-Fernando:ssh_maqquinas santosg$ cat drobo1.sh 
   #!/bin/bash

   sshpass -p Imagen2022$ ssh -X -Y labc12@172.24.80.83
   (base) iMac-de-Fernando:ssh_maqquinas santosg$ 

When the "ssh_exchange_identification: read: Connection reset by peer" error occurs, effective troubleshooting is crucial for identifying 
and resolving the underlying issues. In the following sections, we will explore various methods to diagnose and address the causes of 
this error.

**Restart sshd Daemon on Server**

The sshd daemon is a background process that runs on a server and manages incoming SSH connections. It is a crucial component of the SSH 
protocol, providing encrypted communication over a network.

A possible solution for the "ssh_exchange_identification: read: Connection reset by peer" error is to restart the sshd daemon on the 
server. If you are using Linux, run the command below to restart the service:

.. code:: Bash

   sudo systemctl restart sshd

**Check SSH Server Status**

Checking the SSH server status is an essential step in troubleshooting SSH-related issues. To check the sshd service status, run the 
following command:

.. code:: Bash

   sudo systemctl status ssh

If the SSH service is not running or if there are issues, restart it using one of the commands below:

For systems using ``systemd``:

.. code:: Bash

   sudo systemctl restart ssh

For systems using ``init.d``:

.. code:: Bash

   sudo service ssh restart


In case the service is missing, install it and start the openssh-server on Ubuntu by running the commands below:

.. code:: Bash

   sudo apt install openssh-server

.. code:: Bash

   sudo systemctl start ssh

**Check SSH Log File**

Checking the SSH log files on the server can help diagnose and resolve the "ssh_exchange_identification: read: Connection reset by peer" 
error. The log files contain information about the SSH connection attempts, errors, and other relevant details.

The location of the log files varies depending on the operating system. Common locations in different Linux distributions are:


* /var/log/auth.log
* /var/log/secure
* /var/log/auth.log

Extraer una subcadena
---------------------

En Bash, para extraer una subcadena utilizas la sintaxis ``${variable:inicio:longitud}``, donde inicio es la 
posición 
(basada en 0) desde donde quieres extraer y longitud es la cantidad de caracteres a extraer. Por ejemplo, 
``${mi_cadena:2:4}`` extraerá 4 caracteres de la variable **i_cadena** comenzando desde el tercer carácter (índice 
2). 

**Sintaxis básica:**

.. code:: Bash

   ${cadena:inicio:longitud} 

**cadena**

: La variable de la que deseas extraer una subcadena. 

**inicio**

: El índice (basado en 0) de la posición desde donde comienza la subcadena. 

**longitud**

: El número de caracteres que quieres extraer de la subcadena. 

**Ejemplos:**

Supongamos que tenemos la siguiente cadena en una variable:

bash

.. code:: Bash

   mi_cadena="Hola Mundo!"

Extraer desde una posición específica hasta el final:
 
bash

.. code:: Bash

   echo "${mi_cadena:5}"

  Salida: Mundo! (comienza en el índice 5 y va hasta el final). 

**Extraer una subcadena con posición y longitud:**

bash

.. code:: Bash

   echo "${mi_cadena:0:4}"

   Salida: Hola (comienza en el índice 0 y extrae 4 caracteres). 

**Extraer solo un carácter:**

  bash

.. code:: Bash

   echo "${mi_cadena:6:1}"

   Salida: M (comienza en el índice 6 y extrae 1 carácter). 

**Consideraciones:**

**Índice basado en 0:**

El primer carácter de la cadena está en el índice 0. 

**Sin longitud:**

Si omites la longitud, Bash extraerá la subcadena desde la posición inicio hasta el final de la cadena. 

**Cualquier comando:**

Esta técnica de subcadena se llama "expansión de parámetros" y se realiza directamente en Bash, sin la necesidad 
de ejecutar comandos externos. 


