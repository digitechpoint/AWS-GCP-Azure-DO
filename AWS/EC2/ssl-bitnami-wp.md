## SSL Setup

### 1. Installation path
Log in to the server via ssh and navigate to following folder
```
/opt/bitnami/apps/wordpress/
```
assume your webroot path is avobe directory

### 2. Create new folders 
```
mkdir certs
cd certs
mkdir YOUR_DOMAIN_NAME
cd YOUR_DOMAIN_NAME
```
### 3. Generate CSR & Private Key
```
(umask 077 && touch ssl.key)
openssl req -new -newkey RSA:2048 -nodes -keyout ssl.key -out ssl.csr
```

### 4. Stop Bitnami services

``sudo /opt/bitnami/ctlscript.sh stop``

### 3. Upload certificate

Create a file named `ssl.crt` and copy/paste your certificates according to the following order.
```
1. Your_SSL.crt
2. USERTrustRSADomainValidationSecureServerCA.crt
3. USERTrustRSAAddTrustCA.crt
4. AddTrustExternalCARoot.crt
```

Upload `ssl.crt` to your created path

``/opt/bitnami/apps/wordpress/certs/YOUR_DOMAIN_NAME``

### 4. Server config

check apache/nginx

```sudo /opt/bitnami/ctlscript.sh status```

#### Apache
```
sudo mv /opt/bitnami/apache2/conf/server.crt /opt/bitnami/apache2/conf/server.crt.old
sudo mv /opt/bitnami/apache2/conf/server.key /opt/bitnami/apache2/conf/server.key.old
sudo mv /opt/bitnami/apache2/conf/server.csr /opt/bitnami/apache2/conf/server.csr.old
sudo ln -s /opt/bitnami/apps/wordpress/certs/YOUR_DOMAIN_NAME/ssl.crt /opt/bitnami/apache2/conf/server.crt
sudo ln -s /opt/bitnami/apps/wordpress/certs/YOUR_DOMAIN_NAME/ssl.key /opt/bitnami/apache2/conf/server.key
sudo chown root:root /opt/bitnami/apache2/conf/server*
sudo chmod 600 /opt/bitnami/apache2/conf/server*
```

#### Nginx
```
sudo mv /opt/bitnami/nginx/conf/server.crt /opt/bitnami/nginx/conf/server.crt.old
sudo mv /opt/bitnami/nginx/conf/server.key /opt/bitnami/nginx/conf/server.key.old
sudo mv /opt/bitnami/nginx/conf/server.csr /opt/bitnami/nginx/conf/server.csr.old
sudo ln -s /opt/bitnami/apps/wordpress/certs/YOUR_DOMAIN_NAME/ssl.crt /opt/bitnami/apache2/conf/server.crt
sudo ln -s /opt/bitnami/apps/wordpress/certs/YOUR_DOMAIN_NAME/ssl.key /opt/bitnami/apache2/conf/server.key
sudo chown root:root /opt/bitnami/nginx/conf/server*
sudo chmod 600 /opt/bitnami/nginx/conf/server*
```

### 5. Start Bitnami

``sudo /opt/bitnami/ctlscript.sh restart``

<hr>

> Install "<a href="https://wordpress.org/plugins/really-simple-ssl/">Really Simple SSL</a>" to fix mix content issue and auto redirect to https.
> Bitnami Docs: <a href="https://docs.bitnami.com/bch/infrastructure/lamp/administration/create-ssl-certificate-apache/">Create An SSL Certificate</a> - <a href="https://docs.bitnami.com/bch/infrastructure/lamp/administration/enable-https-ssl-apache/">Enable HTTPS Support</a> 
> Validation Tool: <a href="https://www.sslchecker.com/sslchecker">SSL Checker</a>
