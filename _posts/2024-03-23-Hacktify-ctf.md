---
title: Hacktify CTF
author: JosanGeorge
date: 2024-03-23 13:25:00 +0530
categories: [CTF, Hacktify]
tags: [CTF, osint, crypto, network forensics, reverse engineering, phishing, web, ]
---



## OSINT

### Operation Alias

https://www.threads.net/@artisticsteven

https://www.deviantart.com/artisticsteven/art/Goku-1006444645

https://www.youtube.com/channel/UCKEzwWnc0Rywt9UXrYMjsUg

https://sanie.netlify.app/

https://github.com/StevenSanie?tab=overview&from=2024-03-01&to=2024-03-12

https://www.facebook.com/ArtisticSteven/

- Searching artisticsteven in google able to find several platforms
- Found in deviantart a goku image
- On the bottom left there was a link to spotify
- The flag was found
```flag
flag{This_Feeling_Makes_You_Fly_Higher_Than_Heaven_Till_Forever_Falls_Apart}
```

### Social Hunt

LinuxKiller69

https://www.reddit.com/user/LinuxKiller69/submitted/

- Seaching LinuxKiller69 in instagram, able to find it
- There is something in the profile pic
- Downloading the profile pic and submitting the flag

![Untitled](commons/2024-03-23-Hacktify-ctf/image.png)

```flag
flag{cr0ss_pl4tf0rm}
```

### OWn3r
```flag
flag{Hiroshi_Yamauchi}
```

### Tr4ck
- yandex and google reverse image search
- https://geospy.ai/
- Using google images or lens to search for the images
- managed to get the 3 village names
```flag
flag{llanfairpwllgwyngyll_monsanto_chefchaouen}
```

### Lost
FCC ID: RWO-RZ350259

https://fccid.io/RWO-RZ350259

- Find the phone and mail of the person
https://www.linkedin.com/in/johnsen-tia-0b421539/

```flag
flag{johnsen.tia@razerzone.com}
```

## Crypto

### Cipher Quest
- use cyberchef
- import from file
- use from binary recipe
- you will get png.. save the file open it
- find the flag when we zoom
```flag
flag{crypt1c_1mp0st3r}
```

### FeatherDust
- finding that it is using fernet encoding, searching for fernet decoder online
- https://asecuritysite.com/tokens/ferdecode
```flag
flag{f3rn3t_3ncrypt1on_@r3_s1m1lar_t0_b@s3}
```

### RulerOfTheWorld
- We found it is `baudot-code` from dcode-identifier
- https://www.dcode.fr/baudot-code
```flag
flag{NOTAREGULARBINARY}
```

## Network Forensics
### Shadow Web
- pcapng file, analyzing in wireshark
- Seeing that each HTTP request is continuation of other which have a letter in the POST request
- Getting all the letters from the requests
- Decrypting using the magic tool of cyberchef
```ZmxhZ3ttdWx0MXBsM3A0cnRzYzBuZnVzM3N9```
- We got the flag
```flag
flag{mult1pl3p4rtsc0nfus3s}
```

### Mystic Connections
- pcapng file, analyzing in wireshark
- seeing that it has only ARP and ICMP packets
- Noticing that its having single letter at the end
- All the eth.trailer is having these letters
- Filtering based on arp reply packets
```(arp.opcode == 2)```
- Then filtering based on time
- Getting all the letters from the requests in order.
- We got the flag
```flag
flag{ARP_b31ng_s1mpl3}
```

## Reverse Engineering
### DecryptQuest
- finding that it is encoded using base64. decoding everything
- base64 -d Answer.txt > ans.txt
- Analyzing and finding there is a java program
- Saving the java program separately and executing it
- Finding there is a drive link. It contains brainfuck. Decoding it we get,
```Text
Roses are red,

Violets are blue,

If one wants to pick the correct flag,

Then they should seek the Unix Epod@4a
```
- Finding that Unix Epoch time start in year 1970
- Modifying the program so that it prints all possible flags
- Seaching 1970 in those possible flags we find the flag
```flag
flag{hjwilj111970djs}
```
### 4pP
- Going to https://ai2.appinventor.mit.edu/
- Import project (.aia) from my computer
- Change the designer view to blocks view from the top right
```flag
flag{M1T_4PP_1NV3NT0R_bf0285c53}
```


## Phishing
### Phish Guard
- Search for whitespace decoder
- copy only the whitespace and decode
- can use https://www.dcode.fr/
```flag
flag{D0n't_g3t_ph1sh3d}
```

## Web
### Catch-Me-If-You-Can
- We can see its running `openresty/1.19.3.1`
- Enumerating directories using gobuster, ffuf, or any other tools
```bash
gobuster dir -u url -w /usr/share/wordlist/dirb/big.txt -x php,html --threads 50
```
- We got the directory `/twofish`
- We got the flag
