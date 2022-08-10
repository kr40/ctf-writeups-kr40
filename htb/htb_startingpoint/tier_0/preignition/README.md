# HTB Starting Point Tier 0 - Preignition

- IP Provided - 10.129.179.103

## Recon and Discovery

- nmap found - 80/tcp open  http    nginx 1.14.2
- gobuster found - /admin.php            (Status: 200)

## Analysis and Exploitation

- We visit the site and find it just a basic page
- We use `gobuster dir -u http://<ip> dir  -w <wordlist> -x php,html` to search any hidden directories
	- Tips:
		- Kali has wordlists under `/usr/share/wordlists`
- We find `/admin.php` and visiting the page we see a login window
- Trying to login with weak passwords we find `admin:admin` works
- Logging in with `admin:admin` reveals the flag 

## Difficulty - Very Easy

- Machine introduces the Directory busting using `gobuster`, you also learn about different status codes and using wordlists
