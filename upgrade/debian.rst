Upgrading on Debian / Ubuntu
============================

Core system
-----------

When running 6.3.x or higher simply do:

.. code:: bash

   apt-get install groupoffice

From older versions than 6.3
````````````````````````````

- `First checkout the blog post about this release <http://groupoffice.blogspot.com/2018/07/group-office-63-released.html>`_
- 6.3 offers quite a lot of changes. It's strongly recommended to upgrade in a test environment first.
- After the upgrade you should consider replacing the "gota" module with the new
  "assistant" module for better file editing on the desktop.
- Typically the Custom CSS module was used to replace the logo. To take advanage of 
  the new System Settings -> Appearance features you should remove this CSS code.
- If you customized language then you should convert this to the new language :ref:`customize-language` system.

Steps
^^^^^

1. Make sure you're on the latest 6.2 version.
2. Make sure you've installed the "customfields" and "search" modules as they 
   will become part of the Group-Office core.
3. Uninstall the old "groupoffice-com" package but do **NOT** deconfigure the database:

   .. code:: bash
   
      apt-get remove groupoffice-com
      
4. If you made manual changes inside /usr/share/groupoffice (Like installing z-push for example). The the package manager will leave these folders intact. To avoid problems move /usr/share/groupoffice away before installing::
   
      mv /usr/share/groupoffice /root/groupofficebak

5. Edit /etc/apt/sources.list and remove:

   .. code:: bash
   
      deb http://repos.groupoffice.eu/ sixtwo main

6. Now do a fresh install of the Debian package. But note:

   - When the installer asks to install a database choose "NO".
   - When the installer asks to replace /etc/groupoffice/config.php, choose 
     "Keep the local version currently installed".

Continue at :ref:`install-debian`.


Mailserver
----------

If you're upgrading from a previous 6.3.x or higher version simply run::

   apt-get install groupoffice-mailserver

Or if you also installed the anti spam and virus package:

   apt-get install groupoffice-mailserver groupoffice-mailserver-antispam

Upgrading from 6.2
``````````````````

1. To upgrade from 6.2 you must start with a clean system by removing all previous
software and configuration. **Make a backup!**::

      apt-get purge groupoffice-mailserver dovecot* postfix* clamav* spamassassin amavisd-new

2. Then install the new package::

      apt-get install groupoffice-mailserver

3. Move the mail to the new location::

      mv /home/vmail/* /var/mail/vhosts
      rmdir /home/vmail

4. Remove no longer required packages::
      
      apt-get autoremove