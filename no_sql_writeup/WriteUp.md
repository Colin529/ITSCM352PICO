# No SQL Injection by Ngirimana Schadrack -- (Walkthrough by Colin Hefel)
## Difficulty: Medium || Category: Web Explotation

1) To start I had to launch the Pico instance. This description did not
give many clues, however it provides a link to the website to exploit and the files that make up the website. The link leads to a login page of the website. The downloadable files contain two .html files,  'admin.html' and 'index.html'. It also contains a .json file 'package.json' and a javascript file 'server.js'.

<img width="1281" alt="starting" src="https://github.com/user-attachments/assets/e6398a5e-af1f-49f1-b0e3-223550ca95ed" />


<img width="946" alt="app_file" src="https://github.com/user-attachments/assets/eaf55016-7fbc-42ac-9d67-50b7546d6a48" />

2) We can open the index and admin .html file. The index file is the login page and the admin is a page on the wesite. However, to start trying to attack the login we have to use the link on the pico module.

<img width="1279" alt="login_page" src="https://github.com/user-attachments/assets/2ee92837-85a5-4a1c-954d-37002c9cf77b" />

<img width="1276" alt="admin_page" src="https://github.com/user-attachments/assets/b1292203-a471-4c8d-8b90-afa4af4ef407" />


What is NoSQL?
- Not Only SQL or "NoSQL" for short is a database management system that differs from SQL. NoSQL is considered more scalable and flexible. Unlike SQL servers that use Structured Query Language, NoSQL systems don't necessarily use one language but different languages based on the server system. 

3) Looking at the provided javascript file I saw it had a line '{MongoMemoryServer} = require ("mongodb-memory-server")' I felt like this would be important so I looked up information on MongoDB NoSQL Injection techniques (https://www.imperva.com/learn/application-security/nosql-injection/) along with other information on NoSQL and possible injection(https://amsghimire.medium.com/nosql-injection-c5c5cf703a5e). After some attempts and fails in crafting my own injection I turned to PentestGPT for help.

<img width="1278" alt="js_and_json" src="https://github.com/user-attachments/assets/b4d00ff5-faa1-4c95-b7d3-b503e8af1f7d" />


4) Feeding PentestGPT the javascript file it suggested using the payload '{"$gt": ""}' in the email and password field to bypass the email and password checks.
  - Understanding the '{"$gt": ""}' input: the MongoDB server interprets '$gt' as 'greater than' and "" as an     empty string. So essentially we are able to tell the server to match this to any email and password in        the database that is greater than an empty password and email which is any email and password within the      database. 

6) This input allowed me to bypass the login page, however this just brought me back to the /admin page which contained some random information but no flag.
  
7) After some poking around the page trying to find a hidden flag, I used the second hint that stated, “Make sure you look at everything the server is sending back”. This makes sense because looking at the JavaScript file I can see that it sets the user.token (which is the flag) if the login attempt comes back successful.  

8) Using ‘web developer tools’ in the browser and using the ‘console’ tab within we can see the token value. However, it’s obviously encoded somehow.

<img width="1269" alt="web_developer" src="https://github.com/user-attachments/assets/e65f21c6-99a9-4bcc-83c3-ba6e81d9a473" />


9) Bringing the encoded text over to everyone's favorite decoder ‘cyberchef’ I used the magic feature and very quickly got my decoded flag.

<img width="1440" alt="cyber_chef" src="https://github.com/user-attachments/assets/36b0d934-f855-4d75-b7e0-f07e30807961" />

**<ins>Flag: picoCTF{jBhd2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_25ba4de1}</ins>**

<img width="1280" alt="done" src="https://github.com/user-attachments/assets/95acd1fc-1c3e-46b6-a534-b091594d0fde" />

