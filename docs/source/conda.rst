conda
=====

https://docs.rcc.fsu.edu/software/conda/#conda-vs-pip

Setting up a Conda Environment
------------------------------

**Initial setup**

To use Conda, you need to configure your shell environment using the conda init command. You 
only need to do this once. Thenceforth, when you log in to the HPC, your shell will be 
configured for Conda.

.. code:: Bash

   module load anaconda
 
   conda init bash

   source ~/.bashrc

   # Your prompt will look something like this (notice the "(base)" in front of the prompt)

   (base) [USER@h22-login-26 ~]$

**Managing Conda Environments**

You can create as many Conda environments as you wish. Each environment is isolated to a 
single directory, and you can have as many environments as you need. To a create a new Conda 
enviroment you will need to first load the ``webproxy`` module.

For example, to create a Conda environment named ``my_conda_app``:

.. code:: Bash

   module load webproxy
   conda create -n my_conda_app

Run the command ``conda activate my_conda_app``:

Work in your Conda environment:

.. code:: Bash

   conda install some-package

To de-activate your Conda environment:

.. code:: Bash

   conda env list

Delete a Conda environment:

.. code:: Bash

   conda remove --name my_conda_app --all

**Anaconda**




