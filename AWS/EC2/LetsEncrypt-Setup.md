## Only for Serverpilot

### 1. Clone Letsencrypt

```
git clone https://github.com/letsencrypt/letsencrypt
cd /srv/users/serverpilot/letsencrypt
```

### 2. Stop server

``sudo service nginx-sp stop``

### 3. Generate a certificate

``sudo ./letsencrypt-auto certonly --standalone -d yourdomain.com -d www.yourdomain.com``

### 4. Start server

``sudo service nginx-sp start``

### 5. Config file create

```
cd /etc/nginx-sp/vhosts.d
sudo nano yourappname.ssl.conf
```

### 6. Copy this code
<a href="https://raw.githubusercontent.com/digitechpoint/AWS-GCP-Azure-DO/master/AWS/EC2/yourappname.ssl.conf">Click</a>

### 7. Restart nginx

``sudo service nginx-sp restart``

<hr>

#### If you see error <a href="https://github.com/digitechpoint/AWS-GCP-Azure-DO/blob/master/AWS/EC2/letsencrypt-error.md">See this</a>
