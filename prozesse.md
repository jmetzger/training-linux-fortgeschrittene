## Prozesse (inkl. Kill) 

### pstree / Baum der Prozess anzeigen 

```
pstree -p | less 

# beispiel mit finden der bash in welchen Prozessen
pstree -p | grep bash 
```

### top / Prozesse interaktiv betracht 

```
top 
q # mit q verlassen 
```

```
Bedeutung:
load average: 0.08, 0.04, 0.00

Wieviel Prozesse warten auf Ausführung durch die CPU in der/den letzten 1 min / 5 min / 15 min 
```

```
# 
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   7107.8 avail Mem

Swap - Daten die auf Festplatte ausgelagert werden, weil zu wenig Arbeitsspeicher da 
=> Achtung: Sollte auf Servern möglichst nicht > 0 sein 
=> Chef, ich brauche mehr Arbeitsspeicher (wenn > 0) 

```

### ps - prozesse anzeigen als Liste 

```
Fall 1: Alle Prozesse anzeigen 

# macht in der Regel als root 
sudo ps aux | less
sudo ps aux 

# Information über bestimmtes kommando (Alle Prozesse)  
ps aux | grep bash

# Wieviel Prozesse 
ps aux | grep bash | wc -l
ps aux | grep -c bash
```

### Beispiel: Prozess-Id (pid) finden 

```
# starter.sh ist das script was wir suchen 
ps aux | grep starter.sh # Info in Spalte 2 (Spalte 1 = user) 

# mit header
ps aux | head --lines=1; ps aux | grep starter.sh
```

### Beispiel: Prozess für Kommando in Files ausgeben

```
ps aux > /home/user/ausgabe.ps 
```

### Beenden Programme im Vordergrund 

```
sleep 1000
STRG + c # beendet das programm 
```

### ps - optionen herleiten 

```
2 Varianten:
ps aux 
ps -ef 
```

```
# Beispiele man-pages relativ weit 
man ps 
```

```
ps --help simple 
```

### kill - Signale schicken an Prozesse

kill sendet ein Signal an einen Prozess

```
# Alle möglichen Signale anzeigen 
kill -L
```

```
# das gleich wie STRG + c 
kill -15 1123 # 1123 ist die Prozess ID 
das gleich wie:
kill 1123 # da 15 das Default Signal 
```

```
# Pistolennummer
# Wir haben uns Kind 2x vorgewarnt 
kill -9 1123 
```

### Besondere Signale 

```
SIGSTOP - STRG + z (Prozess stoppen und im Arbeitsspeicher behalten) 
kill -19 1234 # SIGSTOP 

#
SIGHUP 
kill -1 1234 # Reload Configuration File 
```

### Prozess im 2. Terminal beenden 

```
# Terminal 1 
# starter.sh starten 

# Terminal 2
ps aux | grep starter.sh 
# Prozess mit PID (Prozess Id) killen -> z.b 1234
kill 1234 

# Terminal 2
# Reagiert der Prozess nicht, dann -9 (SIGKILL) nachschieben
kill -9 1234 
```

### Prozesse im Hintergrund starten / Jobs

```
# Prozess läuft komplett im Hintergrund wenn keine Ausgaben
# Ich kann weiter arbeiten im Terminal 
starter.sh & 
[1] 123607 # 1 = jobnr (nur in dieser session) // 123607 in allen Sessions verfügbar 

```

```
# Zeige alle jobs an
nobleprog@jochen-g14d:~/bin$ jobs 
[1]+  Running                 starter.sh &
# Schicke STOP signal = siehe kill -L
nobleprog@jochen-g14d:~/bin$ kill -19 %1
# War letzter Befehl erfolgreich 
nobleprog@jochen-g14d:~/bin$ echo $?
0

[1]+  Stopped                 starter.sh
nobleprog@jochen-g14d:~/bin$ fg starter.sh
starter.sh # jetzt läuft er wieder im Vordergrund 
```

### Script im Hintergrund laufen lassen (auch nach Terminal schliessen) 

```
# Terminal 1 
nohup starter.sh & 
ls -la nohup.out 
# Terminal 1 schliessen

# Terminal 2 
# Script läuft nach schliessen von Terminal 1 noch 
ps aux | grep starter.sh # Spalte 2: pid: z.b. 1234  
kill 1234 

```





