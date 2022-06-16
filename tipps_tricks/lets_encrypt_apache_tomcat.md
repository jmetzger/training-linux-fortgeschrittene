# SSL mit Letencrypt und Apache und Tomcat 

## apache reverse proxy aufsetzen 


```
sudo apt-get install apache2 -y
a2enmod proxy
a2enmod proxy_http
a2enmod proxy_ajp
a2enmod rewrite
a2enmod deflate
a2enmod headers
a2enmod proxy_balancer
a2enmod proxy_connect
a2enmod proxy_html
systemctl restart apache2
```

```
# Wichtig ist in apache die richtige VirtualHost config 
# vi /etc/apache2/sites-enabled/subdomain12.conf
<VirtualHost *:80>
 ServerName subdomain12.yourdomain.com
 ProxyPreserveHost On 
 DocumentRoot /var/www/html
 ProxyPass /.well-known !
 ProxyPass / http://127.0.0.1:8080/
 ProxyPassReverse / http://127.0.0.1:8080/
</VirtualHost>
```

```
systemctl reload apache2 
```

```
apt install -y python3-certbot-apache
# Startet auch den apache neu 
certbot --apache 
```

## References 

  * Take only as hint, some stuff is not optimal / like .well-known proxy pass missing
  * https://metamug.com/article/networking/lets-encrypt-ssl-on-tomcat.html
  * https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04-de


