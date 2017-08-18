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
```
lynis_version: the current version of lynis used to grab the tar file from cisofy.com full name of the file, no path
lynis_cron: what lynis is going to run e.g. ( /usr/local/lynis/lynis -c --cronjob --upload --profile /usr/local/lynis/custom.prf)
maldet_cron: what to run e.g. (/usr/local/maldetect/maldet -b -r /home?/?/public_html/,/var/www/html/,/usr/local/apache/htdocs/ 1 >> /dev/null 2>&1)
```

Role Tags
--------------
```
scanners: all scanner installs are tagged with scanners
lynis: to install lynis
maldet: to install maldet
cron: adds lynis and maldet to cron
remove: will remove everything installed
```

Dependencies
------------

None

Example Playbook
----------------
```
---
- name: ansible-linux-security-role
  hosts: all
  user: secureuser
  sudo: yes
  roles:
    - ansible-linux-security-role
  vars_files:
    - group_vars/security
```
Your `group_vars/security` file would look something like this:
```
---
lynis_version: lynis_version: lynis-2.5.3.tar.gz
lynis_cron: /usr/local/lynis/lynis -c --cronjob --upload --profile /usr/local/lynis/custom.prf
maldet_cron: /usr/local/maldetect/maldet -b -r /path/to/scan/here/ 1 >> /dev/null 2>&1
```

and then run from CLI. e.g. to install Lynis on your dev-server
```
$ ansible-playbook -i inventory.py -e ansible_ssh_port=2222 -u secureuser -K ./security.yml --limit=dev-server --tags=lynis
```

Author Information
------------------

Blake Carver

License
---

The project is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

---
