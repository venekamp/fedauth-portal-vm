---
layout: index
---

# Introduction
SURFsara is working on the Fedauth-portal project to create a solution
(workaround) for federated access to services from the command line. In the web
world (i.e. browser based) this is already possible through technologies and
implementations like SAML 2.0 and Shiboleth.

The Fedauth-portal integrates a number of different components inorder to
create a portal which is able to provide tokens based on a successful federated
authentication. These tokens can then be further used to authenticate the user
for the requested service. The provisioning of the portal is done through
Ansible. This creates a reliable method of quicky erecting a portal in
which all components are configured correctly. Interested people can clone
the repository and start experimenting with the environment themselves and
understand the configuration of the different components.

In order to provide a quick and self contained environment of the federated
authtentication portal, Vagrant is used to quickly set up a VirtualBox machine
and then use Ansible for provisioning. For this scenario,safe default values
have been choosen that allow for the provisioning without breaking things. For
example, the domainname is example.org and instead of real and validated
certifcated use self signed certificates instead. However, the Ansible scripts
can also be used to provision a machine that has a proper domainname, uses the
SSH key from an existing user, install a real certificate, etc.

The first service for which the federated authentication is implemented is the
iRODS service. More information can be found at:
[fedauth-portal](https://venekamp.github.io/fedauth-portal)

# Caveat: SURFconext
The federated authentication portal makes use of SURFconext for the
authentication part. Since SURFconext is build on SAML 2.0, it means that both
SURFconext and the portal must know about the meta data of each other. During
the provisioning of the portal, all necessary information from SURFconext is
retrieved. However, SURFconect needs to have the meta data of the portal as
well. Not only can the portal not simply copy its meta data over to
SURFconext, but before the portal is accepted as a service provider a
registration process has to be successfully completed. These two things cannot
be provisioned and needs to be done manually for each instrance. Once done,
the portal should operate as expected.

The caveat means that after having provisioned a machine, you will need to
complete the registration at SURFconext for the meta data and release of
required attributes before you will get an fully functional portal.

# Vagrant and VirtualBox


Download image

# Ansible

## Roles

### Apache

### fedauth-portal

### firewall

### geerlingy.ntp

### generate_key_pair

### hosts

### irods

### irods_pam_authentication

### ldap

### oath

### phpldapadmin

### postgresql

### simpleSAMLphp

### ssd

