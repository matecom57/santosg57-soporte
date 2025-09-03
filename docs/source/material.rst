material
========

Translate-shell
---------------

.. code:: Bash

   sudo apt-get install translate-shell

.. code:: Bash

   trans :es "what is going on your life?"

   trans -b :es thanks

   trans :es file:///home/sapoclay/gtrans.txt


generate qr
-----------

https://qr.io/?gad_source=1&gad_campaignid=11398459434&gbraid=0AAAAAC6IOXIsuH3Y3JQyJM593vOfZizrH&gclid=CjwKCAjwq9rFBhAIEiwAGVAZP5wJyXM2ZAF8G0trdvDNAWKQT4SADoDeAw6ZQKpLqeVkJxyy-Y_ZcBoC-I0QAvD_BwE

https://qr-code.io/es/create?step=1&qr_onboarding=active_dpf&fx=c%C3%B3digo-QR&utm_source=google&utm_medium=cpc&utm_id=21676959307&utm_content=169474674160&utm_term=c%C3%B3digo+qr&network=g&matchtype=b&device=c&gaid=MX-ES-C-DPF&gad_source=1&gad_campaignid=21676959307&gbraid=0AAAAA-G5uJL5Xvy2VfN8u5ORLxLezipXs&gclid=CjwKCAjwq9rFBhAIEiwAGVAZP4GB-vgjqOEdCkoBSQlZtPVHlnlDd8F_03aHxqxJAFlfjvV_CtYmJRoCFEEQAvD_BwE

https://myqrcode.com/create?gclid=CjwKCAjwq9rFBhAIEiwAGVAZP5BMzV8fsNDnzvlBbaO3sfLX6dm-eAcb-t5R4LlEb41l2mGOW1PdcRoCdBcQAvD_BwE&utm_source=google&utm_medium=cpc&utm_campaign=20650250842&utm_content=154113813523&utm_term=create%20qr&matchtype=e&device=c&gad_source=1&gad_campaignid=20650250842&gbraid=0AAAAADHgbSbZv7AcZ3pFZc2NyQAk5dH4g

https://www.qr-code-generator.com/

https://qr.io/es/?gad_source=5&gad_campaignid=18652529461&gclid=EAIaIQobChMI7enizLS6jwMVCDfUAR0zSw-eEAAYASABEgIZ3_D_BwE#crea-gratis

https://bitly.com/pages/landing/qr-codes?gad_source=5&gad_campaignid=20734617027&gclid=EAIaIQobChMI7enizLS6jwMVCDfUAR0zSw-eEAAYBSAAEgKWePD_BwE


USAR DIFF PARA COMPARAR DIFERENCIAS ENTRE 2 DIRECTORIOS
--------------------------------------

Para usar Diff y obtener la diferencias existentes entre dos directorios tan solo tenéis que ejecutar un comando 
del siguiente tipo:

.. code:: Bash

   diff -r -q 'directorio 1' 'directorio 2'

El significado de cada uno de los parámetros es el siguiente:

* ``diff`` : Es la utilidad para comparar directorios entre si o ficheros entre sí.

* ``-r`` : Para indicar que 2 directorios se comparen de forma recursiva. En otras palabras con la opción -r 
también se 
compararán todos los subdirectorios que están dentro del directorio analizado.

* ``-q`` : Para que solo salgan en pantalla los ficheros que difieren de un directorio a otro.

* ``directorio 1`` : Es la ruta del primer directorio o fichero a comparar.

* ``directorio 2`` : Es la ruta del segundo directorio o fichero a comparar.

USAR DIFF PARA COMPARAR EL CONTENIDO DE DOS ARCHIVOS
----------------------------------------

Comparar si el contenido de 2 ficheros .odt es el mismo

.. code:: Bash

   diff '/home/joan/Borrar archivos temporales V1.odt' '/home/joan/Borrar archivos temporales V2.odt'

Ver las diferencias existentes entre 2 ficheros de forma más visual
-------------------------------------------------------------------

.. code:: Bash

   diff -y '/home/joan/Escritorio/Ver las diferencias entre 2 directorios o 2 ficheros/archivo 1.md' 
'/home/joan/Escritorio/Ver las diferencias entre 2 directorios o 2 ficheros/archivo 2.md' | cat -n

https://geekland.eu/comparar-directorios-y-archivos-comando-diff-linux/

dcm2bids
--------

**procesa.sh**

.. code:: Bash

   #!/bin/bash

   git clone https://github.com/neurolabusc/dcm_qa_nih/ dcm_qa_nih

   dcm2bids -d dcm_qa_nih/In/ -p ID01 -c dcm2bids_config.json --auto_extract_entities

**dcm2bids_config.json**

.. code:: Bash

   {
     "descriptions": [
       {
         "id": "id_task-rest",
         "datatype": "func",
         "suffix": "bold",
         "custom_entities": "task-rest",
         "criteria": {
           "SeriesDescription": "Axial EPI-FMRI (Interleaved I to S)*"
         },
         "sidecar_changes": {
           "TaskName": "rest"
         }
       },
       {
         "datatype": "fmap",
         "suffix": "epi",
         "criteria": {
           "SeriesDescription": "EPI PE=*"
         },
         "sidecar_changes": {
           "intendedFor": ["id_task-rest"]
         }
       }
     ]
   }




