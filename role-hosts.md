---
layout: index
---

# Ansible Role:
Setting up the fully quantified domain name (FQDN) of the host. This
role will not be executed when the ansible_virtualization_type is that
of virtualbox. This is the case for example when the portal is
provisioned with Vagrant. In that case, Vagrant already sets up the
hostname and this does not need to be redone.


## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙ hostname
Host name of the target machine.

```
hostname: portal
```
---

### ❙ domainname
Domain name of the tager machine.

```
domainname: example.org
```

## Role Templates

`templates/hosts.j2`

## Role Dependencies
None.
