htpc-common
===========

[![Galaxy](http://img.shields.io/badge/galaxy-GR360RY.htpc--common-green.svg?style=flat-square)](https://galaxy.ansible.com/GR360RY/htpc-common/)

An ansible role to perform common tasks on HTPC. 

Overview
--------

1. Install ssh server to allow remote management.
2. Configure Zerconf networking and avahi-alias service.
3. Create htpc_user if user doesn't exist.
4. Enable sudo access for htpc user.
5. Create htpc media and downloads folders.


Requirements
------------

Ansible 2.0

Role Variables
--------------

 Name                   | Default   
----------------------- |------------
 htpc_user_username     | htpc      
 htpc_user_password     | htpc      
 htpc_user_group        | htpc      
 htpc_user_shell        | /bin/bash 
 htpc_user_ssh_service  | yes       
 htpc_user_sudo_access  | yes       
 htpc_media_path        | /mnt/media
 htpc_media_movies      | movies    
 htpc_media_tv          | tv        
 htpc_media_music       | music     
 htpc_media_pictures    | pictures  
 htpc_media_downloads	| downloads
 htpc_zeroconf          | yes 

Dependencies
------------

None

Example Playbook
----------------

    - hosts: htpc

      vars:
        
        htpc_user_username: foo
        htpc_user_group: foo
        htpc_user_password: bar
        htpc_media_path: /media/big_disk
        htpc_media_movies: "My Movies"


      roles:
         - role: GR360RY.htpc-common

License
-------

BSD

Author Information
------------------

Gregory Shulov
