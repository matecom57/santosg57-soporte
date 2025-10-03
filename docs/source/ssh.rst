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

Bucles for en Bash
------------------


¿Cómo uso el bucle for de Bash para 
repetir una tarea en Linux/UNIX? ¿Cómo puedo configurar bucles infinitos usando la instrucción for? ¿Cómo uso una 
expresión de control de bucle for de Bash de tres parámetros?

Un bucle for en bash es una sentencia del lenguaje de programación bash que permite la ejecución repetida de 
código. Un bucle for se clasifica como una sentencia de iteración, es decir, consiste en la repetición de un 
proceso dentro de un script bash. Por ejemplo, se puede ejecutar un comando o tarea de UNIX cinco veces, o leer y 
procesar una lista de archivos mediante un bucle for. Un bucle for puede utilizarse en el intérprete de comandos 
del shell o dentro del propio script del shell.

**sintaxis del bucle for**

Los rangos numéricos para la sintaxis son los siguientes:

.. code:: Bash

   for VARIABLE in 1 2 3 4 5 .. N
   do
     command1
     command2
     commandN
   done

.. code:: Bash

   for VARIABLE in file1 file2 file3
   do
     command1 on $VARIABLE
     command2
     commandN
   done

.. code:: Bash

   for OUTPUT in $(Linux-Or-Unix-Command-Here)
   do
     command1 on $OUTPUT
     command2 on $OUTPUT
     commandN
   done

**Ejemplos**

.. code:: Bash

   #!/bin/bash
   for i in 1 2 3 4 5
   do
      echo "Welcome $i times"
   done

.. code:: Bash

   #!/bin/bash
   for i in {1..5}
   do
      echo "Welcome $i times"
   done

.. code:: Bash

   #!/bin/bash
   echo "Bash version ${BASH_VERSION}..."
   for i in {0..10..2}
   do
     echo "Welcome $i times"
   done

.. code:: Bash

   #!/bin/bash
   for i in $(seq 1 2 20)
   do
      echo "Welcome $i times"
   done

**Sintaxis de bucles for de bash de tres expresiones**

Este tipo de bucle for comparte una herencia común con el lenguaje de programación C. Se caracteriza por una 
expresión de control de bucle de tres parámetros, que consta de un inicializador (EXP1), una prueba o condición de 
bucle (EXP2) y una expresión/paso de conteo (EXP3).

.. code:: Bash

   for (( EXP1; EXP2; EXP3 ))
   do
    command1
    command2
    command3
   done
   ## The C-style Bash for loop ##
   for (( initializer; condition; step )) 
   do
      shell_COMMANDS
   done

.. code:: Bash

   #!/bin/bash
   # set counter 'c' to 1 and condition 
   # c is less than or equal to 5
   for (( c=1; c<=5; c++ ))
   do 
      echo "Welcome $c times"
   done

**¿Cómo uso for como bucles infinitos ?**

Se pueden crear bucles for infinitos con expresiones vacías, como:

.. code:: Bash

   #!/bin/bash
   for (( ; ; ))
   do
      echo "infinite loops [ hit CTRL+C to stop]"
   done

**Salida condicional con interrupción**

Puedes salir anticipadamente con la sentencia break dentro del bucle for. Puedes salir de un bucle FOR, WHILE o 
UNTIL usando break. Sentencia break general dentro del bucle for:

.. code:: Bash

   for I in 1 2 3 4 5
   do
     statements1      #Executed for all values of ''I'', up to a disaster-condition if any.
     statements2
     if (disaster-condition)
     then
       break              #Abandon the loop.
     fi
     statements3              #While good and, no disaster-condition.
   done


El siguiente script de shell revisará todos los archivos almacenados en el directorio /etc. El bucle for se 
abandonará cuando se encuentre el archivo /etc/resolv.conf :

.. code:: Bash

   #!/bin/bash
   # Count dns name server in the /etc/resolv.conf if found
   for file in /etc/*
   do
        # check if file exists in bash using the if #  
    if [ "${file}" == "/etc/resolv.conf" ]
    then
        countNameservers=$(grep -c nameserver /etc/resolv.conf)
        echo "Total dns ${countNameservers} nameservers defined in ${file}"
        break
    fi
   done

**Continuación temprana con instrucción continue**

Para reanudar la siguiente iteración del bucle FOR, WHILE o UNTIL, utilice la instrucción continue.

.. code:: Bash

   for I in 1 2 3 4 5
   do
     statements1      #Executed for all values of ''I'', up to a disaster-condition if any.
     statements2
     if (condition)
     then
       continue   #Go to next iteration of I in the loop and skip statements3
     fi
     statements3
   done

https://www.cyberciti.biz/faq/bash-for-loop/




