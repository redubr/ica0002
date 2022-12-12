# Restore mysql
as root user
duplicity --no-encryption restore rsync://redubr@backup.infra.rd/mysql /home/backup/restore/mysql
mysql agama < /home/backup/restore/mysql/agama.sql