***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## Cookies and cross-site scripting (XSS) ##

### Part 1: Cookies ###

1. Initial cookies for cs338.jeffondich.com - their names and values

   ***Yes, there is a cookie for the domain cs338.jeffondich.com/fdf/***
   * name: theme, value: default

2. Do cookies change with the theme?

  ***The value of the present cookie changes with the theme. For example, when I changed the theme to blue, the value associated with the theme cookie changed from default to blue***

3. 

4. 
5. 



Do the previous two steps (examining cookies and changing the theme) using Burpsuite. What "Cookie:" and "Set-Cookie:" HTTP headers do you see? Do you see the same cookie values as you did with the Inspector?

Quit your browser, relaunch it, and go back to the FDF. Is your red or blue theme (wherever you last left it) still selected?

How is the current theme transmitted between the browser and the FDF server?

When you change the theme, how is the change transmitted between the browser and the FDF server?

How could you use your browser's Inspector to change the FDF theme without using the FDF's Theme menu?

How could you use Burpsuite's Proxy tool to change the FDF theme without using the FDF's Theme menu?

Where does your OS (the OS where you're running your browser and Burpsuite, that is) store cookies? (This will require some internet searching, most likely.)
