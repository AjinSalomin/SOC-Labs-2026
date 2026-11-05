# Nmap

## Overview

I completed the Nmap room on TryHackMe as part of my cybersecurity and SOC Analyst learning journey

This room helped me understand how Nmap can be used for network discovery, port scanning, service enumeration, OS detection, and vulnerability assessment.

## Topics Covered

* Nmap basics
* Host discovery
* Port scanning
* TCP and UDP scans
* SYN scans
* NULL, FIN and Xmas scans
* Service and version detection
* OS detection
* NSE (Nmap Scripting Engine)
* Firewall and IDS evasion techniques
* Nmap output formats
* Vulnerability scanning

## Commands Practiced

#### Basic scan
nmap <target>

#### Scan specific ports
nmap -p 22,80,443 <target>

#### Scan all 65535 ports
nmap -p- <target>

#### Service and version detection
nmap -sV <target>

#### OS detection
nmap -O <target>

#### Aggressive scan
nmap -A <target>

#### SYN scan
nmap -sS <target>

#### UDP scan
nmap -sU <target>

#### Default NSE scripts
nmap -sC <target>

#### Save output
nmap -oN scan.txt <target>

