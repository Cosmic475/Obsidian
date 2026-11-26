Address Resolution Protocol is used by a device which is attempting to communicate with an IPv4 address it knows is on the same network, but does not have its MAC address.

The source device will broadcast the message to the [[Subnetting#^4581ba|Broadcast Domain]].

The protocol has two main responsibilities:
- Resolving an IPv4 address to a hosts MAC address
- Maintaining an ARP table of mappings between IPv4 and MAC addresses
	- (to minimise the number of ARP calls)

## Cisco Router
---
```
show ip arp
```
- This command will display the ARP table stored within a Cisco router


## Windows PC
---
```
arp -a
```
- Will show the ARP table stored on a windows computer 


## Finding A