# Grub mit password sichern 

## Secure grub with password (not at boot but for changes and subentries)

```
#  Create password 
#  e.g. password 
grub-mkpasswd-pbkdf2
```

```
# Datei anlegen 
# vi /etc/grub.d/40_custom 
# Ans Ende packen 
set superusers="grub"
password_pbkdf2 grub grub.pbkpdf2.sha512.....
```

```
## Rechte setzen 
chmod a+x /etc/grub.d/01_password 
```

```
## Wichtig: Dadurch läßt sich ohne Passwort booten 
## Datei 10_linux unter  
## Variable CLASS anpassen 
## am Ende von CLASS --unrestricted anfügn then 
## 
CLASS="--class gnu-linux ..... --unrestricted" 
```

```
update-grub 
```

## Reference:

  * https://fostips.com/password-protect-grub-bootmenu-linux/

