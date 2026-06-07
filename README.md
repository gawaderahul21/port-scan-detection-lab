# Port Scan Detection Lab

## Project Overview

This project demonstrates how to:

- Perform Nmap reconnaissance
- Capture scan traffic using Wireshark
- Detect SYN scans using iptables
- Analyze packet-level evidence
- Understand attacker and defender perspectives

## Lab Environment

| Component | Details |
|------------|---------|
| Attacker | Kali Linux |
| Target | Ubuntu 22.04 |
| Network | VirtualBox NAT |
| Tools | Nmap, Wireshark, iptables |

## Scans Performed

### SYN Scan

```bash
sudo nmap -sS 10.0.2.5
```

### Version Detection

```bash
sudo nmap -sV 10.0.2.5
```

### OS Detection

```bash
sudo nmap -O 10.0.2.5
```

### Aggressive Scan

```bash
sudo nmap -A 10.0.2.5
```

## Results

Open Ports:

- 22/tcp (SSH)
- 80/tcp (HTTP)

Services Detected:

- OpenSSH 9.6p1
- Apache 2.4.58

## Wireshark Analysis

Filter Used:

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

## IDS Detection

iptables rule:

```bash
sudo iptables -A INPUT -p tcp --syn -j LOG --log-prefix "PORT_SCAN: "
```

## Screenshots

See the screenshots folder.

## Author

Rahul Gawade
