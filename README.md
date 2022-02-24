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

**Lvl(12-13):** The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!).

```
Command : mkdir /tmp/chirag
          cp data.txt /tmp/chirag
          xxd -r data.txt data

          file data
          mv data data.gz
          gzip -d data.gz

          file data
          mv data data.bz2
          bzip -d data.bz2

          file data
          mv data data.gz
          gzip -d data.gz

          file data
          mv data data.tar
          tar -xf data.tar

          file data5.bin
          mv data5.bin data5.tar
          tar -xf data5.tar

          file data6.bin
          mv data6.bin data6.bz2
          bzip2 -d data6.bz2 

          file data6
          mv data6 data6.tar
          tar -xf data6.tar

          fiel data8.bin
          mv data8.bin data8.gz
          gzip -d data8.gz

          file data8
          cat data8

Password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

**Lvl(13-14):** The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.

Solution:
```
Command : ssh -i sshkey.private bandit14@localhost
```

**Lvl(14-15):** The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Solution:
```
Command : cat /etc/bandit_pass/bandit14
          nc localhoat 30000
          4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Password: BfMYroe26WYalil77FoDi9qh59eK5xNr
```

**Lvl(15-16):** The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Solution:
```
Command : ncat localhost 30001 --ssl
          BfMYroe26WYalil77FoDi9qh59eK5xNr     
Password: cluFn7wTiGryunymYOu4RcffSxQluehd
```

**Lvl(16-17):** The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Solution:
```
Command : nmap localhost -p 31000-32000
          ncat --ssl localhost 31790
          cluFn7wTiGryunymYOu4RcffSxQluehd
```
- Copy the text and exit.
- Make new file and copy the text to the file.
- Then follow the command.
  
 ```
Command : chmod 600 key
          ssh -i filename bandit17@bandit.labs.overthewire.org -p 2220
```

**Lvl(17-18):** There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

Solution:
```
Command : diff password.old password.new
Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```

**Lvl(18-19):** The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Solution:
```
Command : ssh bandit18@bandit.labs.overthewire.org -p  2220 cat readme 
Password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

**Lvl(19-20):** TTo gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

Solution:
```
Command : ./bandit20-do cat /etc/bandit_pass/bandit20
Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```