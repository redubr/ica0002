## Coverage
Covered are all mysql databases, InfluxDB log database and Ansible repository.

## RPO
MySql daily backups 00.00
Full upload sunday 1am
Incremental mon-sat 1am

## Versioning and retention

## Usability checks

## Restoration criteria

## RTO

## Make a backup

sudo runuser -u backup -- mysqldump agama > /home/backup/mysql/agama.sql
sudo runuser -u backup -- duplicity --no-encryption full /home/backup/mysql/ rsync://redubr@backup.infra.rd/mysql
