# Regelmäßige Tätigkeiten 

## Überwachen: Automatisch oder händisch 

```
o Festplatte voll / Überwachung einrichten / Benachrichtigung bei 95% 
df / 
df /boot 

```

## Adminstratorische Tätigkeiten 

```
# Patchen ... 
# Wichtig: Wenn neuer kernel / neue initramfs - muss ! neu gebootet werden
# AUSSER: live-updates
apt update; apt upgrade; apt dist-upgrade;

# Aufräumen - regelmäßig 
apt autoremove 

# Aufräumen, files, die nicht mehr benötigt werden
# Wenn das nicht logrotate schon macht 
```

## Sicherheits-administratorische Tätigkeiten 

```
# Sind ports auf, die nicht offen sein sollen.
# Läuft Software, die nicht laufen soll. 
lsof -i 

# Als halb-automatische Alternative --> Vulnerability Scanner 
# OpenVAS -> Appliance 

# Gibt es da user, die da nicht hingehören 
```
