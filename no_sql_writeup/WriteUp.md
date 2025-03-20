# No SQL Injection by Ngirimana Schadrack -- (Walkthrough by Colin Hefel)
## Difficulty: Medium || Category: Web Explotation

1) To start I had to launch the Pico instance. This description did not
give many clues, however it provides a link to the website to exploit and the files that make up the website. The link leads to a login page of the website. The downloadable files contain two .html files,  'admin.html' and 'index.html'. It also contains a .json file 'package.json' and a javascript file 'server.js'. 

What is NoSQL?
- Not Only SQL or "NoSQL" for short is a database management system that differs from SQL. NoSQL is considered more scalable and flexible. Unlike SQL servers that use Structured Query Language, NoSQL systems don't necessarily use one language but different languages based on the server system. 

2) Looking at the provided javascript file I saw it had a line '{MongoMemoryServer} = require ("mongodb-memory-server")' I felt like this would be important so I looked up information on MongoDB NoSQL Injection techniques (https://www.imperva.com/learn/application-security/nosql-injection/) along with other information on NoSQL and possible injection(https://amsghimire.medium.com/nosql-injection-c5c5cf703a5e). After some attempts and fails in crafting my own injection I turned to PentestGPT for help.

3) Feeding PentestGPT the javascript file it suggested using the payload '{"$gt": ""}' in the email and password field to bypass the email and password checks. 

4) This input allowed me to bypass the login page, however this just brought me to the /admin page which contained some random information but no flag.  
After some poking around the page trying to find a hidden flag, I used the second hint that stated, “Make sure you look at everything the server is sending back”. This makes sense because looking at the JavaScript file I can see that it sets the user.token (our flag) if the login attempt comes back successful.  

5) Using ‘web developer tools’ in the browser and using the ‘console’ tab within we can see the token value. However, it’s obviously encoded somehow. 

6) Bringing the encoded text over to everyone's favorite decoder ‘cyberchef’ I used the magic feature and very quickly got my decoded flag. 
Flag: picoCTF{jBhd2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_25ba4de1}  
