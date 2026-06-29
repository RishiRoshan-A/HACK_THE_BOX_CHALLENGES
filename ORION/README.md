# RECON 

Lets start with our nmap scan 

lets scan for all open ports 

![img](1.png)


We Found two Open ports 22 ssh and 80 http , lets perform service verision scan and default script scan on them 

![img](2.png)

by accessing the ip on browser found the origin name as orion.htb , lets add that our /etc/hosts 

![img](3.png)

Lets visits the service running on port 80 as orion.htb

![img](4.png)

# ENEMURATION 

Lets use gobuster to enemurate the web direcotries 

![img](5.png)

We found a intresing Directory named admin , lets access that 

![img](6.png)

on below notice that we got information that  the page is made up craft cms and its verison is 5.6.16 , lets use exploitdb to search for the availabel exploit for this verison 

# EXPLOITATION 

![img](7.png)

dowwnloaded the code and tried running but it does not seems to be working , so lets search for metasploit modules for craft cms 

![img](8.png)

found our exploit , 

set RHOSTS , LHOSTS , and run the exploit 

![img](9.png)

We successfully got the reverse shell 

after visiting some files and directories , in craft directory found an .env file , which containing username and password for sql database 

![img](10.png)

lets access the  database using the username and password we found 

![img](11.png)

in orion database there is a table named users , lets list all the contents from the table 

![img](12.png)

we found the user adam and password in hash format , lets use john to crack the hash 

![img](13.png)

now we found the username and password and we know that ssh port is open , lets use this credentials to loing into ssh 

![img](14.png)

list the found , we found the user.txt file 

![img](15.png)

# PRIVILEGE ESCLATION 

Lets check the any ports that running internally 

![img](16.png)

we found the telnet is running internally , lets check the telnet verison 

![img](17.png)

lets do a search for telnet verison 2 cves 

found an cve to esclate our privilege to root 

![img](18.png)

![img](19.png)

We successfully got the root shell 

lets visits the root.txt file 

![img](20.png)


We successfully found the user flag and the root flag 

------------------------------------------------------------------THE END--------------------------------------------------------------------






