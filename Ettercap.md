https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

https://github.com/svecile/Airgeddon_Notes/blob/main/README.md

# Ettercap

## What is Ettercap?
[Ettercap](https://en.wikipedia.org/wiki/Ettercap_(software)) is originally one of packet analyzers such as wireshark, tcpdump. However, tt is commonly called as a packet sniffer because it is capable of intercepting data streams which flow on computer networks, and these captured packets are decoded and analyzed through proper RFCs or protocols by the tool. Therefore, it can be used as a tool for man-in-the-middle ***(MITM)*** attacks on local area network (LAN). By default, it has the ability to conduct eavesdropping, filter packets and collect passwords. Moreover, its features can be extended by custom plugins using its API as it has plugin suppport. It works by putting its network interface into promiscuous mode (pass its traffic of interface to CPU) and by ***ARP poisoning*** the target machines. It also has the ability to actively or passively find other poisoners on the LAN.

## How does Ettercap work?
Ettercap is basically Unix-like based program. It is installed on Linux, BSD and MacOS. However, Windows is not supported by it. For network interface cards, most network cards can suitable if these works without any problem on OS system. The network card should be promiscuous mode which allows a network interface to pass all traffic through it to CPU for capturing and analyzing data streams. Ettercap is working on wired and wireless local area networks. 

### How to install Ettercap and What settings to be changed to use
On Kali Linux
```
sudo apt install ettercap-common
```
On Ubuntu
```
sudo apt install ettercap-gtk
```
On Fedora
```
sudo yum install ettercap-gtk
```
Before using it, a few settings should be changed in the conf file.
First, ec_uid and ec_gid must be set to 0 in order for the program to work on behalf of the superuser
:

```
sudo vi /etc/ettercap/etter.conf
```

```
ec_uid = 0 # nobody is the default
ec_gid = 0 # nobody is the default
```

### How to use Ettercap (Example: How to start ARP Poisoning)
Please, refer to the below section, how to start ARP Poisoning in the Demo Section.

## Demo - ARP Poisoning with Ettercap
### Scenario

![image](https://user-images.githubusercontent.com/94558947/158044372-86817dee-60a7-4bf0-afb3-5516c4338a8b.png)

### Environment
- 2 Virtual Machines on VMware
     - Normal User (**Victim**): Windows 10
     - Malicious User (**Attacker**): Kali Linux
- Ettercap installed on Kali Linux
     - Ettercap **Target1**: **Window 10**
     - Ettercap **Target2**: VMware **Gateway**
- Test Web site (**Http**): www.vulnweb.com

### ARP Poisoning Demo Details

**ARP Request and ARP Reply/Response**

1. Target1(W:192.168.163.130-fb-ef) is asking "Who has 192.168.163.2? Tell 192.168.163.130".
2. Ettercap(K:192.168.163.134-f9-35) is sending response to Target1(W:192.168.163.130-fb-ef) that "192.168.163.2 is at 00-50-56-fd-0a-5b". 
3. Also Ettercap(K:192.168.163.134-f9-35) is sending message to Target2(G:192.168.163.2-0a-5b) that "192.168.163.130 is at 00-0c-29-2a-fb-ef". 

It is normal ARP request and ARP reply. However, when ARP Poisoning is started, 

4. Ettercap(K:192.168.163.134-f9-35) is sending to Target1(W:192.168.163.130-fb-ef) that "192.168.163.2 is at 00-0c-29-78-f9-35" which is Ettercap itself MAC address.
5. Also Ettercap(K:192.168.163.134-f9-35) is sending to Target2(G:192.168.163.2-0a-5b) that "192.168.163.130 is at 00-0c-29-78-f9-35".
 
These are fake ARP replies to Target1 and Target2. You can check the captured picture from wireshark as below.

![image](https://user-images.githubusercontent.com/94558947/158045704-7512efa8-9eb9-46b1-a9c1-1a8c3941077d.png)

So, with these information, ARP cache table in Target1(Windows10) and Target2(Gateway) is updated as following.

ARP cache table in Target1(Windows10)

| IP            | MAC               |
| ------------- |:-----------------:|
| 192.168.163.2 | 00-0c-29-78-f9-35 |
| 192.168.163.134| 00-0c-29-78-f9-35|

ARP cache table in Target2(Gateway)
| IP            | MAC               |
| ------------- |:-------------:|
| 192.168.163.130| 00-0c-29-78-f9-35|
| 192.168.163.134| 00-0c-29-78-f9-35|

Thus, these targets send all their traffic to Ettercap and it enables Ettercap to sniff them.

Here is also ARP table (Before and After ARP Poisoning) captured on Target1(Windows10)

![image](https://user-images.githubusercontent.com/94558947/158046330-034790d8-80d8-4802-a019-7b2db4a9fe74.png)

### How to start ARP Poisoning

These are steps to proceed ARP Poisoning and sniffing on Ettercap from scratch. You can refer to 2 min demo video at the bottom to know the whole process.

![image](https://user-images.githubusercontent.com/94558947/158043164-b2d1ad5e-1e0b-449c-b3d1-1def6abbf835.png)

## Risk Mitigation

For the prevention methods on security issues, there are several things. First, before logging on websites, you should check if the websites are using HTTPS in the URL. Second, it is better to use secured networks using encrypt protocols like VPN. Plus, you can implement some security solutions or equipment such as IDS(Intrusion Detection Systems) and attacker detection software like ARPcop(Ettercap plugin), etc. Lastly, it is recommended that users keep eyes on security web sites updated with latest information like NVD(NIST), OWASP.org, etc.

## References

https://www.kali.org/tools/ettercap/

https://kalitut.com/how-to-use-ettercap/

https://techgenix.com/Understanding-Man-in-the-Middle-Attacks-ARP-Part2/

https://www.comparitech.com/blog/information-security/arp-poisoning-spoofing-detect-prevent/

## Demo Video

https://user-images.githubusercontent.com/94558947/158044956-401f34b2-09ac-4f0c-86c8-eb75f7f5ac92.mp4
