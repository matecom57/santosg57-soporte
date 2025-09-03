dcm2bids
========

https://unfmontreal.github.io/Dcm2Bids/3.2.0/get-started/install/#python

**Installing using pip or conda**

Before you can use dcm2bids, you will need to get it installed. This page guides you through a minimal, typical dcm2bids installation 
workflow that is sufficient to complete all dcm2bids tasks.

Antes de poder usar dcm2bids, deberá instalarlo. Esta página le guiará a través de un flujo de trabajo de instalación mínimo y típico de dcm2bids, suficiente para completar todas sus tareas.


We recommend to skim-read the full page before you start installing anything considering there are many ways to install software in the 
Python ecosystem which are often dependent on the familiarity and preference of the user.

Le recomendamos leer la página completa antes de comenzar a instalar cualquier cosa, teniendo en cuenta que hay muchas formas de instalar software en el ecosistema Python que a menudo dependen de la familiaridad y preferencia del usuario.


We offer recommendations at the bottom of the page that will take care of the whole installation process in one go and make use of a 
dedicated environment for dcm2bids.

We offer recommendations at the bottom of the page that will take care of the whole installation process in one go and make use of a dedicated environment for dcm2bids.

**Dependencies**

**Python**

As dcm2bids is a Python package, the first prerequisite is that Python must be installed on the machine you will use dcm2bids. You will 
need Python 3.8 or above to run dcm2bids properly.

Dado que dcm2bids es un paquete de Python, el primer requisito es que Python esté instalado en el equipo donde se usará. Necesitará Python 3.8 o superior para ejecutar dcm2bids correctamente.


If you are unsure what version(s) of Python is available on your machine, you can find out by opening a terminal and typing ``python 
--version`` or ``python``. The former will output the version directly in the terminal while the latter will open an interactive Python 
shell 
with the version displayed in the first line.

Si no está seguro de qué versiones de Python están disponibles en su equipo, puede averiguarlo abriendo una terminal y escribiendo python --version o python. La primera mostrará la versión directamente en la terminal, mientras que la segunda abrirá una consola interactiva de Python con la versión mostrada en la primera línea.


.. code:: Bash

   python --version

If your system-wide version of Python is lower 3.8, it is okay. We will make sure to use a higher version in the isolated environment 
that will be created for dcm2bids. The important part is to verify that Python is installed.

If you are a beginning user in the Python ecosystem, the odds are that you have installed Anaconda, which contains all Python versions so 
you should be good. If you were not able to find out which version of Python is installed on your machine or find Anaconda on your 
machine, we recommend that you install Python through Anaconda.

We could install all the software one by one using a series of command:

.. code:: Bash

   conda install -c conda-forge dcm2bids
   conda install -c conda-forge dcm2niix

But this would install the software in the main environment instead of a dedicated one, assuming none were active. This could have 
atrocious dependencies issues in the long-term if you want to install other software.

**Create environment.yml**

That is exactly why dedicated environments were invented. To help creating dedicated environments, we can create a file, often called 
``environment.yml``, which is used to specify things such as the dependencies that need to be installed inside the environment.

To create such a file, you can use any code editor or your terminal to write or paste the information below, and save it in your project 
directory with the name ``environment.yml``:

You can create a project directory anywhere on your computer, it does not matter. You can create ``dcm2bids-proj`` if you need 
inspiration.

.. code:: Bash

   name: dcm2bids
   channels:
     - conda-forge
   dependencies:
     - python>=3.8
     - dcm2niix
     - dcm2bids

**Create conda environment + install dcm2bids**

.. code:: Bash

   conda env create --file environment.yml

**Activate environment**

Last step is to make sure you can activate1 your environment by running the command:

.. code:: Bash

conda activate dcm2bids

**Verify that dcm2bids works**

Finally, you can test that dcm2bids was installed correctly by running the any dcm2bids command such as ``dcm2bids --help``:

**Create a new directory for this tutorial**

For the tutorial, we recommend that you create a new directory (folder) instead of jumping straight into a real project directory with 
real data. In this tutorial, we decided to named our project directory ``dcm2bids-tutorial``.

.. code:: Bash

   mkdir dcm2bids-tutorial
   cd dcm2bids-tutorial

**Scaffolding**

While scaffolding is a not mandatory step before converting data with the main dcm2bids command, it is highly recommended when you plan 
to convert data. dcm2bids has a command named dcm2bids_scaffold that will help you structure and organize your data in an efficient way 
by creating automatically for you a basic directory structure and the core files according to the Brain Imaging Data Structure (BIDS) 
specification.

Tree structure of the scaffold created by dcm2bids

.. code:: Bash

   scaffold_directory/
   ├── CHANGES
   ├── code/
   ├── dataset_description.json
   ├── derivatives/
   ├── participants.json
   ├── participants.tsv
   ├── README
   ├── .bidsignore
   └── sourcedata/

   3 directories, 5 files

**Run dcm2bids_scaffold**

