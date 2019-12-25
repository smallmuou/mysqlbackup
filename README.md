# mysqlbackup

mysqlbackup -  the MySQL backup tool

```bash
USAGE: mysqlbackup [OPTIONS] target_dir [keep_count]

DESCRIPTION:

mysqlbackup -  the MySQL backup tool

target_dir is the directory that backup data location. keep_count is the number copies keep, the minimum is 1, default is 3.

OPTIONS:
    -h  host name, default is localhost.
    -u  user,  default is root.
    -p  password, default is empty.
    -P  port, default is 3306.

EXAMPLES:
    mysqlbackup -u root -p test /srv/backups 3
    mysqlbackup -h 192.168.1.100 -P 3306 -u root -p test /srv/backups 3
```

## INSTALL

```
curl https://raw.githubusercontent.com/smallmuou/mysqlbackup/master/mysqlbackup >/usr/local/bin
chmod +x /usr/local/bin/mysqlbackup
```

## BACKUP

Backup 192.168.1.100 mysql to /srv/backups, and keep latest 3 copies.

```bash
mysqlbackup -h 192.168.1.100 -P 3306 -u root -p test /srv/backups 3
```

## AUTOMATIC

You also can use cron to backup automitic like follow:

```bash
0 2 * * * /usr/local/bin/mysqlbackup -h 192.168.1.100 -P 3306 -u root -p test /srv/backups 3 
```
NOTE: cron environment variable PATH not include /usr/local/bin, you need type full path of mysqlbackup