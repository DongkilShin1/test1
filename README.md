# Ettercap
## Background
[Ettercap](https://en.wikipedia.org/wiki/Ettercap_(software)) is one of packet analyzers such as wireshark, tcpdump. It is also called as a packet sniffer because it is capable of intercepting data streams which flow on computer networks, and these captured packets are decoded and analyzed through proper RFCs or protocols by the tool. Therefore, it can be used as a tool for man-in-the-middle (MITM) attacks on local area network (LAN). By default, it has the ability to conduct eavesdropping, filter packets and collect passwords. Moreover, its features can be extended by custom plugins using its API as it has plugin suppport. It works by putting its network interface into promiscuous mode (pass its traffic of interface to CPU) and by ARP poisoning the target machines. It also has the ability to actively or passively find other poisoners on the LAN.

## ARP (Address Resolution Protocol)
ARP  is one of important protocols of the network layer in the OSI Model. It translates physical address (MAC) of a device to logical address(IP), and vice-versa. It allows devices to communicate to each other on LAN by mapping IP address to its MAC address of a device. For example, a device on a network communicates with a gateway (or a AP) using ARP to connect to the Internet.

![image](https://user-images.githubusercontent.com/94558947/157914203-6ae42ac9-c84b-4567-a42a-2901a1b45475.png)

## ARP Spoofing (ARP cache Poisoing)


## DNS Spoofing (DNS cache Poisoing)







![image](https://user-images.githubusercontent.com/94558947/157911553-5e992dfb-2077-47fa-baba-45b499d59914.png)


## Demo1 - ARP Spoofing
https://user-images.githubusercontent.com/94558947/157906680-e8c380f6-9abc-4374-9075-e506e8f8066d.mp4


## Demo2 - DNS Spoofing
https://user-images.githubusercontent.com/94558947/157905659-5f66594b-eb3f-45fd-aa77-bf0e0e09e29c.mp4

- echo "Fake Web Site" > index.html

- pgrep -lf apache

- vi /etc/ettercap/etter.conf
- uid, gid -> 0

- echo 1 > /proc/sys/net/ipv4/ip_forward
- cat /proc/sys/net/ipv4/ip_forward

https://securityboulevard.com/2019/10/what-is-dns-cache-poisoning/

https://github.com/svecile/Airgeddon_Notes/blob/main/README.md



## Demo1 Description

= Intercept Username/Password with ARP Spoofing

- Kali linux
     
     ifconfig

     route -n

     nmap -sP 192.168.163.0/34

- Windows

     ipconfig

- Kali linux

Ettercap execute

Accept
```
Starting Unified sniffing...
```
Stop sniffing
```
Unified sniffing was stopped
```
Scan Hosts
```
Scanning the whole netmask for 255 hosts
```
Hostlist

Add Target
```
Host 192.168.163.130 added to TARGET1
Host 192.168.163.2 added to TARGET2
```
MITM menu - Start ARP poisoning
```
ARP poisoning victims:
GROUP 1 : 192.168.163.130 00:0C:29:2A:FB:EF
GROUP 2 : 192.168.163.2 00:50:56:FD:0A:5B
```
Start sniffing
```
Starting Unified sniffing
```
- Windows

. Webpage - vulnweb.com

. testphp.vulnweb.com

. singup

. login

- Kali linux

Check contents on Ettercap

## Demo2 Description
= Redirect intended to a website with DNS Spoofing

- Kali linux

cd /var/www/html

cat index.html

service apache2 restart

service apache2 status

. Active: active (running)

vi /etc/ettercap/etter.dns

ARP poisoning stop

dns_spoof start on plugin

. Activating dns_spoof plugin

ARP poisoning start
. Starting Unified sniffing

- Windows

Delete dns cache

. ipconfig /flushdns

Delete web cache on browser

Reconnect to the site

www.yahoo.com



### Evaluation Criteria
#### Presentations
= Background
- adequately explain
. what the tool does
. how it does it
. who users it or want to use it
. why it would be useful
. what is the real-world impact

= Technical merit
. contain an adequate degree of technical content(graph, charts etc)
. key concepts explained?

= Delivery : presentation
. presentation interesting/effective?
. slides clear and visually appealing?
. presentation complete on time?

#### Presentation notes
= Content
make use of a variety of rich content (e.g., hyperlins, code snippets, etc)?

= Technical merit
. contain an adequate degree of technical content(graph, charts etc)
. key concepts explained?

= References
. select and cite appropriate references that would allow the readers
to get up to speed on the topic?
Note, markdown supports footnotes like this:
Some long sentence. [^footnote]
[^footnote]: Test, [Link](https://google.com).
