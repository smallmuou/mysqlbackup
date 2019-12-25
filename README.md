# mysqlbackup

mysqlbackup -  the MySQL backup tool

```bash
USAGE: mysqlbackup [OPTIONS] target_dir [database, database ...]

DESCRIPTION:

mysqlbackup -  the MySQL backup tool

target_dir    the directory that backup data location
database      the database that need backup, if not assign, backup all database exclude 'mysql', 'information_schema', 'performance_schema'

OPTIONS:
    -h  host name, default is localhost.
    -u  user,  default is root.
    -p  password, default is empty.
    -P  port, default is 3306.
    -c  the count of latest copies to keep,  the minimum is 1, default is 3.

EXAMPLES:
    mysqlbackup -u root -p test /srv/backups mydb
    mysqlbackup -h 192.168.1.100 -P 3306 -u root -p test -c 3 /srv/backups
```

## INSTALL

```
curl https://raw.githubusercontent.com/smallmuou/mysqlbackup/master/mysqlbackup > /usr/local/bin/mysqlbackup
chmod +x /usr/local/bin/mysqlbackup
```
You need add /usr/local/bin to environment variable PATH

## BACKUP

Backup 192.168.1.100 mysql to /srv/backups, and keep latest 3 copies.

```bash
mysqlbackup -h 192.168.1.100 -P 3306 -u root -p test -c 3 /srv/backups
```

## AUTOMATIC

You also can use cron to backup automitic like follow:

```bash
0 2 * * * /usr/local/bin/mysqlbackup -u root -p test -c 3 /srv/backups
```
NOTE: cron environment variable PATH not include /usr/local/bin, you need type full path of mysqlbackup