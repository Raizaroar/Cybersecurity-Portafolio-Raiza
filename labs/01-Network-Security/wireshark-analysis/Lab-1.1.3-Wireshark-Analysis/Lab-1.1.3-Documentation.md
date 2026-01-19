# PROJECT OVERVIEW

In this lab, I'll use Wireshark on Kali Linux to capture and analyze traffic between my virtual machines. I'ill perform a realistic scenario: attacking Metasploitable from Kali and capturing all traffic for forensic analysis.

**Real-world scenario:**

I'm an SOC Analyst investigating an attack on a server. I have:

- Kali Linux: attacker simulation
- Metasploitable: Compromised server (victim)
- Wireshark: Tool for capturing evidence of the attack

## Lab Environment

- **Hypervisor:** VirtualBox

- **VM 1 - Kali Linux:**
  - IP: 192.168.56.101
  - Role: Attacker + Packet Analyzer
  - Wireshark installed
  
- **VM 2 - Metasploitable 2:**
  - IP: 192.168.56.102
  - Role: Vulnerable target
  - Services: FTP (vsftpd 2.3.4 with backdoor), SSH, Telnet, HTTP, etc.

- **Network Mode:** Host-Only Adapter (vboxnet0)
- **Isolation:** VMs communicate with each other, isolated from internet

## Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| **Wireshark** | 4.0+ (Kali) | Packet capture and analysis |
| **Kali Linux** | 2024.x | Attacker/Analyzer platform |
| **Metasploitable 2** | N/A | Intentionally vulnerable target |
| **Nmap** | 7.94+ | Port scanning |
| **Netcat** | N/A | Shell connection to backdoor |

Objective

-  Install and configure Wireshark on Kali Linux
-  Capture traffic between attack and victim VMs
-  Analyze real port scanning activity (Nmap)
- Capture and analyze exploitation (vsftpd backdoor)
- Use display filters for forensic analysis
- Follow TCP streams to reconstruct attacks
- Export evidence in pcap format
- Document findings with MITRE ATT&CK mapping

