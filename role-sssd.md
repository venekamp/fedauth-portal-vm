---
layout: index
---

# Ansible Role:
The /etc/nsswitch.conf is used to tell that sssd is to be used to gather
information about users, passwords and groups.

## Requirements
None.

## Role Variables

### ❙ hostname
Name of the host machine on which LDAP is running on.

```
hostname: portal
```
---

### ❙ domainname
Domain name of the machine LSAP is running on.
```
domainname: example.org
```
---

### ❙ basedn
Base DN in the LDAP tree.

```
basedn: dc=portal,dc=example,dc=org
```

## Role Templates

```
templates/nsswtch.conf.j2
```
---

```
templates/sssd.conf.j2
```

## Role Dependencies
None.
