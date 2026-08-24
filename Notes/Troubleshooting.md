# Troubleshooting

This document summarizes the main issues encountered during the Networking Home Lab.

## DHCP Service Failed to Start

The DHCP service initially failed because the configuration did not include the `192.168.50.0/24` network.

The logs showed:

```text
No subnet declaration for enp0s8 (192.168.50.10)
Not configured to listen on any interfaces
```

A subnet declaration was added to `/etc/dhcp/dhcpd.conf`, then the configuration was tested and the service restarted:

```bash
sudo dhcpd -t -cf /etc/dhcp/dhcpd.conf
sudo systemctl restart isc-dhcp-server
sudo systemctl status isc-dhcp-server
```

The service then showed:

```text
Active: active (running)
```

## Windows 11 Setup Network Issue

The Windows clients received DHCP addresses but required internet access during installation.

A temporary NAT adapter was added to each client. After setup was complete, the NAT adapter was removed and the clients were returned to:

```text
Internal Network -> NET-LAB
```

Connectivity was then tested using:

```cmd
ipconfig /all
ping 192.168.50.10
```

Both clients received DHCP addresses and communicated successfully with `NET-SERVER01`.

## Key Takeaways

* Review service logs when troubleshooting.
* Validate configuration files before restarting services.
* Ensure DHCP subnet declarations match the server network.
* Remove temporary network adapters after setup.
* Test DHCP and connectivity after making changes.
