## Only for Bitnami

For SSL Issued by other CA - <a href="https://github.com/digitechpoint/AWS-GCP-Azure-DO/blob/master/AWS/EC2/ssl-bitnami-wp.md">SSL bitnami</a>

### 1. Installation path
Log in to the server via ssh and navigate to following folder
```
/opt/bitnami/apps/wordpress/
```
assume your webroot path is avobe directory

### 2. Clone Letsencrypt
```
git clone https://github.com/letsencrypt/letsencrypt
cd letsencrypt
```

### 3. Stop Bitnami services

``sudo /opt/bitnami/ctlscript.sh stop``

### 3. Generate a certificate

``sudo ./letsencrypt-auto certonly --standalone -d yourdomain.com -d www.yourdomain.com``


### 4. Server config

check apache/nginx

```sudo /opt/bitnami/ctlscript.sh```

#### Apache
```
sudo mv /opt/bitnami/apache2/conf/server.crt /opt/bitnami/apache2/conf/server.crt.old
sudo mv /opt/bitnami/apache2/conf/server.key /opt/bitnami/apache2/conf/server.key.old
sudo mv /opt/bitnami/apache2/conf/server.csr /opt/bitnami/apache2/conf/server.csr.old
sudo ln -s /etc/letsencrypt/live/YOUR_DOMAIN_NAME/fullchain.pem /opt/bitnami/apache2/conf/server.crt
sudo ln -s /etc/letsencrypt/live/YOUR_DOMAIN_NAME/privkey.pem /opt/bitnami/apache2/conf/server.key
sudo chown root:root /opt/bitnami/apache2/conf/server*
sudo chmod 600 /opt/bitnami/apache2/conf/server*
```

#### Nginx
```
sudo mv /opt/bitnami/nginx/conf/server.crt /opt/bitnami/nginx/conf/server.crt.old
sudo mv /opt/bitnami/nginx/conf/server.key /opt/bitnami/nginx/conf/server.key.old
sudo mv /opt/bitnami/nginx/conf/server.csr /opt/bitnami/nginx/conf/server.csr.old
sudo ln -s /etc/letsencrypt/live/YOUR_DOMAIN_NAME/fullchain.pem /opt/bitnami/nginx/conf/server.crt
sudo ln -s /etc/letsencrypt/live/YOUR_DOMAIN_NAME/privkey.pem /opt/bitnami/nginx/conf/server.key
sudo chown root:root /opt/bitnami/nginx/conf/server*
sudo chmod 600 /opt/bitnami/nginx/conf/server*
```

### 5. Start Bitnami

``sudo /opt/bitnami/ctlscript.sh start``

<hr>

> Install "<a href="https://wordpress.org/plugins/really-simple-ssl/">Really Simple SSL</a>" to fix mix content issue and auto redirect to https.


Other Resources: <a href="https://docs.bitnami.com/aws/how-to/get-started-wordpress-aws-marketplace-intermediate/#secure-wordpress-with-a-lets-encrypt-ssl-certificate">AWS</a> - <a href="https://docs.bitnami.com/aws/how-to/generate-install-lets-encrypt-ssl/#introduction">GCloud</a>
