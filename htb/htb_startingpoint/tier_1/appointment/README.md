# HTB Starting Point Tier 1 - Appointement

- IP Provided - 10.129.179.107

## Recon and Discovery

- nmap found - 80/tcp open  http    Apache httpd 2.4.38 ((Debian))

## Analysis and Exploitation

- We open the website to find a login page
- We try some common `login:password` strings to check
- As we cannot see any query on the address bar or error message we assume its a Blind SQL Injection
- We try some Auth Bypass Blind Sql Strings `admin'#, admin' -- ` on the login form and use any password
	- Tips:
		- Google SQL Injection Payload Auth Bypass you will come accross `https://github.com/payloadbox/sql-injection-payload-list/blob/master/Intruder/exploit/Auth_Bypass.txt`
- Using the payload reveals the `flag`

## Difficulty - Very Easy

- Machine introduces SQL injections and Blind SQL injection in particular
