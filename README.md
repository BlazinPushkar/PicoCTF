# PicoCTF
writeups for the ctfs i have completed in picoCTF
**LOG HUNT(EASY)**

1. flag was fragmented across the log files
2. simple grep with INFO PART was able to gather all the pieces of flag

**RIDDLE REGISTRY(EASY)**

1. A pdf was provided with gibberish content
2. few lines were hidden by black filter but simple copying them and pasting somewhere else revealed their content but it was gibberish and useless
3. then some hint about metadata was given in description
4. opened the metadata of pdf and saw author's name was too long and looked like encoded
5. did base64 decoding and got the flag

**HIDDEN IN PLAINSIGHT(EASY)**

1. A jpeg image was provided
2. opened the metadata , comment looked encoded
3. did base64 found hint steghide with another encoding
4. did bas64 on it and got a password
5. learned abit about steghide and used steghide --info and used the password, found an embedded file
6. extracted the file and flag was inside it.

**FLAG IN FLAME(EASY)**

1. a logs file was given , it had a lot of encoded text
2. i got a python script from gpt to detect base64 encoding and decode it
3. when i ran the file with that script but got a lot gibberish
4. i did see something like IDAT but didn't clock it , i looked up a write up for it and you had to convert the decoded data into a jpeg
5. the jpeg contained a hex encoding, decoding it gave away the flag

**COOKIE MONSTER SECRET RECIPE(EASY)**

1. a login page site was given , i just typed random gibberish in the fields , it redirect to the page that gave hint to look at the cookies.
2. i did inspect on the site and went into storage section found a encoded message
3. decoded it from base64 and got the flag

**CRACK THE GATE 1(EASY)**

1. a login page again was given, with an id but no password
2. inspecting it gave a ROT13 encoded message
3. after decoding gave a major hint about header and value that would give the flag
4. so i went onto the site again went into inspect then to network tab, did edit and resend after sending gibberish as password at first
5. added the given details in header, got a 200 response status code, went into response of it and got the flag

**CORRUPTED FILE(EASY)**

1. an unknown type of file was given
2. inside it was complete gibberish, the hint indicated something with jpeg
3. so i looked at it's hexdump with xxd and compared the header with jpeg header
4. after fixing it the jpeg image had the flag in it.

**DISKO 1(EASY)**

1. we were given a disk image file compressed by gzip
2. i unzipped the file by gunzip and found a .dd disk image file
3. i used grep "picoCTF{" on the file it gave it found a match in binary form
4. i used string on the file, found a lot of human readable lines,used strings again and put the whole readable data into a txt file
5. used grep on it and found the flag

**SSTI 1(EASY)**

1. a site was given that had server side template injection vulnerability.
2. it would announce what you typed but if you put inside any argument inside double curly brackets it would execute that
3. i used curl to find about what language was the server using and got a server template injection for python by jinja2 and found the flag

**HASHCRACK(EASY)**

1.a hash was given for a password , we had to get the password from that hash

2.first i identified the type of hash , then using john ripper tool and a wordlist called rockyou that contained a lot of leaked password, i got the password

3.after that we had to do this process 2 more times to get the ctf finally.

**FLAG HUNTERS(EASY)**

1.this was a reverse engineering CTF, we were given a python code that executed a song

2.the flag was between the lyrics, inside a secret part, we had to execute the secret part to see the flag

3.in code it was given that the lyrics would be split by ; and it was given to execute the secret lyrics we would have to get RETURN\[0-9]

4.if we added RETURN statement without semicolon , it would have just been keep repeating later verses, not giving the flag

5\. so you had to put something before semicolon then return after it, then it would reveal the code

**FANTASY CTF(EASY)**

1.this was to just a guide for picoctf, answering the right question would give the flag write away.

**RED(EASY)**

1.a png was given with just plain red

2.i used cat command and found some a poem in it.

3.if you see the first letter of every line, it says check LSB(the bit responsible for color)

4.i saw some write ups too they directly used zsteg tool and got a base64 encoded flag.

5.in cyberchef you can extreact the LSB and get the text that is repeating same encoded message again and again, decode it and get the flag

**3V@I(MEDIUM)**

1. a bank's interest calculator site was given with hint it uses eval() function
2. eval() function can do code execution if we input code in it.
3. common keywords like os,ls,cat are banned and encoding also
4. so instead we use ASCII numbers to open flag.txt file and get the flag.

**SCAN SURPRISE(EASY)**

1.got an zip file, unzip it,found a qr, scanned it got the flag

**BINARY SEARCH(EASY)**

1.this was based on simple binary search algorithm.

2.a random number was generated between 1-1000 and we had to guess the number in less than 10 guesses.

**UNMINIFY(EASY)**

1.a simple website was given to us, the code was minified according to author

2\. simply doing an inspect on the site and looking through the code would reveal the whole flag

**SUPER SSH(EASY)**

you just had to connect via ssh with given details and you would get the flag

**WEB DECODE(EASY)**

you just had to go to different pages of the given site , inspecting their code, i got the flag in on of the pages.

**VERIFY(EASY)**

1.connected to a remote system by ssh and given details

2.found checksum,files and a decrypt script, the checksum had the SHA256 value for the file that had the flags

3.in files there were a lot files, converted the whole directory in SHA256 and got the file that matched with checksum value provided

4.decrypted the file and got the flag.

**INTERECDEC(EASY)**

1.this was a cryptography challenge, we were given a text file that had some encoded text.

2.i did a base64 decoding initially, got another encoded text that looked like base64 again but wasn't giving a meaningful text when decoded

3.and with other decoding methods like hex,url,caeser too weren't giving anything useful

4.this was a bit tricky cause the text was base64 encoded but starting few letters of the line were hindering the decoding

5.after removing first few characters and decoding again gave the flag.

**TIME MACHINE(EASY)**

1. this was a simple challenge where a person lost his progress but had saved it in git
2. simple unzipping the challenge and going inside the drop in file and getting log from git revealed the flag.

**SECRET OF POLYGOT(EASY)**

1. a pdf file was given , it had a portion of flag, giving hint png and pdf
2. i instead opened the pdf as jpg and got the other portion of the flag.

**GUESS MY CHEESE PART1(MEDIUM**)

1.you were given a encrypted text with a hint that a cipher that uses linear equations was used.

2.so i encrypted the keyword "swiss" and used this to get the equation used to this affine cypher.

3.once i got the equation, i decrypted the text and gussed what i did and got the flag
