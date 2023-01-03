## Coverage
Backup coverage is mysql database - backed daily.  
influxdb log database - backed daily.  
ansible repository - covers applications.

## RPO
Maximum amount of data that can be lost is one day. Past this is unacceptable data loss.



## Versioning and retention

Versioning:  

MySql:
Daily backups 00.00am.  
Full upload sunday 1am.  
Incremental mon-sat 1am.  

InfludDB:  
Daily backups 00.10 am.  
Full upload At 01:00 on Sunday.  
Incremental backups At 01:00 on every day-of-week from Monday through Saturday.  
Backups will be retained for 1 year, including offsite backups. 

## Usability checks
Backup usability will be verified in a testing environment before used in production.

## Restoration criteria
Backups should be restored when data is lost or broken.

## RTO
To not cause business damage - backups should be restored within 1 hour and 12 minutes (allowed downtime). Provided service must be availiable at least 95% in a year. 

## Make a backup

`sudo runuser -u backup -- mysqldump agama > /home/backup/mysql/agama.sql`
`sudo runuser -u backup -- duplicity --no-encryption full /home/backup/mysql/ rsync://redubr@backup.infra.rd/mysql`
