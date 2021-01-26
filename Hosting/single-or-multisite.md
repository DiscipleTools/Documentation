# <a name="sigle-multisite"></a>Single Site or MultiSite

## A Wordpress Tool

In setting up Wordpress on a new server we have two options. The default way as single site, or as a multisite.

### Single site

This is the default when you install Wordpress on your server and set it up on your domain or subdomain.
Your site will be available at example.com or site.example.com.

### Multisite

During install (preferred) or after Wordpress is installed you can configure Wordpress as a Multisite.
This lets you set up multiple sites on ones server.

- example.com
- site1.example.com
- site2.example.com
- site3.example.com

## What does this mean for Disciple.Tools?

A single site will give you an instance where you and your users can collaborate on contacts, groups, and more. All your contacts will be in one place and are managed by the Admin and Dispatchers.

This is a great starting point if you are a small team working in together over one region. But suppose you have a team in New York with a Facebook Ministry and a team in Chicago with a cool Website and another team in a different location doing campus ministry.  
It soon become overwhelming to have all the contacts one spot. This is why you might want to separate the teams out into different instances using Wordpress as a multisite.

The Serve could be set up like this:

- ministry.com - a D.T instance, or a front facing webpage
- new-york.ministry.com - instance for the New York team
- chicago.ministry.com - instance for the Chicago team
- etc

You may choose to have a different instance for each location you are in. You can also separate based on teams, language, media page, etc.

Note: We'd love to support team functionality inside one instance. Follow us at <https://disciple.tools/news/>

## Global Metrics - Network Dashboard

If you have gone with the multisite route, you still would like to see what is happening in one place. We've built the Network Dashboard to collect data form many instances and **show metrics in one place**.  
You can set it up to collect data from all the multisite instances on your server and you can connect it to other instances on others servers as well.

Find out more about the Network Dashboard here <https://disciple.tools/plugins/network-dashboard/>

## Site Links - Collaborate Between Instances

D.T allows users to send contacts between instances. This can be the different instances on your multisite, or with other D.T servers.

A **Site Link** is needed to collaborate between instances. Here are instructions on how to set them up: <https://disciple.tools/user-docs/getting-started-info/admin/site-links/>

## Managing a Multisite

### Setup

If you are hosting your own instance check out the Wordpress documentation for enabling multisite [here](https://wordpress.org/support/article/create-a-network/).

If you are using a hosting service like WPEngine google "WPEngine multisite" or contact your hosting support. They will help you get it set up. Sometimes hosting services charge extra for multisites.

### Maintenance - D.T Multisite Plugin

Once your multisite is set up, you can install the Disciple.Tools multisite plugin: <https://disciple.tools/plugins/multisite/>.

It offers growing support for updating and managing all your instances at one time.
