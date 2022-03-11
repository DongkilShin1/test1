# Ettercap - MITM tool

https://kalitut.com/how-to-use-ettercap/

## Background
[Ettercap](https://en.wikipedia.org/wiki/Ettercap_(software)) is one of packet analyzers such as wireshark, tcpdump. It is also called as a packet sniffer because it is capable of intercepting data streams which flow on computer networks, and these captured packets are decoded and analyzed through proper RFCs or protocols by the tool. Therefore, it can be used as a tool for man-in-the-middle ***(MITM)*** attacks on local area network (LAN). By default, it has the ability to conduct eavesdropping, filter packets and collect passwords. Moreover, its features can be extended by custom plugins using its API as it has plugin suppport. It works by putting its network interface into promiscuous mode (pass its traffic of interface to CPU) and by ***ARP poisoning*** the target machines. It also has the ability to actively or passively find other poisoners on the LAN.

## MITM attack Types
ARP Spoofing
DNS Spoofing
Session Hijacking
SSL Hijacking

## MITM Tools
Hetty
Bettercap
Proxy.py
MITMproxy
Burpsuite

## ARP (Address Resolution Protocol)
ARP  is one of important protocols of the network layer in the OSI Model. It translates physical address (MAC) of a device to logical address(IP), and vice-versa. It allows devices to communicate to each other on LAN by mapping IP address to its MAC address of a device. For example, a device on a network communicates with a gateway (or a AP on a wireless network) using ARP to connect to the Internet.

![image](https://user-images.githubusercontent.com/94558947/157914203-6ae42ac9-c84b-4567-a42a-2901a1b45475.png)


## ARP Request and ARP Reply/Response

### ARP Request
When Host A wants to communicate to Host who has IP 192.168.0.1, a broadcast message "MAC address 00:00:00:00:00:00" is sent from Host A to all hosts on the network asking who has "IP 192.168.0.1" 

### ARP Reply
Then Host D replies with "I have 192.168.0.1 and my MAc address is 02:f2:02:f2:02:f2".

Based on these ARP request and reply, ***ARP cache table*** in Host A will be updated.

![image](https://user-images.githubusercontent.com/94558947/157925062-cdb137dc-3991-4edb-a1c8-fa13abc490dd.png)

## ARP cache

ARP cache is a table of ARP entries that are created whenever a device's MAC address is mapped with its local area IP address for future communication references on a network.
This cache can be ***poisoned (using ARP spoofing)***. The term "poisoned" means spoofed or fake MAC address associated with an IP address.
This poisoning lead to ***Man in the middle attack (MITM)*** which causes data to be intercepted, and tnen modified or stopped.

## ARP Spoofing (ARP cache Poisoing)

[ARP Spoofing](https://en.wikipedia.org/wiki/ARP_spoofing)

https://techgenix.com/understanding-man-in-the-middle-attacks-arp-part1/

ARP Spoofing (aka ARP Poisoning) is a type of attack in which an attacker sends fabricate ARP messages over a local area network in order to link attacker's MAC address with the IP address of other device on a network to achieve a malicious task. If an attacker is able to manage linking of the MAC address of its device with the IP address of any other device on a local area network, this linking leads to ARP Poisoning and allows an attacker to carry out several malicious tasks such as intercepting network traffic, modify and even stop the data captured by putting an attacker in the middle of the communication of the devices (Man In The Middle attack)

![image](https://user-images.githubusercontent.com/94558947/157922929-72c535a1-0d14-41c9-9f07-ea12df69d80e.png)

## Consequence of MITM attacks

Attackers can sniff the packets or intercept the network traffic after successful ARP poisoning. Thus MITM leads indivisuals or companyies to enormous impacts since they can result in financial and reputataion losses. For example, stolen private information and credentials such as usernames and passwords can be used to make unauthorized purchases. These information can be also used to install malware or steal other sensitive information. For this reason, it is critical to protect digital systems to mitigate the risks of MITM attacks.

## Conclusion - Preventing MITM attacks

Identifying MITM attacks is difficlut to detect hacking variant as they occur directly on the target system and hackers do not perform suspicious-looking actions once installed in the middle of the affected connection. However, there are several security practices and techniques to prevent MITM variants.

Secure Internet connections on home or business networks, using effective solutions and reliable authentication solutions.







## DNS cache



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
