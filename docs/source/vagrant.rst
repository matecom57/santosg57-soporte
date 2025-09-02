Vagrant
=======

.. code:: Bash

   (base) iMac-de-Fernando:ubuntu24_XNAT_sep0225 santosg$ ./crea_24.sh 
   introduce nombre de la maquina virtual
   ubuntu24_XNAT_sep0225
   ==> vagrant: A new version of Vagrant is available: 2.4.9 (installed version: 2.4.3)!
   ==> vagrant: To upgrade visit: https://www.vagrantup.com/downloads.html

   ==> box: Box file was not detected as metadata. Adding it directly...
   ==> box: Adding box 'ubuntu24_XNAT_sep0225' (v0) for provider: 
       box: Unpacking necessary files from: 
   file:///Users/santosg/ubuntu24_XNAT_sep0225/ubuntu24_Instalador_may0425.box

   ==> box: Successfully added box 'ubuntu24_XNAT_sep0225' (v0) for ''!
   A `Vagrantfile` has been placed in this directory. You are now
   ready to `vagrant up` your first virtual environment! Please read
   the comments in the Vagrantfile as well as documentation on
   `vagrantup.com` for more information on using Vagrant.
   Bringing machine 'default' up with 'virtualbox' provider...
   ==> default: Importing base box 'ubuntu24_XNAT_sep0225'...

   ==> default: Matching MAC address for NAT networking...
   ==> default: Setting the name of the VM: 
   ubuntu24_XNAT_sep0225_default_1756846983854_45632
   ==> default: Clearing any previously set network interfaces...
   ==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
   ==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
   ==> default: Booting VM...
   ==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
   ==> default: Machine booted and ready!
   ==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default: 
    default: Guest Additions Version: 7.0.16
    default: VirtualBox Version: 7.1
   ==> default: Mounting shared folders...
    default: /Users/santosg/ubuntu24_XNAT_sep0225 => /vagrant
   (base) iMac-de-Fernando:ubuntu24_XNAT_sep0225 santosg$ 

https://wiki.xnat.org/documentation/xnat-installation-guide

Step 1: Install Prerequisites
1: Start with a compatible server OS.

2: Install the core XNAT dependencies

* Java 8 JRE or JDK (XNAT will not run with later versions of Java)

* Apache Tomcat 8.5 or 9.0 (recommended; 7.0 supported but requires special 
configuration)

* PostgreSQL 10 or later
  
Step 2: Configure PostgreSQL

https://www.oracle.com/java/technologies/downloads/#java8

(base) iMac-de-Fernando:ubuntu24_XNAT_sep0225 santosg$ ./ss.sh 
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.8.0-59-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Sep  2 09:33:53 PM UTC 2025

  System load:           0.53
  Usage of /:            32.3% of 30.34GB
  Memory usage:          36%
  Swap usage:            16%
  Processes:             239
  Users logged in:       1
  IPv4 address for eth0: 10.0.2.15
  IPv6 address for eth0: fd00::dd8:a112:9ecb:319e
  IPv6 address for eth0: fd00::a00:27ff:fe64:e1ff

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

5 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm


*** System restart required ***

This system is built by the Bento project by Chef Software
More information can be found at https://github.com/chef/bento

Use of this system is acceptance of the OS vendor EULA and License Agreements.
Last login: Tue Sep  2 21:33:55 2025 from 10.0.2.2
vagrant@vagrant:~$ 






