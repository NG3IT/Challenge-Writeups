# TryHackMe - Nmap Basic Port Scans

[Room link](https://tryhackme.com/room/nmap02)

--- 

 ## Task 1
  
No aswer required for complete this task. Just read and understand the introduction about subject.

--- 

## Task 2

1. Which service uses UDP port 53 by default?

**DNS**

2. Which service uses TCP port 22 by default?

**SSH**

3. How many port states does Nmap consider?

**6 (just lookup upside into the question section)**

4. Which port state is the most interesting to discover as a pentester?

**Open**

---

## Task 3

1. What 3 letters represent the Reset flag?

**RST**

2. Which flag needs to be set when you initiate a TCP connection (first packet of TCP 3-way handshake)?

**SYN**

---

## Task 4

1. Launch the VM. Open the AttackBox and execute nmap -sT <IP> via the terminal. A new service has been installed on this VM since our last scan. Which port number was closed in the scan above but is now open on this target VM?
  
**110**

2. What is Nmap’s guess about the newly installed service?
  
**pop3**
  
---
  
## Task 5
  
1. Launch the VM. Some new server software has been installed since the last time we scanned it. On the AttackBox, use the terminal to execute nmap -sS <IP>. What is the new open port?
  
**6667**
  
2. What is Nmap’s guess of the service name?
  
**irc**
  
---
  
## Task 6

1. Launch the VM. On the AttackBox, use the terminal to execute nmap -sU -F -v <IP>. A new service has been installed since the last scan. What is the UDP port that is now open?
  
**53**

2. What is the service name according to Nmap?
  
**domain**
  
---
  
## Task 7
  
1. What is the option to scan all the TCP ports between 5000 and 5500?

**-p5000-5500**
  
2. How can you ensure that Nmap will run at least 64 probes in parallel?
  
**--min-parallelism=64**
  
3. What option would you add to make Nmap very slow and paranoid?
  
**-T0**
  
---
  
## Task 8
  
**No aswer required. Continu to the next room for complete the nmap learning**
