---
layout: index
---

# Ansible Role:
Generate a self signed certificate and private key.

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### key_out
When using self signed certificates, a priviate key will be generated
and saved at the specified path.

```
key_out: /etc/pki/tls/private/portal.example.org.key
```
---

### ❙ cert_out
When using sef signed certificates, a new certificate will be generated
and save at the specified path.

```
cert_out: /etc/pki/tls/certs/portal.example.org.crt
```
---

### ❙ key_type
OpenSSL accepts different private keys (rsa, dsa) and different key
lengths. The `key_type` specifies them in the form of:
\<type\>:\<bitlength\>

```
key_type: rsa:2048
```
---

### ❙ country_name
The certificate requires a country to be present. Use this variable to
specify one.

```
country_name: NL
```
---

### ❙ state_or_province_name
The certificate requires a state or provance to be present. Use this
variable to specify one.

```
state_or_province_name: Noord-Holland
```
---

### ❙ locality_name
The certificate requires a locality (city) to be present. Use this
variable to specify one.

```
locality_name: Amsterdam
```
---

### ❙ organisation
The certificate requires an organisation to be present. Use this
variable to specify one.

```
organisation: Example BV
```
---

### ❙ organisational_unit
The certificate requires a unit (department) to be present. Use this
variable to specify one.

```
organisational_unit: IT
```
---

### ❙ email_unit
The certificate requires an email address. Use this varible to specify
one.

```
email_unit: it
```
---

### ❙ default_bits
Default bits to be used during certificate generation, i.e. not used for
the private key.

```
default_bits: 2048
```

## Role Templates
`templates/openssl.conf.j2`

## Role Dependencies
None
