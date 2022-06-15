# systemctl 

```
systemctl status sshd 
# Rausfinden welche aktivierten / laufenden Dienste 
systemctl list-units -t service 
# Rausfinde welche überhaupt 
systemctl list-unit-files -t service 

# Alle targets anzeigen 
systemctl list-unit-files -t target  

# is target aufrufbar ? 
systemctl cat multi-user.target | grep AllowIsolate  # should be in last line 

# default target anzeigen 
# in welches target wird gebootet 
systemctl get-default 
systemctl set-default multi-user 

# see configuration of units 
systemctl cat multi-user.target 
systemctl cat sshd.service # centos 

# show running and next scheduled timers 
systemctl list-timers 

```

## Dienste starten/aktivieren/deaktivieren/überprüfen 

```
systemctl start httpd 
systemctl start apache2 

systemctl status apache2 
systemctl status httpd 

systemctl enable apache2
systemctl enable httpd

# enable and start 
systemctl enable --now apache2
systemctl enable --now httpd 

systemctl disable apache2
systemctl disable httpd

systemctl is-enabled apache2
systemctl is-enabled httpd 
# wichtig wenn enabled rückgabe wert 0
echo $? 
0
# wenn nicht aktiviert 
echo $? 
1 
```

## Service herausfinden (wenn aktiviert) 

```
# z.B. ssh 
systemctl list-units -t service | grep ssh
```

## System runterfahren 

```
# system runterfahren und ausschalten 
systemctl poweroff 
poweroff 
```
