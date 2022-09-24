# NMAP
- [NMAP Command Cheat Sheet](https://www.golinuxcloud.com/nmap-command-in-linux/)

## Domain IP Address Lookup
| Command | Description |
|---|---|
|`nslookup cloudflare.com`|Lookup domain IP address|
||![image](src/nslookup.png)|

## Scan Techniques
| Command | Description |
|---|---|
|`nmap 192.168.1.1 -sT`|TCP connect port scan (Default without root privilege)
||![image](src/tcpscan.png)|
|`nmap 192.168.1.1 -sU`|UDP port scan|
||![image](src/udpscan.png)|

## Host Discovery
| Command | Description |
|---|---|
|`nmap 192.168.1.1 -sP`|Find Live Hosts|
||![image](src/nmap-live-host.webp)|
|`nmap 192.168.1.1 -sA`|Scan and Detect Firewall|
||![image](src/nmap-firewall.webp)|
|`nmap 192.168.1.1 -PN`|Check if Host Protected by Firewall|
||![image](src/nmap-protected.webp)|
|`nmap 192.168.1.1 --iflist`|List Interfaces and Routes|
||![image](src/nmap-iflist.webp)|
|`nmap 192.168.1.0/24 -sn`|	Host Discovery (Disable port scan)|
|`nmap 192.168.1.1 -p-`|Scan Opened Ports|

## OS Detection
| Command | Description |
|---|---|
|`nmap -A -T3 cloudflare.com`| Scan Ports and Services using **Aggresive** mode|
||![image](src/nmap-os-1.webp)|
|`nmap -O cloudflare.com`| Get OS information |
||![image](src/os.png)|

## Service Detection
| Command | Description |
|---|---|
|`nmap -sV cloudflare.com`| Scan Services Only|
||![image](src/sv-nmap.webp)|

## CVE Detection
| Command | Description |
|---|---|
|`nmap -Pn --script vuln cloudflare.com`| Full Vulnerability Scan |
||![image](src/cve.webp)|
|`nmap --script exploit cloudflare.com`| Exploit Using Identified CVE |