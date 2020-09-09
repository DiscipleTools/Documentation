# D.T on Docker Setup

This is based on https://github.com/cairocoder01/dt-docker which is an earlier version of the setup instructions.

## Docker
[Docker](https://www.docker.com/) is a container system that can be used to set up all of the infrastructure needed to run a web site. The below will setup containers locally needed to run:

- MySQL 5.7 database
- Apache + PHP 7.2 web server

All of this will be running on a Linux virtual machine in order to duplicate as close as possible the production hosting environment.

### Install Docker

https://docs.docker.com/get-docker/

In Windows:

When you start the Docker Desktop, if necessary it will provide you with additional instructions to update WSL 2 (Windows Subsystem for Linux)

If the user account you commonly use does not have admin privileges, it will be added to the docker-users group so you can run docker directly without requiring “runas”.

### SSL

Set up the self-signed SSL certificate. (The instructions are explained [here](https://medium.com/@nh3500/how-to-create-self-assigned-ssl-for-local-docker-based-lamp-dev-environment-on-macos-sierra-ab606a27ba8a) in detail)

For Windows:

- The instructions above for MacOs work if you have Openssl installed
- Openssl is available via Git Bash, Ubuntu for Windows, Cygwin, or Chocolatey

> Note: the dev.conf  and dockerfile configuration files are already updated

From command line in the project root directory (your copy of the Github repository) run:

```shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout server.key -out server.crt
```

Specify the Common Name as 'local.disciple.tools'. You may answer the other questions however you wish.

Site will be available on https://local.disciple.tools (if you add the needed hosts file mapping) or https://localhost:44300

> NOTE: Make sure the dockerfile has up to date version numbers for Wordpress and PHP.

For example the first line will look like:
`FROM wordpress:5.4-php7.4-apache`

It is possible this repository has not been updated yet. Check https://github.com/DiscipleTools/disciple-tools-theme/releases/latest for which version of Wordpress disciple-tools-theme has been tested with.

Run `docker-compose up -d` from the project root directory (or `npm run docker-start`).

The first time this is run, it will need to download all of the machine images, so it may take a little while.

There will be some warning messages that can be ignored, unless Docker cannot bring the Wordpress and Mysql containers up.

You should be able to access the site via https://local.disciple.tools (if you add the needed hosts file mapping), https://localhost:44300 or http://localhost:8000

For Windows: You will need to add a “security exception” in your browser from its warning dialog (depending on browser).

>NOTE: When you configure WordPress from “https://localhost:44300” or “http://localhost:8000” you will have to continue to use that address or reconfigure it from the …/wp-admin/options-general.php settings page to switch.

Step through the WordPress installation process.

- Language:
- Site Title:
- Username:
- Password:
- Your Email:
- Press “Install WordPress”

> NOTE: If you cannot access DT’s home page: https://localhost:44300/contacts
or other pages try this:
> - Login to wp-admin and go to  Settings > Permalinks. You don’t need to change anything, just click save at the bottom.
> 
> (From https://disciple-tools.readthedocs.io section: Errors on New Installation)

### Install Theme

https://github.com/DiscipleTools/disciple-tools-theme

Follow installation instructions: https://github.com/DiscipleTools/disciple-tools-theme#how-to-install

Download latest release: https://github.com/DiscipleTools/disciple-tools-theme/releases/latest/download/disciple-tools-theme.zip

Download the latest plugin zip files from below, and install plugins using these instructions: https://wordpress.org/support/article/managing-plugins/#manual-upload-via-wordpress-admin

https://github.com/DiscipleTools/disciple-tools-demo-content

https://github.com/WP-API/Basic-Auth

Download JWT Authentication for WP REST API from: https://wordpress.org/plugins/jwt-authentication-for-wp-rest-api/

Follow directions on plugin page to add auth header config to .htaccess

Follow directions on plugin page to add 2 values to wp-config.php

#### Enable debugging

Edit wp-config.php to add the following values: 

```php
define( 'WP_DEBUG', true ); // Enable WP_DEBUG mode
define( 'WP_DEBUG_LOG', true ); // Enable Debug logging to the /wp-content/debug.log file
```

## Docker Multi-site Setup

See https://www.wpbeginner.com/glossary/multisite/

1. Add the following to `wp-config.php`

```php
/* Multisite */
define('WP_ALLOW_MULTISITE', true);
```

2. Go to Tools -> Network Setup and follow on-screen directions, adding the necessary code to .htaccess and wp-config.php

3. After changes, login again and return to wp-admin.

4. A new My Sites item appears in the top menu. Go to My Sites -> Network Admin -> Dashboard
   1. Copy `disciple-tools-multisite.php` into `wp-content/plugins/disciple-tools-multisite`

5. Add all of the sites as you desire. 

   - For each site you add, add the needed entry to your local hosts file
   - example:

```ini
127.0.0.1   site1.local.disciple.tools
```

## Making Docker D.T. Accessible from Mobile

Changes need to be made to the Docker Wordpress configuration for the mobile app to connect to it.

> NOTE: With Docker, if your local Wordpress site has not been setup to use http (i.e. NOT https) then you will need to reinitialize it.  

- Adding “—volumes” to docker-compose down  will remove your previous configuration

```shell
docker-compose down  --volumes
 
docker-compose up -d
```

Go to http://localhost:8000 and repeat the configuration steps above.

### Discover the IP address of your local server. 

There are multiple commands to do this, and your computer may have multiple network interfaces and it will depend if it uses a wired or wireless connection.  
- The address would likely be of the form “192.168.1.2” (as an example)
- On Linux you can use ifconfig
- On Windows you can use ipconfig

### Update Settings
- Login to wp-admin and go to  Settings > General and update the WordPress and Site Addresses to your servers IP address.  
- e.g. if your address is “192.168.1.2” and no port number, then:

```ini
WordPress Address (URL)	     http://192.168.1.2  
Site Address (URL)		     http://192.168.1.2  
```

> NOTE: This shows the basic procedure: https://www.youtube.com/watch?v=1KJEOY5J3Sw&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=5&t=6m12s

