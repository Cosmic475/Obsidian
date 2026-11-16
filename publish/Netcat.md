A great tool for interacting with TCP/UDP ports. 
We primarily use it for connecting to shells, but it can also be used to connect to any listening port and interact with the services it provides.


# Banner grabbing

~~~
netcat 10.10.10.10 22

SSH-2.0-OpenSSH_8.4p1 Debian-3
~~~

In this example, we use netcat to "Grab the banner" and identify that as we suspected, SSH is running on port 22 of this host.
