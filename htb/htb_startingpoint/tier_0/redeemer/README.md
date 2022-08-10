# HTB Starting Point Tier 0 - Redeemer

- IP Provided - 10.129.179.91

## Recon and Discovery

- nmap found - 6379/tcp open  redis   Redis key-value store 5.0.7
- Tips:
	- Use `-p-` otherwise nmap won't find the port as it is not in the top 1000 used ports

## Analysis and Exploitation

- We use `redis-cli` utility to login to the Redis Database with `redis-cli -h <ip> -p 6379`
- We use `info` command to see the information about the database and find `db0` and 4 keys
- We use `select 0` to enter the database 
- We use `KEYS *` to list all the keys
- `DUMP flag` reveals the flag

## Difficulty - Very Easy

- Machine introduces Redis Database Server and `redis-cli` utility to interact with the Redis Database Server 
