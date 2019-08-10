We'll create a new database and a new user on RDS via command line.

## Login via SSH
```mysql -h RDS_HOST_NAME -u RDS_MASTER_USERNAME -p```

## Create a new DB
```CREATE DATABASE new_db_name;```

replace **new_db_name** with your database name.

## Create new User
```CREATE USER 'dbuser1' IDENTIFIED BY 'password';```

replace **dbuser1** with your database user & **password** with your secure password.

## Permission change
``GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser';``

## Reload
```FLUSH PRIVILEGES;```

## Close MySQL
```EXIT;```
