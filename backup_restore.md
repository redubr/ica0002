# Restore mysql
## As backup user

### Download backup from server
`sudo runuser -u backup -- duplicity --no-encryption restore rsync://redubr@backup.infra.rd/mysql /home/backup/restore/mysql`

## as root user:
`mysql agama < /home/backup/restore/mysql/agama.sql`

# Restore influxDB telegraf database

### Download backup
`sudo runuser -u backup --  duplicity --no-encryption restore rsync://redubr@backup.infra.rd/influxdb /home/backup/restore/influxdb`

### As root user stop telegraf service, delete telegraf database, restore and restart
`service telegraf stop`
`influx -execute 'DROP DATABASE telegraf'`
`influxd restore -portable -database telegraf /home/backup/restore/influxdb`
`service telegraf start`