To find out how to run ``dcm2bids_scaffold`` work, you can use the ``--help`` option.

.. code:: Bash

   dcm2bids_scaffold --help

Note that you don't have to create the directory where you want to put the scaffold beforehand, the command will create it for you.

.. code:: Bash

   dcm2bids_scaffold -o bids_project

For the purpose of the tutorial, you chose to specify the output directory ``bids_project`` as if it were the start of a new project. For 
your real projects, you can choose to create a new directory with the commands or not, it is entirely up to you.

**Change directory to go in your scaffold**

For those who created the scaffold in another directory, you must go inside that directory.

.. code:: Bash

   cd bids_project

**Download neuroimaging data**

1. Download the zipped file from https://github.com/neurolabusc/dcm_qa_nih/archive/refs/heads/master.zip.

.. code:: Bash

   wget -O dcm_qa_nih-master.zip https://github.com/neurolabusc/dcm_qa_nih/archive/refs/heads/master.zip

2. Extract/unzip the zipped file into sourcedata/.

.. code:: Bash

   unzip dcm_qa_nih-master.zip -d sourcedata/

3. Rename the directory dcm_qa_nih.

.. code:: Bash

   mv sourcedata/dcm_qa_nih-master sourcedata/dcm_qa_nih

You should now have a ``dcm_qa_nih`` directory nested in ``sourcedata`` with a bunch of files and directories:


.. code:: Bash

   ls sourcedata/dcm_qa_nih

**Building the configuration file**

The configuration file is the central element for dcm2bids to organize your data into the Brain Imaging Data Structure standard. dcm2bids 
uses information from the config file to determine which data in the protocol will be converted, and how they will be renamed based on a 
set of rules. For this reason, it is important to have a little understanding of the core BIDS principles. The BIDS Starter Kit a good 
place to start Tutorial on Annotating a BIDS dataset from .

As you will see below, the configuration file must be structured in the Javascript Object Notation (JSON) format.

In short you need a configuration file because, for each acquisition, dcm2niix creates an associated .json file, containing information 
from the dicom header. These are known as sidecar files. These are the sidecars that dcm2bids uses to filter the groups of acquisitions 
based on the configuration file.

You have to input the filters yourself, which is way easier to define when you have access to an example of the sidecar files.

You can generate all the sidecar files for an individual participant using the dcm2bids_helper command.

**dcm2bids_helper command**

This command will convert the DICOM files it finds to NIfTI files and save them inside a temporary directory for you to inspect and make 
some filters for the config file.

As usual the first command will be to request the help info.

.. code:: Bash

   dcm2bids_helper --help

To run the commands, you have to specify the ``-d`` option, namely the input directory containing the DICOM files. The ``-o`` option is 
optional, 
defaulting to moving the files inside a new ``tmp_dcm2bids/helper`` directory from where you run the command, the current directory.


.. code:: Bash

   dcm2bids_helper -d sourcedata/dcm_qa_nih/In/

**Finding what you need in tmp_dcm2bids/helper**

You should now able to see a list of compressed NIfTI files (nii.gz) with their respective sidecar files (.json). You can tell which file 
goes with which file based on their identical names, only with a

.. code:: Bash

   ls tmp_dcm2bids/helper

As you can see, it is not necessarily easy to tell which scan files (nii.gz) refer to which acquisitions from their names only. That is 
why you have to go through their sidecar files to find unique identifiers for one acquisition you want to BIDSify.

Again, when you will do it with your DICOMs, you will want to run dcm2bids_helper on a typical session of one of your participants. You 
will probably get more files than this example

For the purpose of the tutorial, we will be interested in three specific acquisitions, namely:

1. 004_In_DCM2NIIX_regression_test_20180918114023

2. 003_In_EPI_PE=AP_20180918121230

3. 004_In_EPI_PE=PA_20180918121230

The first is an resting-state fMRI acquisition whereas the second and third are fieldmap EPI.

**Setting up the configuration file**

Once you found the data you want to BIDSify, you can start setting up your configuration file. The file name is arbitrary but for the 
readability purpose, you can name it ``dcm2bids_config.json`` like in the tutorial. You can create in the ``code/`` directory. Use any 
code 
editor to create the file and add the following content:

Once you are sure of you matching criteria, you can update your configuration file with the appropriate info.

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

For fieldmaps, you need to add an ``"intendedFor"`` as well as ``id`` field to show that these fieldmaps should be used with your fMRI 
acquisition. Have a look at the explanation of intendedFor in the documentation or in the BIDS specification.

Now that you have a configuration file ready, it is time to finally run ``dcm2bids``.

**Running dcm2bids**

.. code:: Bash

   dcm2bids -d sourcedata/dcm_qa_nih/In/ -p ID01 -c code/dcm2bids_config.json --auto_extract_entities

You can now have a look in the newly created directory sub-ID01 and discover your converted data!

.. code:: Bash

   tree sub-ID01/













