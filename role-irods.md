---
layout: index
---

# Ansible Role
Download and install a iRODS ICAT package. Also a database plugin is required.
This role installs a Postgres database plugin and not the MySQL one.

After installing iRODS, a configuration script must be run in order to
configure iRODS correctly. The script requires a number of input values
and these are defined in 'files/setup_irods_answers'. This file is piped
to the install script.

Once Postgres has been installed a database needs to be created for
iRODS. The creatation of the database is done with the following
script: 'files/postgre_create_ICAT'.

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙ ansible_ssh_user
This is an Ansible fact and as such defined by ansible.

```
ansible_ssh_user: No defaults
```
---

### ❙ irods_version
Specift which iRODS version to be downloaded and installed. The full,
i.e. ICAT, package of iRODS will be downloaded.

````
irods_version: 4.1.8
```
---

### ❙ irods_database_plugin_version
The portal uses postgres as its database backend and with this variable
you are able to tell which version you want to download and install.

```
irods_database_plugin_version: 1.8
```

## Role Templates
`files/postgre_create_ICAT_db`

`files/setup_irods_answers`

## Role Dependencies
None.
