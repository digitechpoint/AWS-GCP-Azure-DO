## Install Certbot

```
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

## Issue SSL
```
sudo certbot certonly --agree-tos --email sam@azgor.com --webroot -w /srv/users/digitechpoint/apps/digitechpoint/public -d digitechpoint.com -d www.digitechpoint.com
```

## Symlink the ssl path
```
sudo ln -sf /etc/letsencrypt/live/digitechpoint.com/fullchain.pem /etc/nginx-sp/ssl/digitechpoint.combined_crt
sudo ln -sf /etc/letsencrypt/live/digitechpoint.com/privkey.pem /etc/nginx-sp/ssl/digitechpoint.key
```

Dont forget to replace the `APP NAME`, `DOMAIN NAME` and `WEB ROOT PATH` from above.


Ref: https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal
