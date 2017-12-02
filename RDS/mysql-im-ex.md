##To export db from RDS

'mysqldump -h rds.host.name -u remote_user_name -p remote_db > remote_db.sql'

When prompted for password, provide the password

##To import db on RDS

'''mysql -h rds.host.name -u remote_user_name -p remote_db < remote_db.sql'''

When prompted for password, provide the password
