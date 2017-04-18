SpiderOak One
=========

Installs and configures SpiderOak One (https://spideroak.com)

Requirements
------------

* Uses _become_ to install packages

Role Variables
--------------

    spideroakone_username: (No default value)
    spideroakone_password: (No default value)
    spideroakone_reinstall: false
    spideroakone_devicename: (No default value)

    spideroakone_mirror_url: https://spideroak.com/getbuild?
    spideroakone_platform: ubuntu
    spideroakone_arch: x86_64    

    spideroakone_backup_include_dir: []
    spideroakone_backup_exclude_dir: []
    spideroakone_backup_include_file: []
    spideroakone_backup_exclude_file: []

    spideroakone_restores: []
    spideroakone_restore_files: False

    
    spideroakone_download_url: "{{spideroakone_mirror_url }}platform={{ spideroakone_platform }}&arch={{ spideroakone_arch}}"


Dependencies
------------

None

Example
-------

__Example playbook__


    - hosts: localhost
      connection: local
    
    roles:
      - henriklyngaard.spirderoakone
      
__Example inventory__


    spideroakone_username: "john.doe@example.com"
    spideroakone_password: "my_secret" 
    spideroakone_reinstall: "false"
    spideroakone_devicename: "laptop"

    spideroakone_restore_files: "true"
    spideroakone_restores: 
      - device: 1 
        path: /home/john/Pictures/2005/01/01 

    spideroakone_backup_include_dir:
      - /home/john/Pictures


    spideroakone_backup_include_file:
      - /home/john/.bash_history

* _device_ is the device id of an already instaled device to restore files from. You can get a list of devices by 
running _SpiderOakONE --userinfo_

License
-------

MIT

Author Information
------------------

This role works by invoking the SpierOakONE binary via the command module. There is little to none parsing of the 
output at this point in time. In future releases I hope to make a custom module.
 
Change log
----------

* 1.0: Initial version
