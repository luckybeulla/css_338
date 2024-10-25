***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## Cookies and cross-site scripting (XSS) ##

### Part 1: Cookies ###

1. Initial cookies for cs338.jeffondich.com - their names and values

   ***Yes, there is a cookie for the domain cs338.jeffondich.com/fdf/***
   * name: theme, value: default

2. Do cookies change with the theme?

    ***The value of the present cookie changes with the theme.***
   * For example: when I changed the theme to blue, the value associated with the theme cookie changed from default to blue
     
3. Step 1 and 2 using Burpsuite

    ***Using burpsuite, the HTTP request to cs338:jeffondich.com contains a Cookie header with its value theme set to default. The resulting HTTP response has a Set-Cookie header containing the theme as default, and experies with a data. When I change the theme of Jeff's site to be red, a new GET request is sent with theme set to red: GET /fdf/?theme=red HTTP 1.1. The Set-Cookie header in the response then has the theme value as red with the same expiration date. These changes in the cookie value are similar to those observed through the inspectpor tool***

   * Note: The very first HTTP GET request that was sent to cs338:jeffondich.com did not contain a Cookie header and the resulting response had a Set-Cookie header with the theme value. The subsequent GET requests to the site then had a Cookie header.

5. Relaunching the browser and going back to FDF.

   ***The theme to the FDF site stayed the same when I closed my Chrome browser and relaunched it. That is, I change the site from the default theme to blue and close it. When I relaunched the site, the theme was still blue***

6. How the current theme transmitted between the browser and the FDF server.

    ***When I visited the FDF site, my browser stored a cookie, in this case theme with its value. Thus when I refresh or relaunch the page, my browser automatically sends this theme cookie along with the request. The server then reads the cookie containing current value of my theme and responds with the appropriate version of the site***
   
6. How changing the theme is transmitted between the browser and the FDF server?

    ***Changing the theme updates the value of my local cookie and thus when my browser makes a new request to the server, the new value of the cookie is automatically sent as part of the HTTP request headers***

7. Using browser's inspector to change FDF theme
   
    ***Using the Inspector, in the applications tab, I was able to edit the value of the theme cookie by typing in a different theme option. When I refreshed the page, the FDF theme updated to the new set value***

8. Using Burpsuite's Proxy tool to change the FDF theme.

    ***By modifying the cookie header value of the intercepted request to the FDF server, I was able to get a response with the updated theme on the FDF site without using the theme menu***

9. Where my OS stores cookies.

    ***Each browser manages the directory and format in which its cookies are stored on my computer's hard drive***
     * For example the cookies from Google Chrome on my macOs are stored in the subdirectory ~/Library/Application Support/Google/Chrome/Default/Cookies
  
     ****** 
