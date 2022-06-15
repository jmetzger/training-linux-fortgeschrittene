# Journalctl 

## journalctl 

```
# ubuntu
journalctl -u ssh 
journalctl -u ssh.service 

# alles was pid xy
# man systemd.journal-fields 
journalctl _PID=5 

# alles seit gestern 
journalctl --since yesterday 
# alles bis gestern 
journalctl --until yesterday

# sehr schön um alle felder zu sehen 
journalctl -o json-pretty 
```

## journalctl - Ausgabeformate 

```
journalctl -u ssh -o json-pretty 

```

## journalctl - Zeitbereiche 

```
journalctl -u ssh --since "2022-06-15 11:45"
```

## Nur die letzten Einträge, z.B. 5 

```
journalctl -u ssh --since "2022-06-15 11:45" -n 5
```

## ssh 

```
# Fenster 1 
journalctl -u ssh -f 

# Fenster 2:
systemctl restart ssh

# Back to Fenster 1 

```

## Show all boots 

``` 
 journalctl --list-boots
 0 3c3cf780186642ae9741b3d3811e95da Tue 2020-11-24 14:29:44 CET▒<80><94>T>
lines 1-1/1 (END)
```

## Journal persistent 

  * Normalerweise (auf den meisten Systemen), überlebt das Journal kein Reboot 
 
```
# persistent setzen
# Achtung: in /etc/systemd/journald.conf muss Storage=auto gesetzt sein
# Dies ist auch der Default - Fall 
# Achtung Achtung: Alle gezeigten Einträge mit # am Anfang sind die Default-Werte (in journald.conf) 
mkdir /var/log/journal 
systemctl restart systemd-journal-flush.service 

```

## Restrict how much is logged / data 

```
# in /etc/systemd/journald.conf 
SystemMaxUse=1G 
```

