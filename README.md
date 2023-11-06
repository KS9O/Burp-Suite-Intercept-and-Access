# Burp Suite Intercept and Access
## Table Of Contents
1. Loading and Configuring Burp Suite
2. Reconnaissance
3. Actions on Objectives
# Loading and Configuring Burp Suite
![Alt text](<assets/starting up our http server so that can simulate an interception of credentials using burp suite.png>)
- After loading burpsuite and creating my temporary project, i then start my http server, apache2, and make sure the service is running correctly and configured on port 80.
![Alt text](<assets/insecure connection, this means we don't have a certificate with firefox using localhost-1.png>)
- Testing our connection i seemed to of gotten an insecure connection because of my proxy not being setup, to mitigate this ill have to create a certificate with burpsuite.
![Alt text](<assets/creating a certifcate with burp suite-1.png>)
![Alt text](<assets/importing my certificate i made with burp suite-1.png>)
- The reason i need to create and import a burp certification is to have our TLS certificate for my host with its own CA, certificate authority.
# Reconnaissance
![Alt text](<assets/Back up files onto desktop and then imported my files for our webpage-1.png>)
- within my reconnaissance, i started with first having a backup on my webpage within my system, using a couple quick commands
![Alt text](<assets/connecting to our index html-1.png>)
- connection is secured with the ability to access our page, showing us that the proxy and certificate is working as intended, and we are now able to intercept.
![Alt text](<assets/incorrect password, got this message-1.png>)
- not knowing the password, we input a command password
![Alt text](<assets/burpsuite intercepted my data-1.png>)
- The interception worked and found the password that was entered, so now we'll send it to the intruder and dive deeper into our data.
![Alt text](<assets/sending data to intruder-1.png>)
![Alt text](<assets/loaded a payload for our attack-1.png>)
- within the intruder browser, i import a payload of possible passwords and make sure to have my search not include the original parameter i inputed, "10-4" i know its configured properly because of the $ symbols around it.
![Alt text](<assets/we have the dollar signs around my parameter so burpsuite doesnt use this during the attack-1.png>)
![Alt text](<assets/identified the correct password with the code 200 as this is the response header given when a correct password is inserted-1.png>)
- With our payload loading and being scanned, we can see all the possible parameters, and to discern the proper one with the code 200.
![Alt text](<assets/retyped the password in my index-1.png>)
- Revisiting our index page while intercepting, with the properly acquired password entered in, burpsuite intercepts it again, and grants me access once i forward it over.
![Alt text](<assets/When i clicked forward in burpsuite, we got access into the website-1.png>)
- Access granted, Welcome Admin!