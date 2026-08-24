# Lessons Learned

* `NET-SERVER01` uses NAT for external access and an internal network for lab communication.
* The server uses the static IP `192.168.50.10`, while Windows clients receive addresses through DHCP.
* The DHCP scope must match the server’s subnet: `192.168.50.0/24`.
* Linux and Windows command-line tools helped validate services, addressing, and connectivity.
* VirtualBox Internal Networking provided an isolated and safe lab environment.
* Configuration testing and connectivity checks are important after making changes.
