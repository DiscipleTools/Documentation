# CRON

Disciple.Tools relies on cron jobs for certain activities. Some of these are sending scheduled emails and creating update needed notifications.

WordPress’s default scheduling strategy depends on traffic. So then if no one comes to the site, the task may not run for a while. It will wait until the next visitor opens the site. A normal Disciple.Tools instance will not generate much traffic. This also slows down the server for this visitor as all these background tasks are now running.

The solution is to disable the WP cron strategy. To do this, open the wp-config.php file and add the following line before the “/ _That’s all, stop editing! Happy blogging._ /” line:

`define('DISABLE_WP_CRON', true);`

Then you want to setup a cron on your server or with your hosting service to run every 15 mins:

`*/15 * * * * wget -q -O - http://yourdomain.com/wp-cron.php?doing_wp_cron >/dev/null 2>&1`

If these instructions don’t make sense, google the name of you hosting service and Replace WordPress Cron

An alternative to setting up a cron job is to use a service like Uptime Robot which will ping your server every interval.

For WPEngine see: [https://wpengine.com/support/wp-cron-wordpress-scheduling/](https://wpengine.com/support/wp-cron-wordpress-scheduling/)

