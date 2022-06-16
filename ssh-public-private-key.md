# ssh mit public/private key verwenden 


```
# 1. key erstellen -> ssh-keygen ohne pass
ssh-keygen

# 2. Key kopieren zum Zielsystem mit ssh-copy-id
# Das speichert das auf dem Zielsystem in 
# ~/.ssh/authorized_keys2
ssh-copy-id kurs@192.168.56.103

# 3. Prüfen ob ich mich einloggen kann: 
ssh kurs@192.168.56.103
```
