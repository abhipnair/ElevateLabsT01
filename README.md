# ElevateLabs Cybersecurity Internship 2025 - Day 01

## Task: Network Reconnaissance using Nmap

### 🔧 Tool Used
**Nmap** (Network Mapper)  
A powerful open-source tool used for network discovery and security auditing. It can detect live hosts, open ports, services, versions, and operating systems.

### 🎯 Objective
Perform a detailed scan on the subnet `172.20.10.2/28` to identify active hosts, open ports, running services, and OS details.

---

## 📡 Scan Summary

| IP Address     | MAC Address           | Open Ports         | Services & Versions                                          |
|----------------|-----------------------|---------------------|---------------------------------------------------------------|
| 172.20.10.1    | E8:10:72:2D:1E:62     | 21, 53, 49152, 62078| FTP (tcpwrapped), DNS (generic), Unknown (tcpwrapped)        |
| 172.20.10.2    | Unknown               | None                | All 1000 ports closed                                         |
| 172.20.10.3    | 08:00:27:ED:BE:6A     | 21, 22, 80          | FTP (vsftpd 3.0.5), SSH (OpenSSH 8.2p1), HTTP (Apache 2.4.41) |
| 172.20.10.5    | D2:F7:13:54:0F:23     | None                | All 1000 ports closed                                         |

---

## 📝 Observations

- **Live Hosts Detected**: 4 hosts responded to ping (`-sn`).
- **Host 172.20.10.3**: Most informative – revealed web service (CTF challenge), SSH, and FTP.
- **Host 172.20.10.1**: Unusual high ports open (49152, 62078) – possibly iOS sync or RPC.
- **tcpwrapped Services**: Some services don’t reveal banners, likely hardened.
- **OS Detection**:
  - Host .3: Likely Linux 5.x series (~98%)
  - Hosts .1 and .5: Inconclusive
- **Filtered Ports**: Host .3 had 969 filtered ports (possible firewall).
- **Stealth Note**: Avoid `-A` in real environments due to heavy fingerprinting.

---

## ⚠️ Disclaimer
The `-A` (Aggressive) scan provides comprehensive details but leaves noticeable footprints on the network. Use with caution in production or stealth operations.

