Performing reconnaissance on the local network to discover open ports on connected devices.

Tools used:
- nmap
- wireshark
- ARCH LINUX

Scan execution:

- ip a
Finds Local IP range

- sudo nmap -sS <IP address> -oN local_scan.txt
Performs nmpa scan and saves it to a .txt file

- sudo wireshark
Packet capture analysis using the wireshark tool.

Scan Results Summary:

192.168.18.1 ==	 22, 80, 443, 8099	==	 Nokia Solutions
192.168.18.2 ==  22	==			 Nokia Solutions
192.168.18.3 ==  9080		==		 (Filtered) Unknown
192.168.18.4 ==	 8008, 8009, 8443, 9000	 ==	 Vantiva USA
192.168.18.5 ==	 135, 139, 445 ==  Intel Corp
192.168.18.9 ==  7000, 8008, 8009, 8443, 9000 == Qingdao Intelligent
192.168.18.16 == 	6881 ==		 Intel Corp


Wireshark Analysis:

Display Filters Used:

SYN packets sent by Nmap: tcp.flags.syn == 1 and tcp.flags.ack == 0
SYN-ACK replies (open ports): tcp.flags.syn == 1 and tcp.flags.ack == 1
RST replies (closed ports): tcp.flags.reset == 1

Observations:

- Port 8099 on .1 is unknown - potentially risky.
- Port 6881 on .16 indicates BitTorrent traffic.
- Multiple web services exposed (8008, 8443).

Security Insights:

- Open SMB(Windows File Sharing) on .5 may be exploitable.
- Telnet (23) filtered - firewalled. Telnet is blocked which is a good practice. 
