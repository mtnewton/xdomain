An example of sharing a random value cross domain

set up /etc/hosts with
```127.0.0.1 domain-a.com domain-b.com iframe.com```
so that when visited the browser thinks they are different domains

run the following commands in different terminals 
```
    php -S localhost:8010 -t iframe
    php -S localhost:8020 -t website
```
this will serve the iframe and website file locally

visit both http://domain-a.com:8020 and http://domain-b.com:8020 and you will see both load the same random number
no cookies are stored on domain-a or domain-b
the iframe that is loaded will generate a random number and store it as a cooke on its domain if not already set then send the value to the parent window via postMessage
The parent (domain-a / domain-b) will listen for a message, check to see if the origin was the iframe, then print to page
