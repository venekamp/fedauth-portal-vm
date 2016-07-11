---
layout: index
---

# Ansible Role:
The Fedauth-Portal makes use of SimpleSAMLphp for the SAML 2.0 flow.

## Requirements
In order for SimpleSAMLphp to work properly, the provisioning of
SimpleSAMLphp alone is not enough. SAML 2.0 works on the basis of
trusted meta data and before our side of the meta data is trusted, we
need to register ourselves first. This is something that cannot be done
automatically. Therefore, after successful provisioning of the
SimpleSAMLphp role, a manula registation is required to finish the
process. Consult your federation to find out how this process works for
you.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙ simplesaml_version
Specify which version of SimpleSAMLphp to provision.

```
simplesaml_version: 1.14.3

```
---

### ❙ admin_password
SimpleSAMLphp requires a password for the admin account in
SimpleSAMLphp.

```
admin_password: changeme
```
---

### ❙ technical_contact_name
In order to complete some information, the name of the technical contact
needs to be specified.

```
technical_contact_name: John Doe
```
---

### ❙ technical_contact_email
In order to complete some information the e-mail address of the
technical contact needs to be specified.

```
technical_contact_email: john.doe@example.org
```
---

### ❙ timezone
Setting the timezone for SimpleSAMLphp.

```
timezone: Europe/Amsterdam
```
---

### ❙ trusted_domains
SimpleSAMLphp can be told about which domain it should trust.

```
trusted_domains: "'localhost:4443', 'portal.example.org'"
```
---

### ❙ federation_name
SimpleSAMLphp can be informed about the name of the federation.

```
federation_name: SURFconext
```
---

### ❙ federation_metadata_url
SAML 2.0 depends on the exchange of meta data. Not only does the
federation need to know about our meta data, we need to know about the
meta data of other as well. Since we are using the SURFconext federation
there is only one source of meta data we need to know about, as
SURFconext is a hub and spoke type of federation. SimpleSAMLphp needs to
be told about where is can find the required meta data.

```
federation_metadata_url: https://engine.surfconext.nl/authentication/idp/metadata
```
---

### ❙ federation_sso_url
SimpleSAMLphp needs to know about the meta data of other parties in the
federation. For SURFconect there is only one such source as it is a hun
and spole type of federation.

```
federation_sso_url: https://engine.surfconext.nl/authentication/idp/single-sign-on
```
---

### ❙ private_key
A private key is generated that is used for signing a certificate.


```
private_key: saml.key
```
---

### ❙ certificate
Self signed certificate.

```
certificate: saml.crt
```

## Role Templates
`templates/authsources.php.j2`

`templates/config.php.j2`

`templates/saml20-idp-remote.php.j2`

## Role Dependencies
None.
