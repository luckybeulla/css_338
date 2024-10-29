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
