# Ettercap
## Overview
Ettercap is one of packet analyzers such as wireshark, tcpdump. It is also called as a packet sniffer because it is capable of intercepting data streams which flow on computer networks, and these captured packets are decoded and analyzed through proper RFCs or protocols by the tool. Therefore, it can be used as a tool for man-in-the-middle (MITM) attacks on local area network (LAN). By default, it has the ability to filter packets, collect passwords, and conduct eavesdropping. Moreover, its features can be extended by custom plugins using its API as it has plugin suppport.

## 



![image](https://user-images.githubusercontent.com/94558947/157911656-5823440b-e4f2-4443-a993-2268d191c7b0.png)



![image](https://user-images.githubusercontent.com/94558947/157911553-5e992dfb-2077-47fa-baba-45b499d59914.png)



https://user-images.githubusercontent.com/94558947/157906680-e8c380f6-9abc-4374-9075-e506e8f8066d.mp4

https://user-images.githubusercontent.com/94558947/157905659-5f66594b-eb3f-45fd-aa77-bf0e0e09e29c.mp4

- echo "Fake Web Site" > index.html

- pgrep -lf apache

- vi /etc/ettercap/etter.conf
- uid, gid -> 0

- echo 1 > /proc/sys/net/ipv4/ip_forward
- cat /proc/sys/net/ipv4/ip_forward

https://securityboulevard.com/2019/10/what-is-dns-cache-poisoning/

https://github.com/svecile/Airgeddon_Notes/blob/main/README.md


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


