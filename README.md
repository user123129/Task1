# Task1
# Nmap Network Scanning &amp; Wireshark Packet Analysis

# 📌 Task Objectives

1.Install Nmap from official website.<br>
2.Find your local IP range (e.g., 192.168.1.0/24).<br>
3.Run: nmap -sS 192.168.1.0/24 to perform TCP SYN scan.<br>
4.Note down IP addresses and open ports found.<br>
5.Optionally analyze packet capture with Wireshark.<br>
6.Research common services running on those ports.<br>
7.Identify potential security risks from open ports.<br>
8.Save scan results as a text or HTML file.<br>

# 🛠️ Tools Used
Nmap - to scan network and ports<br>
Wireshark - to conduct packet analysis<br>
xsltproc - to convert xml file to html file<br>

# 🗺️ Nmap Commands Used
1.TCP SYN Scan<br>
nmap -sS 10.0.2.0/24

2.Output of scan(.txt format)<br>
nmap -sS 10.0.2.0/24 -oN open_ports_summary.txt  //stored in open_ports_summary.txt

3.Output of scan(.html format)<br>
nmap -sS 10.0.2.0/24 -oX result.xml   //No default html format so converted to xml format<br>
xsltproc result.xml -o result.html  //Use xsltproc tool to convert the xml format to html format

# 🦈 Wireshark Analysis

tcp.flags.syn==1 and tcp.flags.ack==0 //filters all the syn requests made by scanner in real time when the -sS nmap scanning is taking place

# 📈 Scan Results Summary

IP's discovered:

10.0.2.2<br>
10.0.2.3<br>
10.0.2.4<br>
10.0.2.15

Open Ports and Services:

|  IP Address  |  Open Ports      |  Services Identified              |

|  10.0.2.2    |  135,445,6646    |  MSRPC,Microsoft-DS,Unknown       |<br>
|  10.0.2.3    |  135,445,6646    |  MSRPC,Microsoft-DS,Unknown       |<br>
|  10.0.2.4    |  135,445,6646    |  MSRPC,Microsoft-DS,Unknown       |<br>
|  10.0.2.15   |  1099,3306,8181  |  RMIRegistry,MariaDB,Intermapper  |

# 🔐 Security Risks Identified

Port 135(MSRPC) - Targeted for Ransomware attacks<br>
Port 445(SMB) - Used for lateral movements in Windows Networks<br>
Port 3306(SQL) - Prone to attacks like SQL Injections<br>
Port 8181(Intermapper) - Prone to network topology exposure
