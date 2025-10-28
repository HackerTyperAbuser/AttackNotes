### Automated
- Ingestors and automated scanning is bad for OPSEC, collect data manually for more stealthy operations.
(Bloodhound) Starting bloodhound
```bash
sudo neo4j console
bloodhound
```
(Bloodhound) Ingestors
```bash
bloodhound-python -d <DOMAIN> -u <USERNAME> -p <PASSWORD> -ns <DC-IP> -c all
```
(SharpHound) Ingestors
```bash
SharpHound.exe
```
(ldapdomaindump) Automated domain enumeration
```bash
ldapdomaindump ldaps://<LDAP_SERVER> -u <DOMAIN>\<USER> -p <PASS>
```
### Manual 
(Ldapsearch + Cobalt Strike) DC naming 
```bash
ldapsearch -H ldap://<DC-IP> -x -s base namingcontexts
```
(Ldapsearch + Cobalt Strike) User account filter
```bash
ldapsearch -H ldap://<DC-IP> -x -b "DC=baby,DC=vl" (samAccountType=805306368)
```
(Ldapsearch + Cobalt Strike) Admin accounts
```bash
ldapsearch -H ldap://<DC-IP> -x -b "DC=baby,DC=vl" (&(samAccountType=805306368)(adminCount=1))
```
(Ldapsearch + Cobalt Strike) Unconstrained Delegations
```
ldapsearch (&(samAccountType=805306369)(userAccountControl:1.2.840.113556.1.4.803:=524288)) --attributes samaccountname
```
