# Developer Docs
## Hosting
https://disciple.tools/dev-docs/hosting/

## CRON
Disciple.Tool relies on cron jobs for certain activities. Some of these are sending scheduled emails and creating update needed notifications.

WordPress’s default scheduling strategy depends on traffic. So then if no one comes to the site, the task may not run for a while. It will wait until the next visitor opens the site. A normal Disciple.Tools instance will not generate much traffic. This also slows down the server for this visitor as all these background tasks are now running.

The solution is to disable the WP cron strategy. To do this, open the wp-config.php file and add the following line before the “/* That’s all, stop editing! Happy blogging. */” line:

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
