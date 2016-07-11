---
layout: index
---

# Ansible Role:
LDAP is used to store the application specific passwords. This role
installs LDAP and creates the appropriate directory structure. Two
objectes are added:

 1. an organizationalUnit (ou) group with 'irodsuser' in it;
 2. an organizationalUnit (ou) users with 'John Doe' as an inital user.

## Limitations
Idealy LDAP is used in a secure manner, i.e. ldaps:// However, this is
not the case yet. Version 1.1 should have this feature in place.

## Nomenclture
LDAP uses a number of abrivation and these are used in the documentation
and templates as well.

| C       | Country (e.g. NL, D, UK, etc.)        |
| CN      | Common Name                           |
| DC      | Domain Component                      |
| DN      | Distingished Name                     |
| L       | Locallity (e.g. City)                 |
| LDAP    | Lightweight Directory Access Protocol |
| O       | Organisation                          |
| OU      | Organisational Unit                   |
| ST      | State or Provance                     |

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also `defaults/main.yml`.

### ❙ base_dn
LDAP uses a directory like structure. For the portal all things stored
are below a certain DN. The `base_dn` specifies from which point objects
are accessed.  Below the base_dn, two objects are defined:

  1. 'groups', which holds group names to which users can be assigned to. Currently (v1.0) the  only group listed is `irodsusers`;
  2. 'users', which holds the users that have been added to LDAP structure. The portal takes care of adding users, but one users is added by default: 'John Doe'.

```
basedn: "dc=portal,dc=example,dc=org"
```
---

### ❙ ldap_admin
LDAP needs an admin account. The `ldap_admin` specifies the name of the
admin user. The admin name on its own is not sufficient within LDAP to
denote the admin account. For this a distignished name (DN) is
necessary. The `ldap_admin` is part of the DN.

```
ldap_admin: admin
```
---

### ❙ ldap_admin_passwd
Password for the admin account in LDAP. The default password is insecure
an cannot be used safely. Change it!

```
ldap_admin_passwd: 12345678
```
---

### ❙ rootdn
This is the identity of the admin user in LDAP. The identity is
specified as a disingshed name (DN). Using the above default values for
both `ldap_admin` (admin) and `basedn` (dc=portal,dc=example,dc=org),
than the default DN is: `cn=admin,dc=portal,dc=example,dc=org`.

```
rootdn: "cn=\{\{ ldap_admin \}\},\{\{ basedn \}\}"
```
---

### ❙ organisation
Name of the origanisation, i.e. O attribute.

```
organisation: Example
```
---

### ❙ hostname
Host name of the machine on which LDAP is installed. Note: you cannot
tell Ansible to install LDAP on the `hostname` machine. This variables
is used for getting a correct configuration.

```
hostname: portal
```
---

### ❙ domainname
Domain name of the machine on which LDAP is installed. This variables is
used for getting a correct configuration.

```
domainname: example.org
```
---

### ❙ ldap_certs_bundle
In case LDAP is configured to user tls for its communication, LDAP must
know where it can find the certificates that it can trust. This variable
speciefies the path where these certiciates are.

```
ldap_certs_bundle: /etc/pki/tls/certs/ca-bundle.crt
```
---

### ❙ ldapcerts_bundle_plus
Like for `ldap_certs_bundle` it hold the certificates that LDAP can
trust, but added with the generated self signed certificate. This
variables speciefies the path where these certificates are.

```
ldap_certs_bundle_plus: /etc/openldap/certs/certs.pem
```

### ❙ ldap_certificate_file
LDAP client must know about the certificate that must be used for secure
(ldaps://) communication with the LDAP server. This variables specifies
the path where the cerficate can be found.

```
ldap_certificate_file: /etc/pki/tls/certs/portal.example.org.crt
```
---

### ❙ ldap_certificate_key_file
The LDAP server need to a have access to the private key that has been
used to self signed the certificate. The variable specified the path of
the private key.

```
ldap_certificate_key_file: /etc/pki/tls/private/portal.example.org.key
```

## Role Templates
`templates/add_admin.ldif.j2`

`templates/add_group_and_populate.ldif.j2`

`templates/add_users.ldif.j2`

`templates/irods.j2`

`templates/ldap.conf.j2`

`templates/slapd.conf.j2`

`templates/slapd.j2`

## Role Dependencies
None.
