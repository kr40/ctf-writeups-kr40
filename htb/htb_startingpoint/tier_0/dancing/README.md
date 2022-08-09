# HTB Starting Point Tier 0 - 

- IP Provided - 10.129.213.119 

## Recon and Discovery

- nmap found - 135/tcp open  msrpc         Microsoft Windows RPC                                                                                                                                           
	       139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn                                                                                                                                   
	       445/tcp open  microsoft-ds? 

## Analysis and Exploitation

- We use `smbclient` utility to list the shares with `smbclient -L <ip>` and find that `WorkShares` is accessible to us
- We use `smbclient \\\\<ip>\\WorkShares` to login without any `password`
- Using `ls` we can see 2 user folders `Amy.J` and `James.P`
- Using `cd James.P` to change directory to `James.P` and `ls` to list the files we can see `flag.txt` 
- Using `get flag.txt` we can download the file to our system
- `cat flag.txt` reveals the flag

## Difficulty - Very Easy

- Machine introduces `SMB` and how to navigate shares using `smbclient`
