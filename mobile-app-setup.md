# Mobile App Setup

[This YouTube playlist](https://www.youtube.com/playlist?list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE) shows how to set up a local development environment for the D.T. Mobile App and contains more information about the environment than this guide.

However, it uses Docker for the local Wordpress server and executes the mobile app setup slightly differently.  There are links in the steps below to pertinent sections in the video, although they are not necessarily in the same order.

Where the details differ please follow these instructions instead. 

## Download

1. Download the latest mobile app plugin zip file, and install the plugin, by following these instructions:

    https://wordpress.org/support/article/managing-plugins/#manual-upload-via-wordpress-admin

- https://github.com/DiscipleTools/disciple-tools-mobile-app-plugin/releases/latest/download/disciple-tools-mobile-app-plugin.zip

## Configure WP Site
Changes need to be made to the Wordpress configuration for the mobile app to connect to it.

If you are following the LocalWP Setup, then there are two choices: Local Live Link address, or change the D.T site’s domain to an address reachable from your mobile device.  This is the only choice if you are using Docker

### For Live Link:
  - Enable ngrok.io Live Link from the centre of the bottom line of the D.T’s Local Sites in the Local app.
  - “Enable” button’s text will change to “Copy”
  - Transfer address to mobile device – it will look like: http://0f0f0f0f0f0f.ngrok.io

**Or** change your Site Domain to your server’s IP address

> NOTE: With Docker, if your local Wordpress site has not been setup to use http (i.e. NOT https) then you will need to reinitialize it.

- Adding “—volumes” to docker-compose down will remove your previous configuration

```shell
docker-compose down  --volumes
 
docker-compose up -d
```

- Go to http://localhost:8000 and repeat the configuration steps from the appendix.

### Discover the IP address of your local server. 

There are multiple commands to do this, and your computer may have multiple network interfaces and it will depend if it uses a wired or wireless connection.  

- The address would likely be of the form “192.168.1.2” (as an example)
  - On Linux you can use `ifconfig`
  - On Windows you can use `ipconfig`

### LocalWP
If you are using **LocalWP**, in the D.T’s Local Sites in the **Local** app, change the Site Domain to your IP address

### Docker
If you are using Docker, login to wp-admin and go to  Settings > General and update the WordPress and Site Addresses to your servers IP address.  

e.g. if your address is “192.168.1.2” and no port number, then:

WordPress Address (URL)	     http://192.168.1.2  

Site Address (URL)		     http://192.168.1.2  

> NOTE: This shows the basic procedure: https://www.youtube.com/watch?v=1KJEOY5J3Sw&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=5&t=6m12s

## Setup D.T Mobile App

Clone the development or master branch of https://github.com/DiscipleTools/disciple-tools-mobile-app to the folder where you want the source code to be stored.

This video goes into much more detail:

https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=2m35

```shell
git clone https://github.com/DiscipleTools/disciple-tools-mobile-app.git
 
cd  ./disciple-tools-mobile-app/
 
git checkout development
```

### https workaround

Your local copy of DT does not have the correct https certificates so the mobile app will not be able to connect to it.  To work around this, use the http connection instead.

This is shown at:

https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=9m24s

> NOTE: The app code is able to connect to the official demo server if you have an account, but not after these changes.

For Windows: You will need execute these commands from a command prompt or terminal / shell.

From the disciple-tools-mobile-app folder:
```shell
cd store/sagas
 
grep -rl https: . | xargs sed -i "s/https:/http:/g"
```

> WARNING: Do not include these changes with any pull requests to the main repository!  They will be rejected.

## Install Expo

See https://expo.io/learn

Expo requires NPM to be installed.
Download and setup from https://nodejs.org/

Use NPM to install expo:

`npm install expo-cli -–global`

**Create an account** if you do not have one (You do not have to create a project)

Install the Expo client on your mobile device (iOS or Android app stores)

From within the *disciple-tools-mobile-app* cloned folder install project dependencies based on the package.json file

Shown at:

https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=5m53s

This may take a while

`npm install`

Launch the development environment.

`npm start`

Wait for the GUI to display a QR code and then on your mobile device:

This may take a while

From iOS take picture of QR code

From Android launch Expo app and take a picture of the QR code.

Wait for the DT android app to start and ask for you to connect to the server.

This may take a while.  The main Expo GUI will provide a status.

Log into the mobile app using the local DT Wordpress server ip address you set the 
server to previously.



> NOTE: The end of Part 5 as well as part 6 of the YouTube videos give additional information about using the mobile development environment:
https://www.youtube.com/watch?v=1KJEOY5J3Sw&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=5&t=8m6s

Part 7 shows you what is happening on the phone while this is happening:

https://www.youtube.com/watch?v=eM2zxplCaOE&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=7
