---
layout: index
---

# Ansible Role: firewall
If your machine in running in the cloud or any loaction where it is publically
accessible, you would most likely want a mininmal firewall. This role provides
for a simple firewall configuration. Two types of rules can be configured:

    1. allowing traffic from a source ip address to a destination port;
    2. allowing traffic from any source to a destination port.

Each rule has it own assiciated variable.

The fire wall is setup only in case the `ansible_virtualization_type` does not
match "virtualbox". Generally, when using VirtualBox, it means that the VM is
run locally on your laptop. Most likely the VM has been configured to use nat.
In case the Vagrant has been used to provision a VirtualBox machine, you have
a local machine with natting and thus having a firewall with these simple
rules does not provide for any additional security.

## Requirements
None.

## Role Variables
The below listed variables are in use by the role. See also
`defaults/main.yml`.

### ❙ allowed_ip_addresses
The setup of the firewall allows to filter on source ip address range with a
destination port. For example on network: 10.0.0.0/24 and to destination
port 22. The allowed_ip_addresses is a list that hold these values.

```
allowed_ip_addresses: [ ]
```

The list elements of allowed_ip_addresses have two key value pairs:

| key        | Description                                    |
| ---------- | ---------------------------------------------- |
| ip_address | source address from which to allow access from |
| dest_port  | destination port to allow access to            |

---

### ❙ allowed_ip_addresses
The setup of the firewall is also capable of opening up a port for any
access. For example allow the world to access the https (443) port. In
which case only the port number is necessay.

```
open_ports: [ ]
```

### Example
Setting up the firewall with access from your VPN (10.0.2.0/24 and
10.0.16.0/24) to SSH and allow general access to HTTPS:// is accomplished by
the below values.

```
---
allowed_ip_addresses:
  - { ip: 10.0.2.0/24,  dest_port: 22 }
  - { ip: 10.0.16.0/24, dest_port: 22 }
open_ports:
  - 443
```

## Role Templates
```templates/iptables.j2```

## Role Dependencies
None.

