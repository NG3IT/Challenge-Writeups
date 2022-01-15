# TryHackMe - Attacktive Directory

[Room link](https://tryhackme.com/room/attacktivedirectory)

--- 

 ## Task 1
  
**No aswer is required for this task.**

--- 

## Task 2

1. Install Impacket, Bloodhound and Neo4j

**Just follow the instructions above.**

---

## Task 3

1. What tool will allow us to enumerate port 139/445?

**enum4linux**

2. What is the NetBIOS-Domain Name of the machine?

**THM-AD**

3. What invalid TLD do people commonly use for their Active Directory Domain?

**.local**

---

## Task 4

1. What command within Kerbrute will allow us to enumerate valid usernames?

**userenum**

2. What notable account is discovered? (These should jump out at you)

**svc-admin**

3. What is the other notable account is discovered? (These should jump out at you)

**backup**

---

## Task 5

1. We have two user accounts that we could potentially query a ticket from. Which user account can you query a ticket from with no password?

**svc-admin**

2. Looking at the Hashcat Examples Wiki page, what type of Kerberos hash did we retrieve from the KDC? (Specify the full name)

****
