
Subnetting has superseded [[Legacy Class Addressing]], although conceptually subnetting from whole octets rather then individual bites may be easier.

> Why do we subnet?

Subnetting allows us to split a large network into smaller, more manageable chunks. Chunks may be arranged by device type, their physical location or the service which they provide (all devices in the room/the floor, all printers)

Why do we subnet?


## Broadcast Storm
---
Critical network protocols such as [[ARP]] and [[DHCP]] require broadcasts to identify hosts on a network. However, Ethernet Layer 2 lacks a TTL on packets, and so they can often be circulated indefinitely - IF a loop exists between three or more switches [[Smurf]] and [[Fraggle]] attacks may also attempt to exploit this if a particularly large network has been found.


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




## Calculating network information
> Even a single IP address and its subnet mask can tell you how many potential hosts are on the network, the broadcast address and network ID

### Calculating the network ID
---
- Perform a binary AND operation with the IP address and mask. The result is your network ID

### Calculating the broadcast address
---
IP Address: 10.150.168.180/27
(Network Mask): 255.255.255.224

| IP address        | 10. | 150. | 168. | 1   | 0   | 1   | 1   | 0   | 1   | 0   | 0   |
| ----------------- | --- | ---- | ---- | --- | --- | --- | --- | --- | --- | --- | --- |
| Network Mask      | 255 | 255  | 255  | 1   | 1   | 1   | 0   | 0   | 0   | 0   | 0   |
| Broadcast address | 10. | 150. | 168  | 1   | 0   | 1   | 1   | 1   | 1   | 1   | 1   |
- All bits in the original IP address after the network mask become 1's
> = 10.150.168.191

### Calculating IP Range
---
Any IP between the network ID and broadcast address is valid and on the same network

