# Log Rotation Using logrotate in Linux


### Step 1: Create a Logrotate Configuration File

1. **Create or Edit the Configuration File**:
   Use your preferred text editor (`nano`, `vim`, `gedit`, etc.) to create a configuration file for `logrotate`. For example:

   ```bash
   sudo nano /etc/logrotate.d/myapp


### Add Configuration:
Insert the following content into the file to configure log rotation for   **`/var/log/myapp.log`**

```bash
/var/log/myapp.log {
    daily
    rotate 7
    compress
    delaycompress
    missingok
    notifempty
}
```bash

Step 2: Save the Configuration File
Save the changes to  **`/etc/logrotate.d/myapp`**

### Configuring a Cron Job for Logrotate
Edit the Crontab:
Configure a cron job to run logrotate every 10 minutes between 2 AM and 4 AM. Edit the crontab file:

```bash
sudo crontab -e

Add Cron Job Entry:
Add the following cron job entry to the crontab file:

*/10 2-3 * * * /usr/sbin/logrotate /etc/logrotate.conf
