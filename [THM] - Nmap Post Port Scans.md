# TryHackMe - Nmap Post Port Scan

[Room link](https://tryhackme.com/room/nmap04)

--- 

 ## Task 1
  
**No aswer required for complete this task. Just read and understand the introduction about subject.**

--- 

## Task 2

1. Start the target machine for this task and launch the AttackBox. Run nmap -sV --version-light 10.10.208.46via the AttackBox. What is the detected version for port 143?

**Dovecot imapd**

2. Which service did not have a version detected with --version-light?

**rpcbind**

---

## Task 3

1. Run nmap with -O option against 10.10.208.46. What OS did Nmap detect?

**Linux**

---

# Task 4

1. Knowing that Nmap scripts are saved in /usr/share/nmap/scripts on the AttackBox. What does the script http-robots.txt check for?

**disallowed entries**

2.Can you figure out the name for the script that checks for the remote code execution vulnerability MS15-034 (CVE2015-2015-1635) ?

**http-vuln-cve2015-1635**

3. Launch the AttackBox if you haven't already. After you ensure you have terminated the VM from Task 2, start the target machine for this task. On the AttackBox, run Nmap with the default scripts -sC against 10.10.208.46. You will notice that there is a service listening on port 53. What is its full version value?

**9.9.5-9+deb8u19-Debian**

Another method :

```bash
$ dig -t txt -c chaos VERSION.BIND @<IP>
```

4. Based on its description, the script ssh2-enum-algos “reports the number of algorithms (for encryption, compression, etc.) that the target SSH2 server offers.” What is the name of the key exchange algorithms (kex_algorithms) that relies upon “sha1” and is supported by 10.10.208.46?

**diffie-hellman-group14-sha1**

---

## Task 5

1. Terminate the target machine of the previous task and start the target machine for this task. On the AttackBox terminal, issue the command scp pentester@10.10.72.10:/home/pentester/* . to download the Nmap reports in normal and grepable formats from the target virtual machine.

```bash
$ grep https scan*
```

**3**

2. What is the IP address of the system listening on port 8089?

**172.17.20.147**
