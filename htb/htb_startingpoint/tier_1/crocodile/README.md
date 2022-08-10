# HTB Starting Point Tier 1 - Crocodile

- IP Provided - 10.129.1.15

## Recon and Discovery

- nmap found - 21/tcp open  ftp     vsftpd 3.0.3  ftp-anon: Anonymous FTP login allowed (FTP code 230)
						  80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
-   gobuster found - /login.php (Status: 200)
						 

## Analysis and Exploitation

- We see that anonymous login is allowed on ftp server so we use `ftp <ip>` and `anonymous` as login
- Using `ls` we find 2 files `allowed.userlist` and `allowed.userlist.passwd` 
- Using `mget *` we download both and see the contents, it has usernames and passwords
- We see that `admin` is a user that might have the highest privileges
- We check the webpage, it does not have a login area
- We use `gobuster dir -u http://<ip>  -w <wordlist> -x php` to find additional directories ending in.php
	- Kali has wordlist located at `/usr/share/wordlists`
- We find `/login.php` and we try `admin` as user name with different passwords
- Logging in as admin reveals the `flag`

## Difficulty - Very Easy

- Machine introduces `ftp` utility and how to download files using `get or mget` and using `gobuster` to search additional directories
