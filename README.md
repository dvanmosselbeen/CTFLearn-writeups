# CTFLearn Writeups

The goal of these writeups here is to share information. But not sharing as is the easy way, even if it is. This is meant to be for when you are stuck trying to `Capture The Flag`. Sharing information is in my opinion very important. Because we have all learnt tons of things from other people who where so kind to share their knowledge.

This is why I want to insist that you first need to try your best to `Capture The Flag` on your own. Use these resources here only as last resort. Otherwise, you will never learn how to do research and find valuable information. Furthermore, when you learn to search, you will keep these search skills, and also easily remember the result.

I also like writeups very much, I read a lot of other people's writeup, just to see how they have handled the problem, the research. Very valuable resources in my opinion. Sharing is caring.

**WARNING: I stripped out the answers, passwords, flags and co. This writeup is pretty detailed. By following and doing the steps described here yourself you will get them all. The goal is to learn more about it, even if you get stuck at some point. Enjoy!**

## Table of Contents

Not ordered, or maybe yes, my last on top. I'm lazy, sorry :-D

- [Suspecious message](#suspecious-message)
- [Simple Steganography](#simple-steganography)
- [Pho Is Tasty!](#pho-is-tasty)
- [Tux!](#tux)
- [Modern Gaius Julius Caesar](#modern-gaius-julius-caesar)
- [Chalkboard](#chalkboard)
- [Snowboard](#snowboard)
- [My Blog](#my-blog)
- [Lazy Game Challenge](#lazy-game-challenge)
- [Rubber Duck](#rubber-duck)
- [HyperStream Test #2](#hyperstream-test-2)
- [BruXOR](#bruxor)
- [Git Is Good](#git-is-good)
- [QR Code](#qr-code)
- [Simple Programming](#simple-programming)
- [WOW.... So Meta](#wow-so-meta)
- [Hextroadinary](#hextroadinary)
- [Reverse Polarity](#reverse-polarity)
- [Taking LS](#taking-ls)
- [Morse Code](#morse-code)
- [Forensics 101](#forensics-101)
- [Binwalk](#binwalk)
- [Exif](#exif)
- [Character Encoding](#character-encodingh)
- [Base 2 2 the 6](#base-2-2-the-6)
- [Where Can My Robot Go?](#where-can-my-robot-go)
- [Wikipedia](#wikipedia) 

## Suspecious message

Question 887: <https://ctflearn.com/challenge/887>

**Hello! My friend Fari send me this suspecious message: 'MQDzqdor{Ix4Oa41W_1F_B00h_m1YlqPpPP}' and photo.png. Help me decrypt this! (Download the attached file on this question)**

The image we can download is very small, but show an `5x5` grid with the alphabet except the letter `j` is missing. If we look up on Google with the keywords `5x5 grid cipher`. We find out this is about the `Play Faire` cipher. Actually, the first results are about Polybius Square Cipher which I did not get to work. A good online `Play Faire` decrypt tool might be: <http://rumkin.com/tools/cipher/playfair.php>

## Simple Steganography

Question 894: <https://ctflearn.com/challenge/894>

**Think the flag is somewhere in there. Would you help me find it? hint-" Steghide Might be Helpfull". (Download the attached file on this question)**

Looking up with `string` on that image, we see some common word/possible password. Which can be used with `steghide extract -sf Minions1.jpeg` to extract the hidden (`raw.txt`) message. then `cat raw.txt | base64 -d` to get the flag.

## Pho Is Tasty! 

Question 971: <https://ctflearn.com/challenge/971>

**The flag is hidden in the jpeg file. Good Luck! Have some Pho! Solve this challenge before solving my Scope challenge for 100 points. (Download the attached file on this question)**

Use the `hexedit` tool, and look very closely on the 3rd line, just below the line `Samsung Galaxy S8 Color Palette:`.

## Tux!

Question 973: <https://ctflearn.com/challenge/973>

**The flag is hidden inside the Penguin! Solve this challenge before solving my 100 point Scope challenge which uses similar techniques as this one. (Download the attached file on this question)**

Use exiftool to find the base64 string in the Comment field. Base64 decode that and you will get a password.

Then extract the `Tux.jpg` file with binwalk (`binwalk -e Tux.jpg`). Which will create a new folder with a zip file called `1570.zip`. Then extract the zip file with the password we previously found.

## Modern Gaius Julius Caesar

Question 885: <https://ctflearn.com/challenge/885>

**One of the easiest and earliest known ciphers but with XXI century twist! Nobody uses Alphabet nowadays right? Why should you when you have your keyboard?**

```
BUH'tdy,|Bim5y~Bdt76yQ
```

That is some typical US CTF. For this you need to own a US keyboard, or lookup on Google image for a US keyboard. Then shift every letter by 2 keys on the keyboard. So my free hint, so you can solve this. The flag start with CTF


## Chalkboard

Question 972: <https://ctflearn.com/challenge/972>

**Solve the equations embedded in the jpeg to find the flag. Solve this problem before solving my Scope challenge which is worth 100 points. (Download attached file.)**

While looking at `strings` on this image, we see the following:

````
CTFlearn{I_Like_Math_x_y}
where x and y are the solution to these equations:
3x + 5y = 31
7x + 9y = 59
````

For this use tool [WolframAlpha](https://www.wolframalpha.com/input/?i=3x+%2B+5y+%3D+31%2C+7x+%2B+9y+%3D+59) and input `3x+5y=31,7x+9y=59` and which will give you the answer. This [Algebra Calculator](https://www.mathpapa.com/algebra-calculator.html) is also nice to understand what's going on step by step. [CueMath](https://www.cuemath.com/algebra/) is also a nice source.

## I'm a dump

Question 883: <https://ctflearn.com/challenge/883>

**The keyword is hexadecimal, and removing an useless H.E.H.U.H.E. from the flag. The flag is in the format `CTFlearn{*}` (Download attached file.)**

Used `strings` for this too, as it is easier I find. You see the flag spread on 3 lines. Copy these 3 lines, removed these 2 useless `H` letters, and you are done.

## PikesPeak

Question 935: <https://ctflearn.com/challenge/935>

**Pay attention to those strings! (Download that attached `PikesPeak.jpg` file.**

Looking with `strings` on this jpg file and we see different flags, each of them written slightly different. The 6th of it is the good one as this website is called `CTFlearn`.

## Snowboard

Question 934: <https://ctflearn.com/challenge/934>

**Find the flag in the jpeg file. Good Luck!**

Downloaded that attached file.

Note, there is a false flag when looking with `exiftool` there in the comment section. When looking with `strings`, we see that false flag on the second line, and the 3rd line contains a base64 string. Decoding this with [CyberChef](https://gchq.github.io/CyberChef/) give you the flag.

## My Blog

Question 979: <https://ctflearn.com/challenge/979>

**Hi, I'm Noxtal! I have hidden a flag somewhere in my [Cyberworld](https://noxtal.com/) (AKA blog)... you may find a good application for your memory. ;)**

**Note: This is my real website (thus no deadly bug to exploit here). You might want to read some of my content (writeups, tutorials, and cheatsheets). I would be glad to receive any kind of feedback.**

**[Click here to](https://noxtal.com/) access it, have fun checking my blog out! Cheers!**

**Hint: replace the flag{} part with CTFlearn{}.**

For this use for example the `Google Chrome Developers Tool` (`F12`). Then in `Application` > `Storage` > `Local Storage` > `https://https://noxtal.com` and you will see the flag.

## Lazy Game Challenge

Question 691: <https://ctflearn.com/challenge/691>

**I found an interesting game made by some guy named "John_123". It is some betting game. I made some small fixes to the game; see if you can still pwn this and steal $1000000 from me!**

**To get flag, pwn the server at:** `nc thekidofarcrania.com 10001`

Bet `-999999` and if you loose, you get the money and the flag :-D

## Rubber Duck

Question 993: <https://ctflearn.com/challenge/933>

**Find the flag! Simple forensics challenge to get started with. File to download: <https://ctflearn.com/challenge/download/933>**

Use `strings` for this, answer is on the second line.

````commandline
strings RubberDuck.jpg | less
````

`exiftool` also reveal the flag in the comment section.

## HyperStream Test #2

_Question 443: <https://ctflearn.com/challenge/443>_

**I love the smell of bacon in the morning! ABAAAABABAABBABBAABBAABAAAAAABAAAAAAAABAABBABABBAAAAABBABBABABBAABAABABABBAABBABBAABB**

For this, used [CyberChef](https://gchq.github.io/CyberChef/) and use the `Bacon Cipher Decode`. Then set the `Translate` option to `A/B` and you get your answer.

## BruXOR

Question 227: <https://ctflearn.com/challenge/227>

**There is a technique called bruteforce. Message: q{vpln'bH_varHuebcrqxetrHOXEj No key! Just brute .. brute .. brute ... :D**

For this, we need [CyberChef](https://gchq.github.io/CyberChef/) and use the `XOR Brute Force` operation. Then on the output, `key 17` is the flag. Prety confussing as `key 37` reveals another flag.

## Git Is Good

_Question 104: <https://ctflearn.com/challenge/104>_

**The flag used to be there. But then I redacted it. Good Luck. <https://mega.nz/#!3CwDFZpJ!Jjr55hfJQJ5-jspnyrnVtqBkMHGJrd6Nn_QqM7iXEuc>**

This is about a `zip` file we need to download and extract (`unzip gitIsGood.zip`). Once extracted, there is only one file `flag.txt` which is revisioned with `git`. So looking with `git log`, we see that there are 3 commits. The commit log is not well done, as the first commit log should have a message in the trend `Initial commit` to make things clear. We can look to the difference of the second commit with using `git diff <COMMIT_HASH>`. The commit hash we find back in the git log.

````
git diff 195dd65b9f5130d5f8a435c5995159d4d760741b
````

Which will reveal you the flag.

## QR Code

_Question 228: <https://ctflearn.com/challenge/228>_

**Do you remember something known as QR Code? Simple. Here for you: <https://mega.nz/#!eGYlFa5Z!8mbiqg3kosk93qJCP-DBxIilHH2rf7iIVY-kpwyrx-0>**

For this I have downloadeded the QR code of that link. Then used an [online QR Code reader](https://pageloot.com/nl/qr-code-scanner/#upload). Which revealed the content `c3ludCB2ZiA6IGEwX29icWxfczBldHJnX2RlX3BicXI=`. Locked up on a online [Hash Analyzer](https://www.tunnelsup.com/hash-analyzer/), which told me this is a `base64` encoded message. Ran `echo "c3ludCB2ZiA6IGEwX29icWxfczBldHJnX2RlX3BicXI=" | base64 -d` which have output: `synt vf : a0_obql_s0etrg_de_pbqr`. Looked up on [CyberChef](https://gchq.github.io/CyberChef/), and used the `ROT13` to decode. 

## Simple Programming

_Question 174: <https://ctflearn.com/challenge/174>_

**Can you help me? I need to know how many lines there are where the number of 0's is a multiple of 3 or the numbers of 1s is a multiple of 2. Please! Here is the file: <https://mega.nz/#!7aoVEKhK!BAohJ0tfnP7bISIkbADK3qe1yNEkzjHXLKoJoKmqLys>**

````python
fp = open('data.dat', 'r')
lines = fp.readlines()
count = 0
for line in lines:
    zero = line.count('0')
    ones = line.count('1')
    if zero % 3 == 0 or ones % 2 == 0:
        count += 1 
        
print("The answer is: CTFlearn{%s}" % count)
````

## Vigenere Cipher

_Question 305: <https://ctflearn.com/challenge/305>_

**The vignere cipher is a method of encrypting alphabetic text by using a series of interwoven Caesar ciphers based on the letters of a keyword.**

**I’m not sure what this means, but it was left lying around:** `blorpy`

`gwox{RgqssihYspOntqpxs}`

Use [CyberChef](https://gchq.github.io/) and the key `blorpy` and you get the flag.

## WOW.... So Meta

_Question 348: <https://ctflearn.com/challenge/348>_

**This photo was taken by our target. See what you can find out about him from it. <https://mega.nz/#!ifA2QAwQ!WF-S-MtWHugj8lx1QanGG7V91R-S1ng7dDRSV25iFbk>**

Use `exiftool` and you will get the flag, it's in the section `Camera Serial Number`.

## Hextroadinary

_Question 158: <https://ctflearn.com/challenge/158>_

**Meet ROXy, a coder obsessed with being exclusively the worlds best hacker. She specializes in short cryptic hard to decipher secret codes. The below hex values for example, she did something with them to generate a secret code, can you figure out what? Your answer should start with 0x.**

**0xc4115 0x4cf8**

Using a [XOR Calculator](https://xor.pw/) helped to get the answer.

## Reverse Polarity

_Question 230: <https://ctflearn.com/challenge/230>_

**I got a new hard drive just to hold my flag, but I'm afraid that it rotted. What do I do? The only thing I could get off of it was this: 01000011010101000100011001111011010000100110100101110100010111110100011001101100011010010111000001110000011010010110111001111101**

This is about binary data. Convert binary and you have the flag. Use for example [CyberChef](https://gchq.github.io/).

## Taking LS

_Question 103: <https://ctflearn.com/challenge/103>_

**Just take the Ls. Check out this zip file and I be the flag will remain hidden. <https://mega.nz/#!mCgBjZgB!_FtmAm8s_mpsHr7KWv8GYUzhbThNn0I8cHMBi4fJQp8>**

````commandline
$ unzip The\ Flag.zip                                                                                                                                   
Archive:  The Flag.zip
   creating: The Flag/
  inflating: The Flag/.DS_Store      
   creating: __MACOSX/
   creating: __MACOSX/The Flag/
  inflating: __MACOSX/The Flag/._.DS_Store  
   creating: The Flag/.ThePassword/
  inflating: The Flag/.ThePassword/ThePassword.txt  
  inflating: The Flag/The Flag.pdf   
  inflating: __MACOSX/The Flag/._The Flag.pdf
````

Note the hidden folder `.ThePassword/ThePassword.txt` which contains the password for the pdf file. The pdf file contain the flag.

## Morse Code

_Question 309: <https://ctflearn.com/challenge/309>_

````
..-. .-.. .- --. ... .- -- ..- . .-.. -- --- .-. ... . .. ... -.-. --- --- .-.. -... -.-- - .... . .-- .- -.-- .. .-.. .. -.- . -.-. .... . . ...
````

Use whatever morse code converter, like the [CyberChef](https://gchq.github.io/) or this online tool for example: <https://morsecode.world/international/translator.html>

## Forensics 101

_Question 96: <https://ctflearn.com/challenge/96>_

Think the flag is somewhere in there. Would you help me find it? <https://mega.nz/#!OHohCbTa!wbg60PARf4u6E6juuvK9-aDRe_bgEL937VO01EImM7c>

    strings 95f6edfb66ef42d774a5a34581f19052.jpg

This one can be quite tricky, as when looking with `steghide info 95f6edfb66ef42d774a5a34581f19052.jpg`, it asks for a passphrase. So we tent to want to try to crack it with `stegcracker 95f6edfb66ef42d774a5a34581f19052.jpg` to look inside.

And you see the flag.

## Binwalk

_Question 108: <https://ctflearn.com/challenge/108>_

With `binwalk`:

    binwalk -D='.*' PurpleThing.jpeg

Which is the same command as:

    binwalk --dd='.*'

We can also use foremost (apt install foremost):

    foremost -T PurpleThing.jpeg

**Here is a file with another file hidden inside it. Can you extract it? <https://mega.nz/#!qbpUTYiK!-deNdQJxsQS8bTSMxeUOtpEclCI-zpK7tbJiKV0tXYY>**

## Exif

_Question 303: <https://ctflearn.com/challenge/303>_

**If only the password were in the image?**

**<https://mega.nz/#!SDpF0aYC!fkkhBJuBBtBKGsLTDiF2NuLihP2WRd97Iynd3PhWqRw> You could really ‘own’ it with exif.**

Just use `exif` or `exiftool` and you will se the flag in the exif information.

## Base 2 2 the 6

_Question 192: <https://ctflearn.com/challenge/192>_

**There are so many different ways of encoding and decoding information nowadays... One of them will work! Q1RGe0ZsYWdneVdhZ2d5UmFnZ3l9**

    echo "Q1RGe0ZsYWdneVdhZ2d5UmFnZ3l9" | base64 -d

Tip: A hash analyze would tell you this is base64.

## Character Encoding 

_Question 115: <https://ctflearn.com/challenge/115>_

**In the computing industry, standards are established to facilitate information interchanges among American coders. Unfortunately, I've made communication a little bit more difficult. Can you figure this one out? 41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D**

After installing the basez utility (apt install basez):

    echo "41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D" | base64 -d

or:

    echo "41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D" | xxd -r -p

## Where Can My Robot Go?

_Question 107: <https://ctflearn.com/challenge/107>_

**Where do robots find what pages are on a website?**

_Hint: What does disallow tell a robot?_

For this look on <https://ctflearn.com/robots.txt> which will output:

````
User-agent: *
Disallow: /70r3hnanldfspufdsoifnlds.html
````

Now going on <https://ctflearn.com/70r3hnanldfspufdsoifnlds.html> will tell you the flag.

## Wikipedia 

_Question 168: <https://ctflearn.com/challenge/168>_

**Not much to go off here, but it’s all you need: Wikipedia and 128.125.52.138.**

For this, go on the wikipedia website, and do a search with that IP address. Then look for `Search for contributions` and in the user field, fill in that IP address. This will show up 1 search result, a page called Flag. On that Flag page, somewhere bellow in the `Competitions` section, you will find a line: `In a certain CTF competition, the flag to a certain problem is "cNi76bV2IVERlh97hP".` Which is actually the flag. Not a standard one, that's why I spoil it here.