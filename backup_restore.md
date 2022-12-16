# Restore mysql
## As backup user

### Download backup from server
`sudo runuser -u backup -- duplicity --no-encryption restore rsync://redubr@backup.infra.rd/mysql /home/backup/restore/mysql`

## as root user:
`mysql agama < /home/backup/restore/mysql/agama.sql`

# Restore influxDB telegraf database