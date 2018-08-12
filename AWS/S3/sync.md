## Install AWSCLI

``sudo apt-get install awscli``

## Configure AWS IAM
``aws configure``

please configure only for specific linux user.

### Enter your Access Key, Secret Key, Default Region

```
AWS Access Key ID [None]: XXXXXXXXXXXXXXX
AWS Secret Access Key [None]: XXXXXXXXXXXXXXXXX
Default region name [None]: eu-central-1
Default output format [None]: 
```
### Navigate to folder (e.g. webroot or image backup)

``cd /srv/users/serverpilot/apps/yourappname/public``

## Sync from EC2/ Lightsail to S3 bucket
``aws s3 sync . s3://YOURBUCKETNAME``

## Sync from S3 bucket to EC2/ Lightsail
``aws s3 sync s3://YOURBUCKETNAME .``
