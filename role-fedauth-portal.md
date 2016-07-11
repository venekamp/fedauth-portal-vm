---
layout: index
---

# Ansible Role: fedauth-portal
A number of scripts work together to provide for the functionally that
is required for all components to work as whole. The front end of the
protal runs within a browser. The `fedauth-portal.conf` is added to the
existing Apache configuration. In it are a number of variables:

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙ ansible_ssh_user
The remote users Ansible will use when using SSH. This is an Ansible
fact. Vagrant uses the vagrant user, while Ansible uses ansible by
default.

### ❙ hostname
Host name of your (virtual) machine.

```
hostname: portal
```
---

### ❙ domainname
Domain name of your (virtual) machine.
```
domainname: example.org
```

### ❙ cert_out
```
cert_out: /etc/pki/tls/certs/portal.example.org.crt
```
---

### ❙ key_out
Path of the private key that has been used for the certificate.

```
key_out: /etc/pki/tls/private/portal.example.org.key
```

## Role Templates
`fedauth-portal.conf.j2`

## Role Dependencies
None.
