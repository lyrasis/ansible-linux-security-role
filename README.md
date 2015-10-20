Linux Security Role
=========

This role will install a number of security auditing and monitoring tools for Linux servers.
```
-rkhunter ( http://rkhunter.sourceforge.net/ )
-chkrootkit ( http://www.chkrootkit.org/ )
-Linux Malware Detect ( https://www.rfxn.com/projects/linux-malware-detect/ )
-Lynis ( https://cisofy.com/lynis/ )
-LSAT ( http://usat.sourceforge.net/ )
-tiger ( http://www.nongnu.org/tiger/ )
```

Requirements
------------

None.

Role Variables
--------------

lynis_version: the current version of lynis used to grab the tar file from cisofy.com

Dependencies
------------

None

Example Playbook
----------------

Doesn't exsist yet, will soon :-)
This is totally NOT WORKING AT ALL YET!!!!
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Blake Carver
