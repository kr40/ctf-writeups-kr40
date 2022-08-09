# HTB Starting Point Tier 0 - Meow

- IP Provided - 10.129.128.183

## Recon and Discovery

- nmap found - 23/tcp open  telnet    

## Analysis and Exploitation

- Using the `telnet` command to connect I was able to login with the username `root` without providing a `password`

- Using `ls` int the root directory shows we have a `flag.txt`

- `cat flag.txt` reveals the flag

## Difficulty - Very Easy

- Being the first box in the Starting Point Tier 0 this is the easiest box available
