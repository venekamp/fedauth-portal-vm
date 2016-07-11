---
layout: index
---

# Ansible Role: Apache
Apache is configured to use TLS, i.e. https:// This also means that a
certificate needs to be installed. This can either be self signed (with the
warning in the browser and accepting the exception) or one obtained by a
trusted registar. There is a role `generate_key_pair` that creates a self
signed key.

# Requirements
None.

## Role Variables
None

## Role Templates

```
templates/openssl.conf.j2
```

## Role dependencies
None
