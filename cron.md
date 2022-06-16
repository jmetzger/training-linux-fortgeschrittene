# Cron 

## Hourly : jede Stunden um 17 nach

```
# Wenn wir das verwenden wollen, script (ohne Endung !) und ausführbar 
# in das Verzeichnis 
# /etc/cron.hourly legen 

# Wichtig:
# Vorher einmal Script händisch ausführen, und gucken ob es funktionier
# Idealerweise schreibt das Script das auch in ein Logfile, und wir 
# können so sehen, ob es funktioniert 

```

## Weekly, Monthly 

  * Analog wie hourly 

## Auf neuen System: Dienst cron 

  * systemctl status cron.service 
  * Hier sehen, wir wann cron, den letzten Aufruf gemacht (allgemein) 


## Scripte ausführen zu speziellen Zeiten 

```
# Schritt 1: script anlegen und ausführbar machen 
# nano /usr/local/bin/script-every-minute.sh 
```

```
#!/bin/bash

LOGTO=/var/log/ausgabe-every-minute
date >> $LOGTO
cat /etc/services >> $LOGTO
date >> $LOGTO
```

```
chmod u+x /usr/local/bin/script-every-minute.sh 
```

```
# Schritt 2: Eintrag in /etc/cron.d machen 
# vi script-every-minute (Achtung ohne Endung) 
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

*/1 * * * *   root    /usr/local/bin/script-every-minute.sh
```


```
# Schritt 3: script 1x händisch testen
# Aus Schritt 3 kopieren und ausführen 
/usr/local/bin/script-every-minute.sh

```

```
# Gucken, ob script etwas gemacht hat
ls -la /var/log/ausgabe-every-minute 

```
 ## Debugging 
 
   * systemctl status cron
   * journactl -u cron 
