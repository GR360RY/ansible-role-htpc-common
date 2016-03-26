htpc-common
===========

[![Build Status](https://travis-ci.org/GR360RY/ansible-role-htpc-common.svg?branch=master)](https://travis-ci.org/GR360RY/ansible-role-htpc-common) [![Galaxy](http://img.shields.io/badge/galaxy-GR360RY.htpc--common-green.svg)](https://galaxy.ansible.com/GR360RY/htpc-common/)

An ansible role to perform common tasks on HTPC. 

Overview
--------

1. Install ssh server to allow remote management.
2. Configure Zerconf networking and avahi-alias service.
3. Create htpc_user if user doesn't exist.
4. Enable sudo access for htpc user.
5. Create htpc media and downloads folders.

Downloads and Media folders layout if used with default variable values:

```
/mnt/media/
├── downloads
│   ├── complete
│   └── incomplete
├── movies
├── music
├── pictures
└── tv
```

Requirements
------------

Ansible 2.0

Role Variables
--------------

```
# defaults file for htpc-common

# htpc user
htpc_user_username: htpc
htpc_user_password: htpc
htpc_user_group: htpc
htpc_user_shell: /bin/bash
htpc_user_sudo_access: yes

# services
htpc_ssh_service: yes
htpc_create_media_folders: yes
htpc_zeroconf: yes

# downloads and media directories
htpc_media_path: /mnt/media
htpc_media_movies: movies
htpc_media_tv: tv
htpc_media_music: music
htpc_media_pictures: pictures
htpc_downloads_complete: "{{ htpc_media_path }}/downloads/complete"
htpc_downloads_incomplete: "{{ htpc_media_path }}/downloads/incomplete"

# Helper variable. In use by other roles
# Change the way different service are resolved in configuration files.
# Available values are zeroconf, hostname and staticip
htpc_resolving: zeroconf

# Helper variable. In use by other roles
# When installed with docker role, make sure htpc user can access the docker daemon
docker_group_members:
  - "{{ htpc_user_username }}"
```

Dependencies
------------

None

Example Playbook
----------------

```
- hosts: htpc-server
  become: yes

  vars:

    htpc_user_username: foo
    htpc_user_group: foo
    htpc_user_password: bar
	htpc_media_path: /media/big_disk
	htpc_media_movies: "My Movies"


  roles:
    - role: GR360RY.htpc-common
```

HTPC-Ansible Project
--------------------

This role is part of HTPC-Ansible project that includes additional roles for building Ubuntu Based HTPC Server.

Complete list of Ansible Galaxy roles is below:

- [`GR360RY.htpc-common`](https://galaxy.ansible.com/GR360RY/htpc-common) - Create htpc user and media folders
- [`GR360RY.htpc-nas`](https://galaxy.ansible.com/GR360RY/htpc-nas) - Configure NAS ( NFS, CIFS and AFP )
- [`GR360RY.kodi-client`](https://galaxy.ansible.com/GR360RY/kodi-client) - Install Kodi Media Player
- [`GR360RY.kodi-mysql`](https://galaxy.ansible.com/GR360RY/kodi-mysql) - Install MySQL Backend for Kodi
- [`GR360RY.deluge`](https://galaxy.ansible.com/GR360RY/deluge) - Install Deluge Bittornet Client
- [`GR360RY.sabnzbd`](https://galaxy.ansible.com/GR360RY/sabnzbd) - Install Sabnzbd Usenet Client
- [`GR360RY.nzbtomedia`](https://galaxy.ansible.com/GR360RY/nzbtomedia) - Install NZBtoMedia Postprocessing
- [`GR360RY.sickrage`](https://galaxy.ansible.com/GR360RY/sickrage) - Install SickRage
- [`GR360RY.couchpotato`](https://galaxy.ansible.com/GR360RY/couchpotato) - Install CouchPotato
- [`GR360RY.htpc-manager`](https://galaxy.ansible.com/GR360RY/htpc-manager) - Install HTPCManager

Additional Info is available at [www.htpc-ansible.org](http://www.htpc-ansible.org)

License
-------

BSD

Author Information
------------------

Gregory Shulov
