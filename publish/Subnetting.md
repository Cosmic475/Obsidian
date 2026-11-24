
Subnetting has superseded [[Legacy Class Addressing]], although conceptually subnetting from whole octets rather then individual bites may be easier.

> Why do we subnet?

Subnetting allows us to split a large network into smaller, more manageable chunks. Chunks may be arranged by device type, their physical location or the service which they provide (all devices in the room/the floor, all printers)


## Unicast Transmission
- When a packet is sent to a single destination IP address (172.16.4.253)

## Broadcast Transmission
- When a packet is addressed to every device on the network
- Packets are structured as the Network ID, and then the Host ID is all 1's
- Used by DHCP and ARP protocols