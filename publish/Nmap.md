~~~
Parzii@htb[/htb]$ nmap 10.129.42.253
~~~

Scans the most common 1000 ports, all of which are TCP only.

The State heading tells us if the ports are open. Occasionally, we will see "filtered" when a firewall is only allowing access from specific addresses

The service heading tells us which protocol is typically associate with the port is has highlighted. However, this is only a guess and may not be accurate (using defaults). We can get NMap to probe these services to confirm what protocols may actually be running.



A more advanced scan looks like this:
~~~
Parzii@htb[/htb]$ nmap -sV -sC -p- 10.129.42.253
~~~

-sV tells nmap to do an indepth version scan, fingerprinting the service and comparing it to its comprehensive database.

-sC tells nmap to use scripts to obtain more detailed information

-p- tells nmap to scan ALL 65,535 TCP ports


