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
In case you do not have an environment in which you can easily create VMs or
you wish to keep things local when trying out the provisioning, you
can use Vagrant to create a VirtualBox machine. All that need to be done is to
start the VM with:

    `vagrant up`

In case the VM is nolonger needed it can be
destroyed with:

    vagrant destroy -f

Access to this VM is achieved with:

    vagrant ssh

## Vagrant base image
When Vagrant creates the VirtualBox VM, it needs a base image from which a new
image is derived and used for the creation of the VM. Any `CentOS7.2` image
could be used. However, the `centos72-vbox-ga` image has the VirtualBox Guest
Additions installed. Although the provided Ansible scripts do not depend on
this feature, it might be worth having. The `centos72-vbox-ga` base image can
be downloaded from: [SURFdrive]()

# Ansible
The first step of getting a working environment is creating the virtual
machine. This gives you a very basic image in which you can login into. The
components that make up the portal are not there yet. The VM needs to be
provisioned first. Ansible is used for this. It is recommened to use at least
version 2.1.

The different compontents are provisioned in diffrent roles. Listed below are
all the roles used and their paramaters are explained.

| [apache](role-apache) | [hosts](role-hosts) | [phpldapadmin](role-phpldapadmin) |
| [fedauth-portal](role-fedauth-portal) | [irods](role-irods) | [postgresql](role-postgresql) |
| [firewall](role-firewall) | [irods_pam_authentication](role-irods_pam_authentication) | [simpleSAMLphp](role-simpleSAMLphp) |
| [geerlingguy.ntp](role-geerlingguy.ntp.html) | [ldap](role-ldap) | [sssd](role-sssd) |
| [generate_key_pair](role-generate_key_pair) | [oath](role-oath) | |
