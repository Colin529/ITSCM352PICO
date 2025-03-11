# Super SSH by Jeffery John -- (Walkthrough by Colin Hefel)
## Difficulty: Easy  Category: General Skills

1) To start the pico challenge I needed to start the pico instance. 
<img width="1281" alt="picoCTFSuperShellSS#1" src="https://github.com/user-attachments/assets/323f8680-f5ea-4ee7-b28c-b1bc05e5fa64" />


2) The description after launching the pico instance gives us all the information to ssh in.
"Description: Using a Secure Shell (SSH) is going to be pretty important. Can you ssh as ctf-player to titan.picoctf.net at port 54595 to get the flag? You'll also need the password 6abf4a82. If asked, accept the fingerprint with yes."

I quickly looked up how to format an ssh command and crafted 'ssh ctf-player@titan.picoctf.net -p 54367'. 
<img width="1278" alt="picoCTFSuperShellSS#2" src="https://github.com/user-attachments/assets/b6d2cd74-3c15-4e04-ae96-ff08c1790f75" />


This led me to the flag picoCTF{s3cur3_c0nn3ct10n_65a7a106} and as can be seen this is correct.
<img width="1275" alt="picoCTFSuperShellSS#3" src="https://github.com/user-attachments/assets/46d0fea9-86cd-43ab-a425-f03ef4e76362" />

**Flag: picoCTF{s3cur3_c0nn3ct10n_65a7a106}**
