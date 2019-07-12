Satellite
=========

This role takes care of installing Red Hat Satellite.

Requirements
------------

- Host needs to be subscribed and the correct repos enabled before running this role.

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

```

License
-------

Apache License 2.0


Author Information
------------------
Originally written by the below, further enhanced by Ken Hitchcock
Red Hat Community of Practice & staff of the Red Hat Open Innovation Labs.
