## To export db from RDS

```mysqldump -h rds.host.name -u remote_user_name -p remote_db > remote_db.sql```

or following command to create the filename with date.

```mysqldump -h [rds.host.name] -u [remote_user_name] -p [remote_db] > [dbname]-$(date +%F).sql```

When prompted for password, provide the **password**

## To import db on RDS

```mysql -h rds.host.name -u remote_user_name -p remote_db < remote_db.sql```

When prompted for password, provide the **password**

## To login via SSH
```mysql -h rds.host.name -u remote_user_name -p```
