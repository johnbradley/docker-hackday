
Given a database mariadb/postgres running in a docker container back it up to a volume.
We would like to put the command in cron without including the password so we can periodically backup the database.


MariaDB:
The mariadb container has environment variables for the MYSQL_* user/password etc.
So we were able to run this:
```
docker exec -i -t <name> sh -c 'mysqldump --password=$MYSQL_ROOT_PASSWORD --all-databases'
```
Using ```sh --c '...'``` uses the environment variables in the container we are exec'ing in.


Postgres:
So we were able to run this:
```
docker exec -i -t some-postgres pg_dumpall -U postgres
```
