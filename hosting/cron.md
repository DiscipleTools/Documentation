# CRON

Disciple.Tools relies on cron jobs for certain activities. Some of these are sending scheduled emails and creating update needed notifications.

WordPress’s default scheduling strategy depends on traffic. So then if no one comes to the site, the task may not run for a while. It will wait until the next visitor opens the site. A normal Disciple.Tools instance will not generate much traffic. This also slows down the server for this visitor as all these background tasks are now running.


For WPEngine.com: see this section in their documentatian [https://wpengine.com/support/wp-cron-wordpress-scheduling/#WP_Engine_Alternate_Cron](https://wpengine.com/support/wp-cron-wordpress-scheduling/#WP_Engine_Alternate_Cron)
They will do everything for you.

For other hosting services: we recommend googling the name of you hosting service along with "Replace WordPress Cron"

## Doing it manually:

The solution is to disable the WP cron strategy. To do this, open the wp-config.php file and add the following line before the “/ _That’s all, stop editing! Happy blogging._ /” line:

`define('DISABLE_WP_CRON', true);`

Then,

### Option 1 - Server Cron

you want to setup a cron on your server or with your hosting service to run every 5 mins:

`*/5 * * * * wget -q -O - http://yourdomain.com/wp-cron.php?doing_wp_cron > /dev/null 2>&1`

**Note:** change `yourdomain.com` to you disciple.tools domain


### Option 2 - Outsite Cron service

An alternative to setting up a cron job is to use a service like [Uptime Robot](https://uptimerobot.com/) to ping `http://yourdomain.com/wp-cron.php?doing_wp_cron` every 5 minutes.


## On Multisites

### Option 1 
Create a cron job for each subsite
- http://yourdomain.com/wp-cron.php?doing_wp_cron
- http://subsite1.yourdomain.com/wp-cron.php?doing_wp_cron
- http://subsite2.yourdomain.com/wp-cron.php?doing_wp_cron

### Option 2
Create a script to call each subsite.
Create a file `custom-cron.sh` in the same folder as your wp-config.php

custom-cron.sh contents:
```
/usr/local/bin/php /usr/local/bin/wp site list --field=domain --archived=0 --deleted=0 | xargs -i -n1 /usr/local/bin/php /usr/local/bin/wp cron event run --due-now --url="https://{}";
```

create the cron job, replace `/path/to/wp/install` with the path to you wordpress installating.

`*/15 * * * * cd /path/to/wp/install && /path/to/wp/install/custom-cron.sh`

On a large multisite you might want to make sure cron jobs don't run at the same time. For this we create a lock file while custom-cron.sh is running.

`*/15 * * * * cd /path/to/wp/install && /usr/bin/flock -n /tmp/multisitecron.lock /path/to/wp/install/custom-cron.sh`

