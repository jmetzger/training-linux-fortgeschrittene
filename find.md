# Find 

## Simple find command 

```
# find directories with specific name 
find / -name tmpfiles.d -type d 
```

## Search for all directories match 'ic' 

```
find / -type d -name '*ic*'
```

## Complex example with own script 

```
# vi /usr/local/bin/ausgabe.sh
#!/bin/bash
# $1 ist der 1. Parameter der nach dem Scriptname übergeben wird 
# z.B. ausgabe.sh hallo
echo "mein file...."$1 
```

```
chmod u+x ausgabe.sh 
```

```
find /etc/ -type f -name '*init*' -exec ausgabe.sh {} \;
```
