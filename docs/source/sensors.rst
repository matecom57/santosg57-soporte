sensors
=======

You can monitor your hardware temperatures and fan speeds in Ubuntu by installing and using the ``lm-sensors package``. 


**Installing and Using lm-sensors**

* Open your terminal (``Ctrl + Alt + T``).

* Install the tool by running: ``sudo apt install lm-sensors``

* Detect your system's hardware sensors by running: sudo sensors-detect (answer YES to the prompts).

* Check your current readings by typing: ``sensors``. 

To see a visual walkthrough of installing and running lm-sensors in your terminal, watch this guide:

---------------------------------------------------

Once **lm-sensors** is installed you need to reach for your terminal:

type

.. code:: Bash

   sudo sensors-detect

just press **ENTER** for everything it suggests (shown in Uppercase)

At the end it will ask you whether to add what it finds to /etc/modules. If you are happy with the findings type "yes".

More information about lm-sensors and how to tailor it for your system can be found on the lm-sensors installation wiki page

------------------------------------------------------------

Get information about the sensors package on Ubuntu / Debian Linux, run:

.. code:: Bash

   apt info lm-sensors

The sensors-detect is an interactive command. It will walk you through scanning your system for various hardware monitoring chips installed on your motherboard. Hence, next configure the sensors, type:

.. code:: Bash

   sudo sensors-detect

So far, so good. Now that you have installed the package and configured the system. The next step is to read the data. Then to get CPU temperature/voltage/fan sensors, run:

.. code:: Bash

   sensors

https://www.cyberciti.biz/faq/install-sensors-lm-sensors-on-ubuntu-debian-linux/

**Understanding sensors (lm-sensors) outputs**

I see the following information:

    * coretemp-isa-0000 – CPU core temperature
    * thinkpad-isa-0000 – Thinkpad laptop fan speed
    * nvme-pci-0300 – NVIDIA GPU temperature data
    * BAT0-acpi-0 – Laptop battery (ACPI) voltage
    * ucsi_source_psy_USBC000:001-isa-0000 – Plugged in USB device voltage readings
    * iwlwifi_1-virtual-0 – Intel WiFi temperature data

In this example, run the sensors command every 2 seconds and highlight the difference:

.. code::Bash

   watch -n 2 -d sensors

-----------------------------------------------------------

The problem I am seeing is that as soon as stress starts the temperature skyrockets, and as soon as it stops it plummets. This can't be right!

Here is a little shell script and output to demonstrate the problem:

Script:

.. code:: Bash

   sensors | grep Core
   stress -c 8 -t 1
   sensors | grep Core
   str=$'Sleeping for 1s \n' 
   read -t 1 -p "$str"
   sensors | grep Core

Is this expected behavior? Is it physically possible for the temperatures sensors to see that much change this quickly? If so, I'm in trouble in terms of characterizing temperature changes. There is no time for me to gather data. The temperature basically spikes instantaneously, doesn't change while the jobs are running, and the vanishes as soon as the job finishes.

-----------------------------------------------------------------------

This is on an Ubuntu PC. My openSUSE Leap system installs it with a working configuration, but Ubuntu needs some additional tweaking. Run sensors-detect to set it up to detect even more stuff. The safe method is to accept all of the defaults by pressing the return key to answer every question:

.. code:: Bash

   sudo sensors-detect

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


https://www.linux.com/topic/desktop/advanced-lm-sensors-tips-and-tricks-linux-0/



