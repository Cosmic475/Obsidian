
There are two categories of port: Transmission Control Protocol and User Datagram Protocol

TCP is connection oriented - a connection between client and server must be established before any data can be sent. The server must be in a  listening state awaiting connection requests.

UDP does not require connection prior to data transfer, which makes it suited to time-sensitive tasks as it is faster. However, it will not guarantee data delivery and so error handling will need to be done at the application level.

The first 1-1023 ports are reserved for privileged services

Port 0 is reserved for TCP/IP networking. Inputting this will be treated as a wild card and will bind with the next available port above 1024


| Port(s)         | Protocol              |
| --------------- | --------------------- |
| `20`/`21` (TCP) | `FTP`                 |
| `22` (TCP)      | [[SSH]]               |
| `23` (TCP)      | `Telnet`              |
| `25` (TCP)      | `SMTP`                |
| `80` (TCP)      | [[HTTP]]              |
| `161` (TCP/UDP) | `SNMP`                |
| `389` (TCP/UDP) | `LDAP`                |
| `443` (TCP)     | `SSL`/`TLS` (`HTTPS`) |
| `445` (TCP)     | `SMB`                 |
| `3389` (TCP)    | [[RDP]]               |
| 443             | [[HTTPS]              |

- However, these are only the standard allocations and theoretically a network admin could ignore this convention completely. 

Cheat sheets here
https://www.stationx.net/common-ports-cheat-sheet/
https://web.archive.org/web/20240315102711/https://packetlife.net/media/library/23/common-ports.pdf