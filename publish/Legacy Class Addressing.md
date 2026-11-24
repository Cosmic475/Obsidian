An agreement called RFC 1918 was reached in 1996 to reserve certain blocks of IP addressed. This was needed due to the limited nature of IPv4.

Essentially, when establishing a network and IP was selected based on the number of hosts the admin expected would use the network, from the table below.


| Class | Address Range               | Total Networks | Hosts per Network | Leading Identifier | Network Address Segment (Octets) |
| ----- | --------------------------- | -------------- | ----------------- | ------------------ | -------------------------------- |
| A     | 0.0.0.0 - 127.255.255.255   | 128            | 16,777,214        | 0                  | 1                                |
| B     | 128.0.0.0 - 191.255.255.255 | 16,384         | 65,534            | 10                 | 2                                |
| C     | 192.0.0.0 - 223.255.255.255 | 2,097,152      | 254               | 110                | 3                                |
| D     | 224.0.0.0 - 239.255.255.255 | 268,435,456    | N/A               | 1110               | 4                                |
| E     | 240.0.0.0 - 255.255.255.255 | 268,435,456    | N/A               | 1111               | 4                                |



- Why does this system only allow for 128 Class A networks and not the 256 we would typically expect? The first bit of a Class A address is always a 0 - this is its identifier, leaving the other 7 bits of the first octal (which is also the network mask) to be the network ID

- How do we calculate the total number of networks and the number of hosts per network?
	- Total networks - Subtract the number of bits in the leading identifier from the number of bits used in the network address segment. 2^ your result is the number of networks
	- Hosts per network - 2^ the number of bits in the host segment of the IP address - 16 in class B or 24 in class C. We then subtract two from the final answer because
		- The first host ID (NetworkID.0) is used to identify the network, and is used in NAT
		- The last host ID (NetworkID.255) is the broadcast address for the network



Class D was reserved for multicast groups, where multiple hosts would share a common IP address rather then individually identifying themselves

Class E was reserved for future experimentation and reserved IP's
- Interestingly, these IP addresses are still out of range, despite us al