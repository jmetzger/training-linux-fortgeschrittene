# ssh - Server absichern 

## Walktrough 

```
# Nur Nutzer, die in einer bestimmten Gruppe sind, 
# dürfen sich per ssh anmelden 
```

```
addgroup sshadmin 
usermod -aG sshadmin kurs 
# einen Referenzuser anlegen, zum Testen, dass es nicht geht 
addgroup training
```

```
# Konfigurationsdatei anpassen 
echo "AllowGruops sshadmin" >> /etc/ssh/sshd_config 
```

```
# Server neu durchladen 
systemctl reload ssh
systemctl status ssh
```

## Testen mit funktionierendem User 

```
# neue ssh-Session mit User kurs (neu einloggen) 
ssh kurs@192.168.56.103 

# Hat funktioniert ! 
```

## Testen mit nicht funktionierendem User 

```
# Warum ? Ist nicht in der Gruppe sshadmin
ssh training@192.168.56.103 
```

## Analyse des Nichteinloggens von training

```
systemctl status ssh
journalctl -u ssh 

# bzw alte Logs 
tail -n 50 /var/log/auth.og

```

```
