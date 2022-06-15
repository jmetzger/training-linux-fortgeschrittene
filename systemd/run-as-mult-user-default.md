# Server mit Default-Target Multi-user laufen lassen

```
systemctl get-default # Was der aktuelle Endzustand nach booten 
# z.B. graphical 

# Während der Laufzeit in anderes Target wechseln 
systemctl isolate multi-user.target 

# Festlegen in welches Target er nach dem Booten gehen 
systemctl set-default multi-user.target

# Zum Testen 
reboot 

```
