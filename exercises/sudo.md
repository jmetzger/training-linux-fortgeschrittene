# Sudo 

## Übung sudo I

```
1. Lege einen neuen Nutzer teilnehmer an. 
2. Fügt diesen Nutzer der Gruppe sshadmin hinzu 
3. Fügt diesen Nutzer der Gruppe sudo hinzu 
4. Testet mit einer neuen ssh-Verbindung, ob ihr auf den server 
kommt und einen sudo Befehl ausführen könnt (z.B. sudo su) 
```

## Übung sudo II

```
adduser miniadmin
usermod -aG sshadmin miniadmin
```

```
# vi /etc/sudoers.d/miniadmin
miniadmin ALL=(ALL:ALL) /sbin/reboot 
```

```
# mit neuer ssh-session einloggen 
# reboot + passwrord des Benutzers miniadmin eingeben
sudo reboot 
```
