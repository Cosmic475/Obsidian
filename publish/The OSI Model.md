Test edit

| OSi Model Layers | TCP/IP Model Layers | Example Protocols                              |
| ---------------- | ------------------- | ---------------------------------------------- |
| 7 - Application  | Application         | DNS, DHCP, SMTP, POP3, IMAP, FTP, HTTP/S, REST |
| 6 - Presentation |                     |                                                |
| 5 - Session      |                     |                                                |
| 4 - Transport    | Transport           | TCP, UDP                                       |
| 3 - Network      | Internet            | IPv4/v6, NAT, ICMP, EGP, EIGRP, OSPF           |
| 2 - Data Link    | Network             | ARP, Ethernet, WLAN                            |
| 1 - Physical     |                     |                                                |
- This is just a model that structures an otherwise complex process
- In reality, each individual protocol is responsible for preparing the data


Layer 1-3 is completed by hardware components within the network such as the NIC in the host, routers and switches


# Layer 1 - Physical

- Includes hardware components such as NIC's (wired/wireless) - note, a device may have multiple NIC's.
- The media such as copped, fibre or wireless.
- Layer 1 protocols are responsible for converting stored data into a stream of signal which can be transmitted across the corresponding media of choice.

# Layer 2 - Data Link

- The data link layer handles all communication across a LAN. It cannot route packet across networks the host is not directly connected to.

## Switches

- Are responsible for forwarding data from one device to another on the same network. 

- Small desktop switches can connect 4-6 devices together and are unmanaged.
- Enterprise switches connecting 24-48 devices together are typically managed and have to be configured manually from a remote computer.
	- The switch has an OS, but no I/O hence the need for remote access.
- Modern switches may embed firewalling and even some routing capabilities

- When a switch receives data from a host for the first time, it makes note of its MAC address, and which physical port the data arrived from.
	- Typically, MAC addresses are held for 300 seconds, and are updated whenever a packet is received again

## Sending local data

Assuming the devices are physically connected on the same network:
1. The data is sent from the originating host to the networks switch
2. The switch recognises the destination hosts MAC address from its MAC address table
3. The switch forwards the data to the destination host

-
> [!note]
> This process does not use IP Addressing!

- At layer 2, we can take advantage of MAC addresses, which are baking into the hardware NIC's within a host. The 48 bit code is typically represented as 6 pairs of hex values:
	- 00-1A-2B-3C-4D-5E-6F
		- Where the first 3 pairs represent the manufacturers ID
		- And the last 3 pairs represent the unique device
		- **Cisco:** use `00:00:0C`, `00:01:42`, or `00:1E:13` as their manufacturers ID's
- MAC addresses have sometimes been colloquially described as "Physical ID's" because they are baked into hardware and are completely fixed.
- They should only be used by devices on the same network


## Error checking
- TBC


# Layer 3 - Network

- Supersedes MAC (physical) addressing by using IPv4/v6 to address logically
- Provides pathfinding for best routing of data to remote networks
	- Anywhere in the world

## Routers

- Routers have at least two physical network interface cards so that it can belong to two networks and bridge between them (act as a gateway)

## Internet Protocol (IP)

- Governs how data is sent across a wide area network, on three assumptions:
	- Connectionless - remote devices do not have to be aware of each other.
	- Best effort - errorless communication is not guaranteed, and requires protocols from a higher level
	- Media independence - the physical media on which the data is transferred is irrelevant 


## Sending data

A source host performs a logical AND operation with the destination IP, source IP and subnet mask to generate two network prefixes, which is then compares
- If the network prefixes (ID's) are the same, it uses its own ARP table to find the MAC address of the destination, and then forwards it to the switch to perform layer 2 trafer
- If the network prefixes (ID's) are not the same, its sends the data to its default gateway (a router) which will then perform NAT translating its private IP address into a public IP address which can be used on the wider internet.

- Data is sent out of the LAN is exactly in the same way, regardless if the destination is on the wider internet, another LAN or even just a subnet
- If data is sent across the wider internet, it will hop between multiple routers which each use Layer 3 protocols to determine where to next send the data. Each router then uses layer 2 protocols (MAC addresses) to physically send data to the next router.

Both hosts and routers will create routing tables to show which next device data should be sent to as the next step to reaching its final destination
- For a host, this will almost always be the default gatewau
- 


## Default gateways

- Must have one NIC with an IP address in the same range as the rest of the LAN.
- Can accept data from within the LAN and forward it outside
- Can route to other networks
- Routers or level 3 switches can be default gateways




# Encapsulation

- Each process and layer takes data on a computer and prepares it to be received by another device. Each layer processes data, and then packages it to be worked on by the layer below, which adds its own header/footer information to the packet, until it eventually becomes a bit stream which is sent across the transmission media.

## Web request example

- A user types in a web address, invoking Layer 7 (application)  
protocols such as HTTP, DNS and DHCP  
- Layer 6 (presentation) encrypts and compresses the data while  
 - Layer 5 (session) authenticates the device and opens the session  
ready to manage the dialogue  


These are known as Application layer protocols (TCP/IP) and  
although they can transform the data, encapsulation does not  
occur until layer 4

Layer 4 (transport) allocates port numbers to be used for  
sending and receiving the data and adds them to the data. In  
this case, the destination device will use port 80 (HTTP) or port  
443 (HTTPS).  
Encapsulation begins here and at layer 4 the data becomes a  
segment – the data is split into smaller parts known as a  
protocol data unit (PDU). Each segment is also given a  
sequence number so that the data can be restored as one file  
at the other end.

Layer 3 (network) adds the source IP which is the device’s own  
IP address. The destination IP address is also added which in  
this case is the IP address of the web server that the user has  
typed in, as returned by DNS. At this point the protocol flag is  
also set to show future devices what protocol is being used – in  
this case it’s TCP, which uses a standard code of 0x06. The  
PDU is now known as a packet.  
Routers are known as Layer 3 devices as they use IP addresses  
to forward the data from the source network to the destination  
network

Layer 2 (data-link) adds the destination MAC address for the  
next directly connected device that the data can be sent to.  
This will eventually be the webserver, but to begin with the  
device is only connected to the default gateway or router.  
Additionally, a CRC checksum is added to the data as a footer.  
This allows the receiving devices to check that the data hasn’t  
been corrupted in any way during transport. The encapsulated  
data is now a frame.

Layer 1 (physical) can now convert the data into the  
appropriate signal type for the media channel and begin to  
transmit the data.




