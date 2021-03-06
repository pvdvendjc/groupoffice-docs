Manual upgrade from the Tarball
-------------------------------

We strongly recommend that you use our Debian packages or Docker instead of the
tarball. But if you really want use it then follow these steps:

1. Make sure your system meets the :ref:`system-requirements`.
2. Make sure you're on the latest 6.2 version.
3. Make sure you've installed the "customfields" and "search" modules as they 
   will become part of the Group-Office core.
4. Move away your old source files. Important! Do not copy the new files over 
   the existing.
5. Put the new files at the right location.
6. If exists copy your old config.php or config.ini and license file to the new 
   files. It is good practice to keep these files one directory higher then the 
   Group-Office source so you have a complete clean code base.
7. Visit http://yourdomain/install/ and follow instructions.
8. Check if you have the right cron job in place::

      * * * * * www-data php <YOURDOCUMENTROOT>/cron.php
