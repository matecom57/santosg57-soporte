andy_freesurfer
===============

https://andysbrainbook.readthedocs.io/en/latest/FreeSurfer/FS_ShortCourse/FS_03_ReconAll.html

**Uso del comando Recon-all**

Generaremos todas las imágenes mencionadas anteriormente mediante el comando `recon-all`, el cual solo 
requiere una imagen anatómica ponderada en T1 con un buen contraste entre la sustancia blanca y la 
sustancia gris. Si te encuentras en el directorio `Cannabis`, dirígete al directorio anatómico de 
`sub-101` escribiendo `cd sub-101/ses-BL/anat`. A continuación, puedes ejecutar `recon-all` con el 
siguiente comando:

.. code:: Bash

   recon-all -s sub-101 -i sub-101_ses-BL_T1w.nii.gz -all


La opción -s especifica el nombre del sujeto, al cual puedes asignar el valor que desees. La opción -i 
indica la imagen anatómica que vas a analizar; por su parte, la opción -all ejecuta todos los pasos de 
preprocesamiento en tus datos. Salvo en los casos en que vuelvas a ejecutar un comando recon-all tras 
haber editado los datos, siempre te convendrá utilizar la opción -all.

Mientras se ejecuta el comando, los resultados se guardarán en un directorio denominado $SUBJECTS_DIR. 
Por defecto, $SUBJECTS_DIR es una variable que apunta al directorio $FREESURFER_HOME/subjects, donde 
$FREESURFER_HOME es otra variable que señala al directorio en el que se instaló FreeSurfer (por 
ejemplo, /usr/local/freesurfer). En otras palabras, los resultados de este comando recon-all se 
encontrarán en /usr/local/freesurfer/subjects.


