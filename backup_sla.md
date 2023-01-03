## Coverage
Covered are all mysql databases, InfluxDB log database and Ansible repository.

## RPO
MySql: 
Daily backups 00.00.
Full upload sunday 1am.
Incremental mon-sat 1am.

InfludDB:
Daily backups 00.10 am.
Full upload At 01:00 on Sunday.
Incremental backups At 01:00 on every day-of-week from Monday through Saturday.

## Versioning and retention
Backups will be retained for 1 year, at least two backup versions avail.

## Usability checks
Backup usability will be verified in a testing environment before used in production.

## Restoration criteria
Backups should be restored when data is lost or broken.

## RTO
Backups should be restored within 5 minutes.

## Make a backup

`sudo runuser -u backup -- mysqldump agama > /home/backup/mysql/agama.sql`
`sudo runuser -u backup -- duplicity --no-encryption full /home/backup/mysql/ rsync://redubr@backup.infra.rd/mysql`
