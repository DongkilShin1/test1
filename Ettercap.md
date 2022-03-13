https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

https://www.kali.org/tools/ettercap/

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

## Demo - ARP Poisoning
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

### ARP Poisoning Details in Demo

**ARP Request and ARP Reply/Response**
First, Target1(192.168.163.130-fb-ef) is asking "Who has 192.168.163.2? Tell 192.168.163.130". Ettercap(192.168.163.134-f9-35) is sending response to Target1(192.168.163.130-fb-ef) that "192.168.163.2 is at 00-50-56-fd-0a-5b". And also Ettercap(192.168.163.134-f9-35) is sending message to Target2(192.168.163.2-0a-5b) that "192.168.163.130 is at 00-0c-29-2a-fb-ef". It is normal ARP request and ARP reply. However, when ARP Poisoning is started, Ettercap(192.168.163.134-f9-35) is sending to Target1(192.168.163.130-fb-ef) that "192.168.163.2 is at 00-0c-29-78-f9-35" which is Ettercap itself MAC address and also Ettercap(192.168.163.134-f9-35) is sending to Target2(192.168.163.2-0a-5b) that "192.168.163.130 is at 00-0c-29-78-f9-35". These are fake ARP replies to Target1 and Target2. So, with these information, ARP cache table in Target1(Windows10) and Target2(Gateway) is update as following.

ARP cache table in Target1(Windows10)



ARP cache table in Target2(Gateway)

Thus, these targets send all their traffic to Ettercap and it is able to sniff them.
You can check the captured picture from wireshark as below.

**ARP Request**
When Host A wants to communicate to Host who has IP 192.168.0.1, a broadcast message "MAC address 00:00:00:00:00:00" is sent from Host A to all hosts on the network asking who has "IP 192.168.0.1" 

**ARP Reply**
Then Host D replies with "I have 192.168.0.1 and my MAc address is 02:f2:02:f2:02:f2".

Based on these ARP request and reply, ***ARP cache table*** in Target1(Windows10) and Target2(Gatewa) will be updated.



![image](https://user-images.githubusercontent.com/94558947/158043164-b2d1ad5e-1e0b-449c-b3d1-1def6abbf835.png)





![image](https://user-images.githubusercontent.com/94558947/158044979-45870b00-63f0-40bd-be7b-222ac7d7ee8d.png)


![image](https://user-images.githubusercontent.com/94558947/158044996-a2103382-900b-4de0-b456-844d398d6e10.png)



https://user-images.githubusercontent.com/94558947/158044956-401f34b2-09ac-4f0c-86c8-eb75f7f5ac92.mp4


## Risk Mitigation

