dcm2bids
========

https://unfmontreal.github.io/Dcm2Bids/3.2.0/get-started/install/#python


Installing using pip or conda

.. code:: Python

   python --version

Install dcm2bids

.. code:: Python

   conda install -c conda-forge dcm2bids
   conda install -c conda-forge dcm2niix

Create environment.yml

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











