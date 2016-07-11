---
layout: index
---

# Ansible Role:
Install and configure phpldapadmin. This is useful, though strickly
speaking not necessary, to have. It provides for a web environment in
which you are able to read and write to the LDAP tree.

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙allowed_ip_addresses
Specify which ip addresses are allowed to use phpldapadmin.

```
allowed_ip_addresses:
  - { ip: 10.0.0.0/8 }
```
---

### ❙ basedn
The phpldapadmin config supports setting up a basedn. This is useful in
accessing the object as this happens relative from the basedn. Also,
when logging in as the admin LDAP user and in combination of ldap_admin
user name, it saves on typing the full DN, i.e.
cn=admin,dc=portal,dc=example,dc=org

```
basedn: dc=portal,dc=example,dc=org
```
---

### ❙ ldap_admin
Name of the LDAP admin user that phpldapadmin will use.

```
ldap_admin: admin
```
---

### ❙ ldap_endpoint
Specify the endpoint to which phpldapadmin should talk to..

```
ldap_endpoint: ldaps://portal.example.org
```

## Role Templates
`file/config.php.j2`

`file/phpldapadmin.conf.j2`

## Role Dependencies
None.
