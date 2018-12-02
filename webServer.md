Run simple PHP web server
```
php -S 0.0.0.0:1234
```
## Apache
---
Start/Restart web server
```
service apache2 start
service apache2 restart
```

Config file is in `/etc/apache2/apache2.conf`

```xml
<!-- Disable Directory Indexing -->
<Directory /var/www/html/ch6/images/>
        Options Indexes
</Directory>
```

LAMP stack on Ubuntu 14.04

```
apt update
apt install apache2
apt install php
apt install php5-mysqlnd
apt install mysql-server
```

Run service script
```
#!/bin/bash

chown -R mysql:mysql /var/lib/mysql /var/run/mysqld

echo '[+] Starting mysql...'
service mysql start

echo '[+] Starting apache'
service apache2 start

while true
do
    tail -f /var/log/apache2/*.log
    exit 0
done
```