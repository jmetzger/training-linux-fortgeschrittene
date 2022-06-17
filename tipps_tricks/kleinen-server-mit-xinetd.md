# Kleinen Server mit xinetd 

## Schritt 1: Auf Server 1)

```
apt install -y xinetd 
```

```
# nano /etc/xinetd.d/test 
service test
{
        socket_type = stream
        protocol    = tcp
        port        = 3000
        type        = UNLISTED
        wait        = no
        user        = nobody
        server      = /bin/echo
        server_args = Hallo Welt!
}
```

```
systemctl reload xinetd 
systemctl status xinetd 

# Läuft xinetd auf diesem port 3000 
lsof -i 
```

## Schritt 2: Auf Server 2

```
apt install -y telnet 
# Server 1: 192.168.56.103 
telnet 192.168.56.103 3000
# Jetzt sollte Hello World kommen 

```
