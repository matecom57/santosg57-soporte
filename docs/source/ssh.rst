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

