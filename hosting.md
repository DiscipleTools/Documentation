# Developer Docs

## Hosting

https://disciple.tools/dev-docs/hosting/

## Backups

You know that you need to keep your data backed up. Here are some things to keep in mind. Not all backups are equal. You need to have a backup that you can access if your website goes down or if your hosting provider accidentally deletes your account (this happens). This means that any backup that stays on the server your site is on isn’t a reliable backup. You must have a secure remote backup of you Disciple.Tools instance. This can be with Amazon S3, Google Drive or any other secure storage location.

### UpdraftPlus

We recommend and use UpdraftPlus for our backups. The free version does not backup Disciple.Tools data, so to use this plugin you must pay for the premium account. See UpdraftPlus for more info.

### BackWPup

We’ve also tested BackWPup: https://wordpress.org/plugins/backwpup/. This plugin is free but more difficult to set up.

## CRON

Disciple.Tool relies on cron jobs for certain activities. Some of these are sending scheduled emails and creating update needed notifications.

WordPress’s default scheduling strategy depends on traffic. So then if no one comes to the site, the task may not run for a while. It will wait until the next visitor opens the site. A normal Disciple.Tools instance will not generate much traffic. This also slows down the server for this visitor as all these background tasks are now running.

The solution is to disable the WP cron strategy. To do this, open the wp-config.php file and add the following line before the “/_ That’s all, stop editing! Happy blogging. _/” line:

`define('DISABLE_WP_CRON', true);`

Then you want to setup a cron on your server or with your hosting service to run every 15 mins:

`* /15 * * * * wget -q -O - http://yourdomain.com/wp-cron.php?doing_wp_cron >/dev/null 2>&1`

If these instructions don’t make sense, google the name of you hosting service and Replace WordPress Cron

An alternative to setting up a cron job is to use a service like Uptime Robot which will ping your server every interval.

For WPEngine see: https://wpengine.com/support/wp-cron-wordpress-scheduling/

## 404 Errors on new install

If you installed Disciple.Tools and are getting 404 errors or /contacts or other pages try this: Log in to wp-admin and go to Settings > Permalinks. You don’t need to change anything, just click [`save`] at the bottom.

**Special Note for hosting on Windows servers**: If you receive a 404 error message when trying to preview or run DT after installing WordPress and the DT theme, check the root WordPress folder (e.g., `C:\inetpub\wwwroot\wordpress`) , and verify the `web.config` file exists. If not, create a text file named `web.config` and include the following code block in the file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
  <configuration>
    <system.webServer>
      <rewrite>
        <rules>
          <rule name="WordPress" stopProcessing="true">
            <match url="^(.*)$" />
            <conditions>
            <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
            <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
            </conditions>
            <action type="Rewrite" url="index.php" appendQueryString="true" />
          </rule>
        </rules>
      </rewrite>
    </system.webServer>
  </configuration>
```

For more information, please refer to https://www.smarterasp.net/support/kb/a1433/how-to-enable-wordpress-iis-rewrite-wordpress-iis-rewrite-example.aspx.
