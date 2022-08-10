# HTB Starting Point Tier 0 - Explosion

- IP Provided - 10.129.38.155

## Recon and Discovery

- nmap found - 135/tcp  open  msrpc         Microsoft Windows RPC                                                                                                                                          
						139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn                                                                                                                                  
						445/tcp  open  microsoft-ds?                                                                                                                                                                
						3389/tcp open  ms-wbt-server Microsoft Terminal Services

## Analysis and Exploitation

- We use `xfreerdp` to interact with the RDP server
- We use `xfreerdp /v:<IP> /u:Administator /cert:ignore` to login without the password
	- Tips: 
		- Usually in windows enviornments unlike linux `root` is synonymous to `Administrator`
		- Without `/cert:ignore` flag it throws certification errors
- It opens a Windows RDP session with `flag.txt`
- Opening the `flag.txt` file reveals the flag

## Difficulty - Very Easy

- This Machine introduces RDP and `xfreerdp` utility to interact with RDP server
