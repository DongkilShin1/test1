https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

https://www.kali.org/tools/ettercap/

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




![image](https://user-images.githubusercontent.com/94558947/158043164-b2d1ad5e-1e0b-449c-b3d1-1def6abbf835.png)

### Environment




### ARP Poisoning Details in Demo


