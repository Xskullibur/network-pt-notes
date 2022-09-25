# Medusa

## Common Commands
```bash
# Bruteforcing Specific Username
> medusa -h 192.168.1.1 -u John -P rockyou.txt -M ssh -t 100 -f 

# Bruteforcing Specific Password
> medusa -h 192.168.1.1 -U users.txt -p Pasword123 -M ftp -t 100 -f 

# Bruteforcing Login Credentials
> medusa -h 192.168.1.1 -U users.txt -P rockyou.txt -M ftp -t 100 -f 

# Bruteforcing on Multiple Host
> medusa -H hosts.txt -U user.txt -P pass.txt -M ftp -t 100 -f
```

## Modules
> Specify `medusa -q -M <module>` for more information about the module

|Module|Description|
|---|---|
|afp |AFP sessions|
|cvs |CVS sessions|
|ftp |FTP/FTPS sessions|
|http |HTTP|
|imap |IMAP sessions|
|mssql |MSSQL sessions|
|mysql |MySQL sessions|
|nntp |NNTP sessions|
|pcanywhere |PcAnywhere sessions|
|pop3 |POP3 sessions|
|postgres |PostgreSQL sessions|
|rdp |RDP (Microsoft Terminal Server) sessions|
|rexec |REXEC sessions|
|rlogin |RLOGIN sessions|
|rsh |RSH sessions|
|smbnt |SMB (LM/NTLM/LMv2/NTLMv2) sessions|
|smtp-vrfy |verifying SMTP accounts (VRFY/EXPN/RCPT TO)|
|smtp |SMTP Authentication with TLS|
|snmp |SNMP Community Strings|
|ssh |SSH v2 sessions|
|svn |Subversion sessions|
|telnet |telnet sessions|
|vmauthd |the VMware Authentication Daemon|
|vnc |VNC sessions|
|web-form |web form|
|wrapper | Generic Wrapper Module|

# Hashcat

## Common Commands
```bash
# Benchmark MD4 hashes
hashcat -b -m 900

# Create a hashcat session to hash Kerberos 5 tickets using wordlist
hashcat -m 13100 -a 0 --session crackin1 hashes.txt wordlist.txt -o output.pot

# Crack MD5 hashes using all char in 7 char passwords
hashcat -m 0 -a 3 -i hashes.txt ?a?a?a?a?a?a?a -o output.pot

# Crack SHA1 by using wordlist with 2 char at the end 
hashcat -m 100 -a 6 hashes.txt wordlist.txt ?a?a -o output.pot

# Crack WinZip hash using mask (Summer2018!)
hashcat -m 13600 -a 3 hashes.txt ?u?l?l?l?l?l?l?d?d?d?d! -o output.pot

# Crack MD5 hashes using dictionnary and rules
hashcat -a 0 -m 0 example0.hash example.dict -r rules/best64.rules

# Crack MD5 using combinator function with 2 dictionnaries
hashcat -a 1 -m 0 example0.hash example.dict example.dict

# Cracking NTLM hashes
hashcat64 -m 1000 -a 0 -w 4 --force --opencl-device-types 1,2 -O d:\hashsample.hash "d:\WORDLISTS\realuniq.lst" -r OneRuleToRuleThemAll.rule

# Cracking hashes from kerberoasting
hashcat64 -m 13100 -a 0 -w 4 --force --opencl-device-types 1,2 -O d:\krb5tgs.hash d:\WORDLISTS\realhuman_phill.txt -r OneRuleToRuleThemAll.rule
```

```bash
# You can use hashcat to perform combined attacks
# For example by using wordlist + mask + rules
hashcat -a 6 -m 0 prenoms.txt ?d?d?d?d -r rules/yourule.rule

# Single rule used to uppercase first letter --> Marie2018
hashcat -a 6 -m 0 prenoms.txt ?d?d?d?d -j 'c'
```

## Cheatsheets
- [Bruteforcing](https://github.com/frizb/Hashcat-Cheatsheet#using-hashcat-bruteforcing)
- [Linux Hashes](https://github.com/frizb/Hashcat-Cheatsheet#cracking-linux-hashes---etcshadow-file)
- [Windows Hashes](https://github.com/frizb/Hashcat-Cheatsheet#cracking-windows-hashes)
- [Application Hashes](https://github.com/frizb/Hashcat-Cheatsheet#cracking-common-application-hashes)
- [File Password Protections](https://github.com/frizb/Hashcat-Cheatsheet#cracking-common-file-password-protections)
- [Database Hash Formats](https://github.com/frizb/Hashcat-Cheatsheet#cracking-commmon-database-hash-formats)