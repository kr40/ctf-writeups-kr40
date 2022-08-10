# HTB Starting Point Tier 1 - Sequel 

- IP Provided - 10.129.179.130

## Recon and Discovery

- nmap found - 3306/tcp open  mysql?

## Analysis and Exploitation

- We login to the MariaDB database with `mysql -h <ip> -u root` without needing the password
- We use `SHOW databases;` to list all the databases
- We find `htb` and use `use htb;` to enter the `htb` database
- We use `SHOW tables;` to see all the tables in the database
- We see `config and users` and use `SELECT * FROM config;` to dump the contents of the table
- Dump reveals the `flag`

## Difficulty - Very Easy

- Machine introduces MySQL databases and how to use `mysql` to interact with the Databases
