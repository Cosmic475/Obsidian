
# Open-Source intelligence
OSINT

- Private and public keys found in code - Github, stack overflow etc


# Infrastructure Enumeration

- We use tools such as DNS to create a map of the clients servers and hosts to understand their structure
- Take notes of hosts and IP addresses - compare them to our scope
- Begin determining the companies security measures (firewalls, web app firewalls) which may trigger alarms

- When enumerating internally, we may [[Password Spraying|password spray]], (using one password to attempt to authenticate one of many usernames) to get an initial foothold in the network

# Service Enumeration

- Identify services running on the network, what version it is running and importantly what it is used for on the network
- Security vulnerabilities in outdated versions can then be researched and exploited
- Admins often dont update software which may break the network, instead remaining with outdated versions which may have one or two vulnerabilities
- Internal tests often yield more results, as admins determine that internal software is not accessible from the internet and so a few vulnerabilities are not of concern


# Host Enumeration

- Port identification
- Examine the internal of hosts and servers, looking for files
- Outdated operating systems and services with vulnerabilities

# Pillaging

In the post exploitation stage:
- collecting sensitive information from hosts which are already exploited (names, customer data)
- May be used in lateral movement or to escalate our privileges



