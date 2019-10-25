Satellite Install
=================

This role takes care of installing Red Hat Satellite. In either connected or disconnected mode.

Requirements
------------

- Host needs to be subscribed and the correct repos enabled before running this role. This only required if you are installing in connected mode.

Role Variables
--------------

```
# Scenario determines if we are deploying a satellite or capsule
# Only accepted options are satellite and capsule
satellite_scenario: satellite

# Manifest file needs to be generated and downloaded before this
# role is executed.
manifest_file_path: <path to the downloaded manifest-....zip file>

# Satellite basic configuration values
satellite_organization: <organization name>
satellite_location: <location of the Satellite server>
satellite_username: <admin username to be set>
satellite_password: <admin password to be set>

# Satellite can be installed in connected or disconnected mode. Below are the variable with their default values.
## Is the install disconnected?
satellite_disconnected: 'no'

## If disconnected, what are the iso file names?
satellite_iso_name: 'satellite-6.6.0-rhel-7-x86_64-dvd.iso'
satellite_rhel_iso_name: 'rhel-server-7.7-x86_64-dvd.iso'

## If disconnected where will the iso images be mounted?
satellite_rhel_mount_location: '/media/rhel7-server'
satellite_sat_mount_location: '/media/sat6'

## If disconnected, where are the ISO files stored?
satellite_pull_from_webserver: 'no'
satellite_iso_webserver: "http://webserver"
satellite_iso_file_location: '../files'

## Where will the ISO files be saved? Defaults to /var/pulp as it has the largest storage on a Satellite 6 install.
satellite_iso_dest_dir: '/var/pulp'
satellite_iso_mnt_dir: '/mnt/'


```

Example Playbook
----------------

```
- name: 'Configure Satellite'
  hosts: satellite-server
  roles:
  - role: ansible-role-satellite-install
```

Example Inventory
----------------

```
manifest_file_path: "{{ inventory_dir }}/../files/manifest_4fcc12bd-08bc-46c6-b3e0-09dbfaece2bd.zip"

satellite_organization: "Example Org
satellite_location: "DataCenter"
satellite_username: "admin"
satellite_password: "admin01"
satellite_disconnected: 'no'

```

License
-------

Apache License 2.0


Author Information
------------------
Originally written by the below, further enhanced by Ken Hitchcock
Red Hat Community of Practice & staff of the Red Hat Open Innovation Labs.
