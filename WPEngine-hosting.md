# Hosting on WPEngine

<!-- From [WPEngine Hosting Details](https://docs.google.com/document/d/1zZwnXtvQ7P7Tzuy5YbnwD3Lf0pzmfylY2PaX6H8QLjI/edit%23heading=h.gregd5ot7gg8) -->

## Create an account

Create an account on https://wpengine.com and pick a plan - an annual $300+ expense. 
See https://wpengine.com/plans

## Create a site.

You have the choice between a single instance and a multisite instance.

A single instance is fine if you have one team in one location.

You'll want a multisite if you have multiple teams, multiple locations, or need more control over who has access to what. 

We recommend starting with a multisite. This makes it easier to add instances later as your ministry grows.

To use multisite you'll need to first purchase the "Wordpress Multisite" Add-on from Billing > Purchase Add-ons (https://my.wpengine.com/modify_plan). 
It will cost ~$200 (one time expense).

You now have a WordPress instance at [instance_name].wpengine.com

## Setup Custom Domain 

Purchase custom domain (your-domain.com)

Set up DNS to access your instance from your-domain.com or subsite.your-domain.com
DNS instructions?

## Install Theme

Download the theme
https://github.com/DiscipleTools/disciple-tools-theme/releases/latest/download/disciple-tools-theme.zip - or link to the downloads page.

Log in to your new wordpress instance.

Install the theme (link to how to install themes) Single/Multisite

## Setup TLS (SSL)

After your custom domain is set up

### Single Site

Click SSL > Add Certificates > Get FREE certificate using the Let's Encrypt option

### Multisite

If you add each subdomain to the domains panel then it is the single site process. 

If you have many sub-domains and will be adding and removing them often:

- Buy the wildcard SSL cert from WPEngine - an annual $200 expense

### Restrict all traffic to use https. 

Under SSL, select the certificate and choose “Secure All URLs”. 

## Backups

Have a strategy for offsite backups. If WPEngine accidently deletes your account or it gets frozen (GDPR?) you want to have access to your data. See
https://disciple-tools.readthedocs.io/en/latest/Disciple_Tools_Theme/development/self_hosting.html#backups 


## Additional Configuration

### CRON

Enable system schedule processes:

-enable cron https://wpengine.com/support/wp-cron-wordpress-scheduling/ 

### Caching and Bots

-https://wpengine.com/support/redirecting-bots-how-this-benefits-you/ 

-We initially had to contact support to disable caching on GET api requests. This has not been an issue recently.

### Multisites

Install the multisite plugins:

Multisite Tools and helpful functions: https://github.com/DiscipleTools/disciple-tools-multisite

Show update notifications if your main site is not an instance of Disciple.Tools: https://github.com/DiscipleTools/disciple-tools-multisite-mu-plugin 


## Notes
WPEngine does have a publicly accessible error log (though you need to know the link to access it). Error logs have the potential to dump personal contact info.

WPEngine has a small storage limit per account, so don't store a lot of backups locally.
With a multisite the option “Secure all URLs” with HTTPS does not always work.

When you want to add another WPEngine instance, you can stay on the cheapest plan and under Billing > Add-ons add a site for $200
