linux
=====

Escribe uno de los siguientes comandos y presiona Enter:

.. code:: Bash

   ip a

Este comando muestra información detallada de todas las interfaces de red (Ethernet, inalámbricas, etc.) y sus direcciones IP asociadas. Busca la línea que comienza con inet para la dirección IPv4 o inet6 para IPv6.

.. code:: Bash

    hostname -I

Este comando mostrará directamente la(s) dirección(es) IP asignada(s) a tu máquina. 

Eliminar un prefijo/sufijo fijo de una cadena en Bash
-----------------------------------------------------

.. code:: Bash

   prefix="hell"
   suffix="ld"
   string="hello-world"
   foo=${string#"$prefix"}
   foo=${foo%"$suffix"}
   echo "${foo}"
   o-wor

Usando sed:

.. code:: Bash

   echo "$string" | sed -e "s/^$prefix//" -e "s/$suffix$//"
   o-wor



