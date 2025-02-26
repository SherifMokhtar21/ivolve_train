# Lab 2: MySQL Installation and  Schedule a script to run weekly at 5:00 PM that automates Backup of DataBase . 
This lab covers the installation of MySQL on a Red Hat-based system and the automation of database backups using a scheduled cron job.  

## Steps
### 1. Install MySQL Server
```
sudo yum install -y mysql-server

sudo systemctl start mysqld
sudo systemctl enable mysqld
```
### 2. 2. Secure MySQL Installation
Run the security script to set a root password and secure MySQL:
```
sudo adduser sherif
sudo passwd sherif

```
### 3. Create a Backup Script
```
sudo nano /usr/local/bin/mysql_backup.sh
```
### 4. Write Backeup Script
```
#!/bin/bash

# Variables
BACKUP_DIR="/backup/mysql"
TIMESTAMP=$(date +%Y-%m-%d_%H-%M-%S)
BACKUP_FILE="$BACKUP_DIR/mysql_backup_$TIMESTAMP.sql"
MYSQL_USER="root"
MYSQL_PASSWORD="your_password"

# Ensure the backup directory exists
mkdir -p $BACKUP_DIR

# Perform the backup
mysqldump -u $MYSQL_USER -p$MYSQL_PASSWORD --all-databases > $BACKUP_FILE

```
### 5. Make the Script Executable
```
sudo chmod +x /usr/local/bin/mysql_backup.sh

```
### 6. Schedule the Backup to Run Every Sunday at 5:00 AM
```
sudo crontab -e

0 5 * * 0 /usr/local/bin/mysql_backup.sh

```


