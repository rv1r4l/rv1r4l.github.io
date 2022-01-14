# Ritsec-2021-CTF-Writeup
A description for challenges "snek" and "Sessions"

Challenge 1 (BIN/REV) "snek"

![Image of snek](https://github.com/rv1ral/Ritsec-2021-CTF-Writeup/blob/main/Screenshot%20from%202021-04-11%2020-24-48.png)


This one's pretty simple, when viewing the challenge, it gives you something that seems like
a binary. The first thing that comes up to mind is to open up radare and start disassembling 
everything until you realize there's something slightly off. There isn't an "ELF" tag and there 
seems to be "snek.py" when examining the file. Knowing this, it becomes obvious that "snek" is 
actually bytcode for snek.py. For more information on bytecode, https://opensource.com/article/18/4/introduction-python-bytecode.
Since bytecode can be converted from a .pyc back into a .py file, I used a tool called uncompyle6 to do the job.
```
uncompyle6 snek.pyc
```
![Image of snekCode](https://github.com/rv1ral/Ritsec-2021-CTF-Writeup/blob/main/Screenshot%20from%202021-04-11%2020-25-42.png)

After examining the code, we see an odd list of numbers, which actually turn out of be ASCII 
values. Putting this into a decimal to ASCII value converter gives us the alphabet and the flag, RS{all_hi$$_and_n0_bit3}.


Challenge 2 (WEB) "Sessions"

![Image of Sessions](https://github.com/rv1ral/Ritsec-2021-CTF-Writeup/blob/main/Screenshot%20from%202021-04-11%2020-22-33.png)


At first, this challenge seems a bit off, since we just get a login screen and nothing else.
After looking at the source code, we can see a comment that lists the credentials, "iroh:iroh".

![Image of Sessions](https://github.com/rv1ral/Ritsec-2021-CTF-Writeup/blob/main/iroh.png)

After logging in, we get 2 different directories we can go to. After a lot of searching, it seems really useless.
Knowing that the challenge name is "sessions", it prompts us to look into the network tab. After closer inspection, 
there is a session token that looks like its been encoded in base64.

![Image of Sessions](https://github.com/rv1ral/Ritsec-2021-CTF-Writeup/blob/main/Screenshot%20from%202021-04-11%2020-23-40.png)

After putting this through a base64 decryptor, we get the flag, RS{0nly_One_s3ssion_tok3n}.
