# DHCP Configuration

This document describes the DHCP setup for the Networking Home Lab.

## DHCP Server

DHCP runs on:

`NET-SERVER01`

The server uses interface `enp0s8` with the static IP address:

```text
192.168.50.10/24
```

DHCP is available only on the `NET-LAB` internal network.

## DHCP Interface

The DHCP interface is configured in:

```text
/etc/default/isc-dhcp-server
```

```text
INTERFACESv4="enp0s8"
```

## DHCP Configuration

The DHCP scope is configured in:

```text
/etc/dhcp/dhcpd.conf
```

```text
subnet 192.168.50.0 netmask 255.255.255.0 {
    range 192.168.50.100 192.168.50.200;
    option subnet-mask 255.255.255.0;
    option domain-name-servers 192.168.50.10;
    default-lease-time 600;
    max-lease-time 7200;
}
```

## Addressing

| Setting     | Value                             |
| ----------- | --------------------------------- |
| Network     | `192.168.50.0/24`                 |
| DHCP Server | `192.168.50.10`                   |
| DHCP Range  | `192.168.50.100 - 192.168.50.200` |
| Interface   | `enp0s8`                          |

Addresses below `192.168.50.100` are available for devices that need static IP addresses.

## Testing the Configuration

Validate the DHCP configuration:

```bash
sudo dhcpd -t -cf /etc/dhcp/dhcpd.conf
```

Restart the DHCP service:

```bash
sudo systemctl restart isc-dhcp-server
```

Check the service status:

```bash
sudo systemctl status isc-dhcp-server
```

The service should show:

```text
Active: active (running)
```

## Client Testing

On each Windows client, run:

```cmd
ipconfig /all
```

The clients should receive an IP address between:

```text
192.168.50.100
```

and:

```text
192.168.50.200
```

The DHCP server should be listed as:

```text
192.168.50.10
```

## Result

The DHCP server automatically assigns IP addresses to Windows clients on the `NET-LAB` network.
