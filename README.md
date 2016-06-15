### Virtual Host

```
# Apache
<VirtualHost *:80>
  ServerName froq.local
  DocumentRoot /var/www/froq/pub
  <Directory /var/www/froq/pub>
    Options +FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>
</VirtualHost>

# Nginx
server {
  index index.php;
  server_name froq.local;
  root /var/www/froq/pub;
  location / {
    try_files $uri $uri/ /index.php?$args;
  }
  # ... rest of config stuff
}
```

### Install Skeleton

```
~$ mkdir -p /var/www/froq \
   && cd /var/www/froq \
   && git clone git@github.com:froq/froq-app.git . \
   && composer install
```
