 install Google Chrome on Ubuntu
================================


Method 1: Using the Terminal (Recommended)

1. Open your terminal (``Ctrl + Alt + T``).

2. Download the official 64-bit .deb package using ``wget``:

.. code:: Bash

   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

3. Install the package using apt so it automatically handles dependencies:

.. code:: Bash

   sudo apt install ./google-chrome-stable_current_amd64.deb

**Starting Chrome**

.. code:: Bash

   google-chrome



