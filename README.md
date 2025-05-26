# Task1
# Nmap Network Scanning &amp; Wireshark Packet Analysis

# 📌 Task Objectives

1.Install Nmap from official website.

2.Find your local IP range (e.g., 192.168.1.0/24).

3.Run: nmap -sS 192.168.1.0/24 to perform TCP SYN scan.

4.Note down IP addresses and open ports found.

5.Optionally analyze packet capture with Wireshark.

6.Research common services running on those ports.

7.Identify potential security risks from open ports.

8.Save scan results as a text or HTML file.

# 🛠️ Tools Used
Nmap - to scan network and ports

Wireshark - to conduct packet analysis

xsltproc - to convert xml file to html file

# 🗺️ Nmap Commands Used
# TCP SYN Scan
nmap -sS 10.0.2.0/24
# Output of scan(.txt format)
nmap -sS 10.0.2.0/24 -oN open_ports_summary.txt  //stored in open_ports_summary.txt
# Output of scan(.html format)
nmap -sS 10.0.2.0/24 -oX result.xml   //No default html format so converted to xml format
xsltproc result.xml -o result.html  //Use xsltproc tool to convert the xml format to html format

# 🦈 Wireshark Analysis
tcp.flags.syn==1 and tcp.flags.ack==0 //filters all the syn requests made by scanner in real time when the -sS nmap scanning is taking place

# 📈 Scan Results Summary
IP's discovered:
10.0.2.2
10.0.2.3
10.0.2.4
10.0.2.15
Open Ports and Services:
IP Address      Open Ports          Services Identified
10.0.2.2        135,445,6646        MSRPC,Microsoft-DS,Unknown
10.0.2.3        135,445,6646        MSRPC,Microsoft-DS,Unknown
10.0.2.4        135,445,6646        MSRPC,Microsoft-DS,Unknown
10.0.2.15       1099,3306,8181      RMIRegistry,MariaDB,Intermapper

# 🔐 Security Risks Identified
Port 135(MSRPC) - Targeted for Ransomware attacks
Port 445(SMB) - Used for lateral movements in Windows Networks
Port 3306(SQL) - Prone to attacks like SQL Injections
Port 8181(Intermapper) - Prone to network topology exposure
