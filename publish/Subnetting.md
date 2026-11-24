
Subnetting has superseded [[Legacy Class Addressing]], although conceptually subnetting from whole octets rather then individual bites may be easier.

> Why do we subnet?

Subnetting allows us to split a large network into smaller, more manageable chunks. Chunks may be arranged by device type, their physical location or the service which they provide (all devices in the room/the floor, all printers)


## Unicast Transmission
- When a packet is sent to a single destination IP address (172.16.4.253)

## Broadcast Transmission
- When a packet is addressed to every device on the network
- Packets are structured as the Network ID, and then the Host ID is all 1's
- Used by [[DHCP]] and [[ARP]] protocols

## Multicast Transmission
- Sent to all devices which are members of a multicast group
- Uses the IP address that is given to all member devices
	- eg, all printers on the network


## Broadcast Domains
- Protocols such as [[DHCP]] and [[ARP]] make use of broadcast messages. 
- A broadcast message is sent by a switch to every device on the network (except for the source device.)
- Switches will send broadcast messages between each other
	- eg 1 router, 3 switches with 25 hosts each. Every device will receive the broadcast
	- eg 5 hosts, switch, router, router, switch, 5 hosts. Only the 5 hosts and switch on either side of the routes will receive the broadcast
- Hence we see that routers will not forward broadcasts
