
The command to access the HTB VPN is:

~~~
sudo openvpn user.ovpn
~~~

openvpn is the VPN client
user.ovpn is the VPN key which we have downloaded from the internet

~~~
ifconfig
~~~

if we see a "tun" adapter, we know we have connected successfully.

~~~
netstat -rn
~~~
- Allows us to see all available networks.
