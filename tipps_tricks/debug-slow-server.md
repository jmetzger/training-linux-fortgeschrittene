# Debug Slow System / Not Responding (Single Services) 

## Ausgangssituation

```
Sporadisch ist der Datenbank-Server nicht zu erreichen
(Man weiss nicht genau warum) 
```

## Empfehlung 

```
Monitoring:
icinga / nagios / checkmk 

Warum: Um kontinuierlich bestimmte Daten zu tracken 
(CPU-Last, Speicher, Wieviel Prozesse gibt es von bestimmten Diensten) 
Ist der MySQL-Server erreichbar ? 
```

## Fragen während des Vorfalls 

```
top - das aber nur wenn das genau zu dem Zeitpunkt auftritt 
# Statistik Netzwerk  
ip -s link 

# Welche Dienste nehmen welchen Ressourcen 
# CPU, Speicher, IO 
ps aux | grep mysql
ps aux | grep -c apache2
ps aux | grep apache2 

# Debugging eines einzelnes Dienstes 
# Kann der x-Verbindungen handeln 
# max_connections 
# Langsame queries -> slow_query_queries -> logdatei 
```

## Probleme Datenbankserver 

```
# 1. Zu wenig Arbeitsspeicher (physisch) -> top / free  
# 2. Zu wenig Arbeitsspeicher konfiguriert (innodb_buffer_pool_size)
# 3. CPU zu langsam 
# 4. I/O (input/output) - Last -> Platte zu langsam 
```

## CPU - langsam 

```
top 

% bei CPU (be/us bzw. sy) hoch 
aber wa - wert niedrig 

(Zeile 1- bis 4) 

```

## Platte ist langsam 

```
top 

% bei CPU (be/us bzw. sy) hoch 
und wa - wert hoch  

(Zeile 1- bis 4) 
```


## Baselining 

```
# Zeitpunkt: System steht unter Last, die es gut verarbeiten.
# Variante 1: Momentaufnahme. 


# Variante 2: Für wieviel IOPS / Input/Ouput Operationen ist denn meine Platte gut 
# Man schickt so viel wie möglich daten auf die platte 
# Meine beste Performance-Möglichkeit 


# Während das Problem auftritt vergleichen 
vmstat / iostat 
```
