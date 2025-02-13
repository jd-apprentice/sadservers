## Scenario: "Bucharest": Connecting to Postgres

### Problem

*Description*: A web application relies on the PostgreSQL 13 database present on this server. However, the connection to the database is not working. Your task is to identify and resolve the issue causing this connection failure. The application connects to a database named app1 with the user app1user and the password app1user.

### Solution

The problem itself shows that the file `pg_hba.conf` is not accepting the connection from the host `127.0.0.1`
```shell
PGPASSWORD=app1user psql -h 127.0.0.1 -d app1 -U app1user -c '\q'
psql: error: FATAL:  pg_hba.conf rejects connection for host "127.0.0.1", user "app1user", database "app1", SSL on
FATAL:  pg_hba.conf rejects connection for host "127.0.0.1", user "app1user", database "app1", SSL off
```

That file is located in `/etc/postgresql/<version>/main/pg_hba.conf`
Once inside the find that the are two lines rejecting the connection
We need to remove them

```
sudo nano /etc/postgresql/13/main/pg_hba.conf
#host    all             all             all                     reject
#host    all             all             all                     reject
```

After that, we need to restart the postgres service

```
sudo service postgresql restart
```

Now the application is able to connect

![done](../images/bucharest.png)