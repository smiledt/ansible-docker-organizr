Docker-Organizr
=========

A role to spin up an Organizr docker container. This role was heavily inspired by (and all credit goes to) [Calvin Bui](https://calvin.me)'s other roles. This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. see defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory, the command line, AWX, etc. 

    organizr_name: organizr

This is the name of the container. 

    organizr_image: organizr/organizr

The image container. By default this pulls the official image.

    organizr_ports:
      - 80:80

These are the exported ports of the container. By default, port 80 is exposed.

    organizr_config_directory: "/opt/organizr"

This is the directory that config files will be stored. This is mapped to /config in the container. 

    organizr_environment_variables:
      PUID: "1000"
      PGID: "1000"
      fpm: "true"
      TZ: "America/Chicago"
      branch: "v2-master"

This is a dictionary of extra environment variables for the container. 

    organizr_docker_additional_options:
      restart_policy: unless-stopped

Another dictionary, this time of additional options for the container. By default, this sets the container to start on boot unless it was previously stopped. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy Organizr web interface.
      hosts: organizr
      become: true
      roles:
      - role: docker-organizr

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/