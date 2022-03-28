# Demo - CVE-2020-0796 (SMBGhost)

The CVE-2020-0796 (SMBGhost) vulnerability causes an integer overflow in the process of dealing with OriginalSize and Offset inside the Srv2!Srv2DecompressData function which processes compressed messages in the Microsoft SMB 3.1.1 (SMBV3) protocol. The vulnerability could result in system failure, privilege escalation, and remote code execution. In this demo, system failure of blue screen is reenacted.

## Demo Scenario
In the scenario, first an attacker search a target by scan network, and after finding the target, the attacker check if the target pc is Windows system and it open SMB port, 445. Then, the attacker check if the user has SMBv3 which is vulnerability enabled with a script. Next, he sends manipulated SMB compress packet to the target. Finally, the attack occurs Blue Screeen in the user's PC.

![image](https://user-images.githubusercontent.com/94558947/160330035-643c247b-eb10-468e-a5c0-c485a6e337fc.png)

### 1.
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

## How does Ettercap work?
Ettercap is basically Unix-like based program. It is installed on Linux, BSD and MacOS. However, Windows is not supported by it. For network interface cards, most network cards can suitable if these works without any problem on OS system. The network card should be promiscuous mode which allows a network interface to pass all traffic through it to CPU for capturing and analyzing data streams. Ettercap is working on wired and wireless local area networks. 

### How to use Ettercap (Example: How to start ARP Poisoning)
Please, refer to the below section, how to start ARP Poisoning in the Demo Section.

### Scenario

![image](https://user-images.githubusercontent.com/94558947/158044372-86817dee-60a7-4bf0-afb3-5516c4338a8b.png)
