dcm2bids
========

https://unfmontreal.github.io/Dcm2Bids/3.2.0/get-started/install/#python

**Installation**

There are several ways to install dcm2bids.

**Containers**


We provide a container image that includes both dcm2niix and dcm2bids as well as pydeface and the BIDS validator. You can install it using Docker or Apptainer/Singularity.

**Docker**

.. code:: Bash

   export VERSION=3.2.0
   docker pull unfmontreal/dcm2bids:${VERSION}

**Installing binary executables**

**Installing using pip or conda**

**Dependencies**

Installing using pip or conda

.. code:: Python

   python --version

Install dcm2bids

.. code:: Python

   conda install -c conda-forge dcm2bids
   conda install -c conda-forge dcm2niix

Create environment.yml

.. code:: Bash

   mkdir dcm2bids-proj

You can create a project directory anywhere on your computer, it does not matter. 
You can create ``dcm2bids-proj`` if you need inspiration.

.. code:: Python

   name: dcm2bids
   channels:
     - conda-forge
   dependencies:
     - python>=3.8
     - dcm2niix
     - dcm2bids

Activate environment

.. code:: Python

   conda activate dcm2bids

Verify that dcm2bids works

.. code:: Python

   dcm2bids --help

Create a new directory for this tutorial

.. code:: Python

   mkdir dcm2bids-tutorial
   cd dcm2bids-tutorial

Scaffolding

Tree structure of the scaffold created by dcm2bids⚓︎

.. code:: bash

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

Run ``dcm2bids_scaffold``

.. code:: Python

   dcm2bids_scaffold --help


.. code:: Python

   dcm2bids_scaffold -o bids_project

Change directory to go in your scaffold

.. code:: Python

   cd bids_project

Download neuroimaging data

.. code:: Bash

   wget -O dcm_qa_nih-master.zip https://github.com/neurolabusc/dcm_qa_nih/archive/refs/heads/master.zip

   unzip dcm_qa_nih-master.zip -d sourcedata/

   mv sourcedata/dcm_qa_nih-master sourcedata/dcm_qa_nih

You should now have a ``dcm_qa_nih`` directory nested in sourcedata with a bunch of files and directories:

.. code:: Bash

   ls sourcedata/dcm_qa_nih

Building the configuration file

.. code:: Bash

   dcm2bids_helper --help




3 directories, 5 files









