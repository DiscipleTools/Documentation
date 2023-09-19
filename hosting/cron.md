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
The same process has to be done on each subsite on your multisite
- http://yourdomain.com/wp-cron.php?doing_wp_cron
- http://subsite1.yourdomain.com/wp-cron.php?doing_wp_cron
- http://subsite2.yourdomain.com/wp-cron.php?doing_wp_cron
