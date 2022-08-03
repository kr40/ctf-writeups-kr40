# HTB Starting Point Tier 1 - Meow

- IP Provided - 10.129.128.183

## Basic Recon

- nmap found - 23/tcp open  telnet    

## Enumeration

- Using the `telnet` command to connect I was able to login with the username `root` without providing a `password`

- Using `ls` int the root directory shows we have a `flag.txt`

- `cat flag.txt` reveals the flag

## Difficulty - Very Easy

- Being the first box in the Starting Point Tier 1 this is the easiest box available
