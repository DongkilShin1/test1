# Demo - CVE-2020-0796 (SMBGhost)

The CVE-2020-0796 (SMBGhost) vulnerability causes an integer overflow in the process of dealing with OriginalSize and Offset inside the Srv2!Srv2DecompressData function which processes compressed messages in the Microsoft SMB 3.1.1 (SMBV3) protocol. The vulnerability could result in system failure, privilege escalation, and remote code execution. In this demo, system failure of blue screen is reenacted.

## Demo Scenario
In the scenario, first, an attacker searches a target by scan network, and after finding the target, the attacker checks if the target pc is Windows system and it open SMB port which is 445 port. Then, he checks if the user has SMBv3 which is vulnerability enabled with a script. Next, he sends manipulated SMB compress packet to the target. Finally, the attack occurs Blue Screeen in the user's PC.

![image](https://user-images.githubusercontent.com/94558947/160330035-643c247b-eb10-468e-a5c0-c485a6e337fc.png)

### 1. Search a target and check SMB port

**1.1 Scan hosts**

```
nmap -sP 192.168.163.0/24
```
![image](https://user-images.githubusercontent.com/94558947/160330817-cd520b5e-7cb8-4f9c-95fe-aab55ac674d4.png)

**1.2 Check OS system and ports**

```
nmap -O -sV 192.168.163.135
```
![image](https://user-images.githubusercontent.com/94558947/160330983-c9135bb7-bdea-49ff-8b38-369a85c0a9fb.png)

### 2. Check vulnerability with python script

The attacker checks with python script whether the target has SMBv3 enabled. 

![image](https://user-images.githubusercontent.com/94558947/160342760-43cc9038-3e36-4566-9d86-ff337fce9f99.png)

```
python3 scanner.py 192.168.163.135
```

### 3. Attack vulnerability with python script

The attacker sends the manipulated SMB compress packet to target. At first, the victim's pc is still alive.

![image](https://user-images.githubusercontent.com/94558947/160342523-1ce6ab35-064a-4a86-9682-00294e380100.png)

 ```
python3 crash.py 192.168.163.135
```

### 4. Blue Screen on target PC

Finally, it occurs blue screen on the victim's PC through the attack.

![image](https://user-images.githubusercontent.com/94558947/160342620-d9820b07-041b-4069-ae58-3505f7d7b5a7.png)


