# Over The Wire - Bandit

**Login via ssh**
```
Command : ssh bandit0@bandit.labs.overthewire.org -p 2220
Password: bandit0
```

**Lvl(0-1):** The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

Solution : 
 ```
 Command : cat readme 
 Password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1
 ```
**Lvl(1-2):** The password for the next level is stored in a file called - located in the home directory.

Solution:
```
Command : cat./-
Password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

**Lvl(2-3):** The password for the next level is stored in a file called spaces in this filename located in the home directory. 

Solution:
```
Command : cat 'spaces in this filename'
Password: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

**Lvl(3-4):** The password for the next level is stored in a hidden file in the inhere directory.

Solution:
```
Command : cd inhere
          ls -a
          cat ./.hidden
Password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

**Lvl(4-5):** The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Solution:
```
Command : cd inhere
          file ./-file0*
          cat ./-file07
Password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

**Lvl(5-6):** The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable

Solution:
```
Command : cd inhere
          find . -type f -size 1033c ! -executable
Password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

**Lvl(6-7):** The password for the next level is stored somewhere on the server and has all of the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

Solution:
```
Command : find / -type f -user bandit7 -group bandit6 -size 33c
          cat /var/lib/dpkg/info/bandit7.password
Password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

**Lvl(7-8):** The password for the next level is stored in the file data.txt next to the word millionth.

Solution:
```
Command : grep 'millionth' data.txt 
Password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

**Lvl(8-9):** The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

Solution:
```
Command : sort data.txt | uniq -c 
Password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
``` 

**Lvl(9-10):** The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

Solution:
```
Command : strings data..txt | grep '='
Password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

**Lvl(10-11):** The password for the next level is stored in the file data.txt, which contains base64 encoded data.

Solution:
```
Command : base64 -d data.txt
Password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

**Lvl(11-12):** The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

Solution:
- Go to [Rot 13](https://rot13.com/) to decrypt the text.
```
Command : cat data.txt
Password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

