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


## Finding a MAC address
---
When a source host is trying to send data to a host it does not know the MAC address of, it broadcasts using MAC address ff.ff.ff.ff.ff. This packet is then picked up by the network switch, which will be programmed to send this packet to every connected port, excluding the one from which the packet originated. 

The NIC of every connected device will pass the packet to the OS of the host, which will compare the requested IP address to the one it currently holds. If they do not match, the packet is silently dropped.

If they do match, the destination host addresses its MAC address to the source host and the exchange is made

This information is then stored within the source hosts ARP table


## ARP Spoofing
---
One major, fundamental flaw in the design of ARP is that it will update its table to responses, even if it didn't send a request
- How could this be exploited?


1. A malicious host embeds themself on the network
2. They scan to discover IP addresses of hosts and a default gateway
3. Forged ARP response packets are distributed, giving its own MAC address
	1. Hosts believe their default gateway is the malicious actor
	2. The genuine default gateway believes the malicious actor is a genuine host
4. Each device communicates with the malicious host, which forwards the packets 


### How is this handled in the modern world
---
- IPv6 uses [[NDP]] which utilises encryption and secure cryptographic keys to verify host identities
- 

