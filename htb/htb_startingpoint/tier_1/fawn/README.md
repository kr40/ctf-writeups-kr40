# HTB Starting Point Tier 1 - Fawn

- IP Provided - 10.129.1.14

## Recon and Discovery

- nmap found - 21/tcp open  ftp     syn-ack ttl 63 vsftpd 3.0.3
	- ftp-anon: Anonymous FTP login allowed (FTP code 230)

## Analysis and Exploitation

- Using the `ftp` utility and `anonymous:anonymous` I was able to login
- Using the `ls` command I was able to see `flag.txt`
- Using the `get flag.txt` command I was able to download `flag.txt` 
- `cat flag.txt` reveals the flag

## Difficulty - Very Easy

- Machine Introduces `ftp anonymous login` through which we are able to login to `ftp` service with `anonymous:anonymous` as credentials
