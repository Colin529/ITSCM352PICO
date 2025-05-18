## Glitch Cat by T 'SYREAL' JONES - Easy
# By COLIN HEFEL
1) This picoCTF was about ASCII values in particularly in python. After launching the provided netcat command 'nc saturn.picoctf.net 54402' are given the output 'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'.
2) Looking at this out put and the hints we quickly find out that chr is a way to turn hex values to int then to the equivelent ASCII character. Knowing this we can write a very simple decryption program.
<img width="1440" alt="Screenshot 2025-05-17 at 7 44 12 PM" src="https://github.com/user-attachments/assets/269a61bd-de91-4d31-a41f-2beefac0ef51" />
3) Using this program we can quickly decode and get out flag.
<img width="1440" alt="Screenshot 2025-05-17 at 7 45 59 PM" src="https://github.com/user-attachments/assets/66094c45-0452-4d25-95ce-8c0dcdbe9034" />
Flag: picoCTF{gl17ch_m3_n07_a4392d2ell}
