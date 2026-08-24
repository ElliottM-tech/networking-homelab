# Client Validation

This document summarizes the network validation completed on the Windows 11 clients.

## Client Devices

The lab contains two Windows 11 Pro clients:

* `NET-CLIENT01`
* `NET-CLIENT02`

Both clients are connected to:

```text
Internal Network -> NET-LAB
```

## DHCP Validation

On each client, network configuration was checked using:

```cmd
ipconfig /all
```

The clients successfully received:

* An IP address from the `192.168.50.100 - 192.168.50.200` DHCP range
* Subnet mask `255.255.255.0`
* DHCP server `192.168.50.10`

`NET-CLIENT01` received:

```text
192.168.50.100
```

## Hostname Validation

The client hostname was checked using:

```cmd
hostname
```

The configured hostnames are:

```text
NET-CLIENT01
NET-CLIENT02
```

## Connectivity Testing

Connectivity to `NET-SERVER01` was tested using:

```cmd
ping 192.168.50.10
```

Both clients successfully received replies from the server.

## Result

Both Windows clients successfully:

* Connected to the `NET-LAB` network
* Received DHCP configuration from `NET-SERVER01`
* Communicated with the Ubuntu server
* Used the correct hostnames and network settings
