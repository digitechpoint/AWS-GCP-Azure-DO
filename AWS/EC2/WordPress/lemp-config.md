Create or modify your website block config file.

```
sudo nano /etc/nginx/sites-available/wordpress
```

Replace the domain name (`digitechpoint.com`) and webroot path (`/home/dtp/apps/digitechpoint/public`) & `php7.2-fpm` version.

```
server {
  listen 80;
  listen [::]:80;

  listen 443 ssl;
  listen [::]:443 ssl;

  ssl_protocols SSLv3 TLSv1;
  ssl_ciphers ALL:!aNULL:!ADH:!eNULL:!LOW:!EXP:RC4+RSA:+HIGH:+MEDIUM;
  server_name digitechpoint.com www.digitechpoint.com;
  keepalive_timeout 75 75;
  ssl on;
  ssl_certificate /etc/letsencrypt/live/digitechpoint.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/digitechpoint.com/privkey.pem;
  ssl_session_timeout  5m;
  add_header Strict-Transport-Security "max-age=7200";
  ssl_stapling on;
  ssl_stapling_verify on;

root /home/dtp/apps/digitechpoint/public;
  index index.php index.html index.htm;
server_name digitechpoint.com www.digitechpoint.com;
error_page 404 /404.html;
  error_page 500 502 503 504 /50x.html;

  location = /50x.html {
    root /usr/share/nginx/html;
  }

  location / {
    try_files $uri $uri/ /index.php?q=$uri&$args;
  }
location ~ .php$ {
    try_files $uri =404;
    fastcgi_split_path_info ^(.+.php)(/.+)$;
    fastcgi_pass unix:/run/php/php7.2-fpm.sock;
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include fastcgi_params;
  }
location = /favicon.ico {
    log_not_found off;
    access_log off;
  }

  location = /robots.txt {
    log_not_found off;
    access_log off;
    allow all;
  }

  location ~* .(css|gif|ico|jpeg|jpg|js|png)$ {
    expires max;
    log_not_found off;
  }
```
