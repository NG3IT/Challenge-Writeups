# [THM] - Phishing Emails 1

[Room link](https://tryhackme.com/room/phishingemails1tryoe)

---

## Task 1 

**No answer required. Just start the machine attached.**

---

## Task 2

1. Email dates back to what time frame? 

**1970s**

## Task 3

1. What port is classified as Secure Transport for SMTP?

**465**

2. What port is classified as Secure Transport for SMTP?

**993**

3. What port is classified as Secure Transport for POP3?

**995**

---

## task 4

1. What port is classified as Secure Transport for POP3?

**Return-path**

2. What port is classified as Secure Transport for POP3?

**http://www.arin.net/**

---

## Task 5 

1. In the above screenshots, what is the URI of the blocked image?

**https://i.imgur.com/LSWOtDI.png**

2. In the above screenshots, what is the name of the PDF attachment?

**Payment-updateid.pdf**

3. In the attached virtual machine, view the information in email2.txt and reconstruct the PDF using the base64 data. What is the text within the PDF?

**Use this command as follow for decode the attachment encoded in base64 :**

**base64 -d email2.txt > decode**

**Finally, you just need to open the decode file with chrome are something else for open pdf file for get the flag.**

---

## Task 6

1. What trusted entity is this email masquerading as?

**Open the email3's file with Thunderbird. You can see the answer on the from field : "Home depot"**

2. What is the sender's email?

**support@teckbe.com**

3. What is the subject line? 

**Take the string in the subject section "=?UTF-8?B?T3JkZXIgUGxhY2VkIDogWW91ciBPcmRlciBJRCBPRDIzMjE2NTcwODkyOTEgUGxhY2VkIFN1Y2Nlc3NmdWxseQ==?="**

**Now you need to delete the following substring at the original string "=?UTF-8?B?" and you can process to decode with this following command :**

**echo "T3JkZXIgUGxhY2VkIDogWW91ciBPcmRlciBJRCBPRDIzMjE2NTcwODkyOTEgUGxhY2VkIFN1Y2Nlc3NmdWxseQ==?=" | base64 -d**

**Order Placed : Your Order ID OD2321657089291 Placed Successfully**

4. What is the URL link for - CLICK HERE? (Enter the defanged URL)

**Copy the link associated with the "CLICK HERE" button and change http to hxxp and add [] near "."**

**This gives this result :**

**hxxp://t[.]teckbe[.]com/p/?j3=EOowFcEwFHl6EOAyFcoUFVTVEchwFHlUFOo6lVTTDcATE7oUE7AUET==**

---

## Task 7 

1. What is BEC?

**Business Email Compromise**
