# HTB Starting Point Tier 1 - Ignition
- IP Provided - 10.129.1.27

## Recon and Discovery

- nmap found - 80/tcp open  http    nginx 1.14.2\
- gobuster found - /admin                (Status: 200) [Size: 7095]
						 
## Analysis and Exploitation

- We try to visit the website but get a 302 redirect
- We see it wants the host name to be `ignition.htb` so we add it to `/etc/hosts`
- We run gobuster on `ignition.htb` to find directories and come across `/admin`
- We are thrown into the Magento Login Screen
- We use `admin` as username and search for `top most used passwords`
- After trying for a bit we use `admin:qwerty123` to login
- Logging in reveals the `flag`

## Difficulty - Very Easy

- Machine introduces web fuzzing, using google to manually brute-force
