# RCJ Soccer Scoring Platform

This system manages the soccer draws, refereeing and scoring for RoboCup Junior Australia.

TODO: Dockerize it.

To configure, pass in environment variables, start MariaDB and then run the image:

```bash
export RCJ_DATABASE_CONNECTION="mysql+pymysql://YOUR_DB_USER:YOUR_DB_PASS@localhost/YOUR_DB_NAME"
export RCJ_SMS_USERNAME="YOUR_SMS_BROADCAST_ACCOUNT"
export RCJ_SMS_PASSWORD="YOUR_SMS_BROADCAST_PASSWORD"
export RCJ_SMS_FROM="RoboCupJnr"
export RCJ_SECRETS_KEY="YOUR_SECRET_KEY"

docker build -t rcj-soccer-platform .

docker run --name=mariadb -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=YOUR_DB_PASS centos/mariadb

docker run -e "RCJ_DATABASE_CONNECTION=$RCJ_DATABASE_CONNECTION" \
-e "RCJ_SMS_USERNAME=$RCJ_SMS_USERNAME" \
-e "RCJ_SMS_PASSWORD=$RCJ_SMS_PASSWORD" \
-e "RCJ_SMS_FROM=$RCJ_SMS_FROM" \
-e "RCJ_SECRETS_KEY=$YOUR_SECRET_KEY" \
-p 80:5000 rcj-soccer-platform
```