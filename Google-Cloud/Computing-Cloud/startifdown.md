`sudo nano /opt/startifdown.sh`

```
#!/bin/bash
#Scripts to start services if not running
ps -ef | grep nginx |grep -v grep > /dev/null
if [ $? != 0 ]
then
       /etc/init.d/nginx start > /dev/null
fi
ps -ef | grep php7.2-fpm |grep -v grep > /dev/null
if [ $? != 0 ]
then
       /etc/init.d/php7.2-fpm start > /dev/null
fi
ps -ef | grep mysql |grep -v grep > /dev/null
if [ $? != 0 ]
then
       /etc/init.d/mysql start > /dev/null 
fi
```

Change the file permission to be executable

`chmod 755 startifdown.sh`

cron to run every 15 minutes

`*/1 * * * * /opt/startifdown.sh`
