# Networking Home Lab

## Project Overview

This project documents the design, configuration, and testing of a small virtual network built using Oracle VirtualBox.

The lab uses an Ubuntu Server system to provide network services to two Windows 11 client machines. The environment was designed to develop practical experience with IP addressing, DHCP, virtual networking, Linux administration, and connectivity troubleshooting.

## Objectives

- Build an isolated virtual network using VirtualBox
- Configure multiple virtual machines on the same internal network
- Configure static and dynamic IPv4 addressing
- Install and configure a DHCP server
- Verify DHCP lease assignment on Windows clients
- Test connectivity between clients and the server
- Troubleshoot network and service configuration issues
- Develop practical Linux and Windows networking skills

## Lab Environment

### Virtualisation Platform

- Oracle VirtualBox 7.2.14

### Virtual Machines

| Device | Operating System | Role |
|---|---|---|
| `NET-SERVER01` | Ubuntu Server 24.04 LTS | DHCP and network services |
| `NET-CLIENT01` | Windows 11 Pro | Client workstation |
| `NET-CLIENT02` | Windows 11 Pro | Client workstation |

## Network Design

The lab uses a dedicated VirtualBox Internal Network named:

`NET-LAB`

`NET-SERVER01` contains two network interfaces:

- NAT interface for external connectivity
- Internal Network interface for communication with lab clients

The Windows clients connect directly to the isolated `NET-LAB` network.

## IP Addressing

| Device / Service | Address |
|---|---|
| Network | `192.168.50.0/24` |
| Subnet Mask | `255.255.255.0` |
| NET-SERVER01 | `192.168.50.10` |
| DHCP Pool | `192.168.50.100 - 192.168.50.200` |
| NET-CLIENT01 | DHCP assigned |
| NET-CLIENT02 | DHCP assigned |

The Ubuntu server uses a static address so that network services remain available at a consistent IP address.

## DHCP

`NET-SERVER01` was configured to provide DHCP services to devices connected to the `NET-LAB` network.

Both Windows clients successfully received IPv4 configuration from the Ubuntu DHCP server.

Detailed DHCP configuration notes are available in the [DHCP Configuration](./Notes/DHCP-Configuration.md) file.

## Client Validation

Both Windows 11 clients were successfully connected to the internal network and verified to receive DHCP configuration from `NET-SERVER01`.

Client-to-server connectivity was confirmed using ICMP ping tests.

Detailed validation information is available in the [Client Validation](./Notes/Client-Validation.md) file.

## Troubleshooting

Several configuration issues were encountered and resolved during the deployment of the DHCP service.

Detailed troubleshooting notes are available in the [Troubleshooting](./Notes/Troubleshooting.md) file.

## Skills Demonstrated

- VirtualBox virtual networking
- IPv4 addressing
- Subnetting
- Static IP configuration
- DHCP configuration
- Linux Netplan
- Linux service management
- Windows network configuration
- Command-line networking tools
- ICMP connectivity testing
- Linux log analysis
- Network troubleshooting
- Windows and Linux administration

## Screenshots

Project screenshots are available in the [Screenshots](./Screenshots) folder.

## Notes

Additional configuration and project notes are available in the [Notes](./Notes) folder.

## Diagrams

Network diagrams are available in the [Diagrams](./Diagrams) folder.

## Future Improvements

This lab will continue to be expanded with additional networking services, routing, DNS configuration, firewall rules, and further connectivity testing.