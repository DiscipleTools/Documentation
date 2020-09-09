# Mobile App Setup

[playlist]: https://www.youtube.com/playlist?list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE

This [YouTube playlist][playlist] shows how to set up a local development environment for the D.T. Mobile App and contains more information about the environment than this guide.

However, the [playlist] use Docker for the local Wordpress server and executes the mobile app setup slightly differently.  There are links in the steps below to pertinent sections in the video, although they are not necessarily in the same order.

Where the details differ please follow these instructions instead.
- [Mobile App Setup](#mobile-app-setup)
  - [1. Download](#1-download)
  - [2. Configure WP Site](#2-configure-wp-site)
    - [Use Live Link](#use-live-link)
    - [**OR** change your Site Domain to your server’s IP address](#or-change-your-site-domain-to-your-servers-ip-address)
  - [3. Setup Source Code](#3-setup-source-code)
    - [Https workaround](#https-workaround)
    - [Install Expo](#install-expo)
    - [Install Dependencies](#install-dependencies)
  - [4. Run the development environment](#4-run-the-development-environment)
  

## 1. Download

Download the latest mobile app plugin zip file, and install the plugin, by following these instructions: <https://wordpress.org/support/article/managing-plugins/#manual-upload-via-wordpress-admin>

- <https://github.com/DiscipleTools/disciple-tools-mobile-app-plugin/releases/latest/download/disciple-tools-mobile-app-plugin.zip>

## 2. Configure WP Site

Changes need to be made to the *Wordpress* configuration for the mobile app to connect to it.

If you are following the *LocalWP* Setup, then there are two choices: Local Live Link address, *or* change the D.T site’s domain to an address reachable from your mobile device.  The latter is the only choice if you are using *Docker*

### Use Live Link

1. **Enable** ngrok.io Live Link from the centre of the bottom line of the D.T’s Local Sites in the Local app.
1. “**Enable**” button’s text will change to “**Copy**”
1. Transfer address to mobile device – it will look like: `http://0f0f0f0f0f0f.ngrok.io`

### **OR** change your Site Domain to your server’s IP address

1. **NOTE: With Docker, if your local Wordpress site has not been setup to use http (i.e. NOT https) then you will need to reinitialize it.**

    >- Adding “—volumes” to docker-compose down will remove your previous configuration
    >
    >   ```shell
    >   > docker-compose down  --volumes
    >   > docker-compose up -d
    >   ```
    >
    >- Go to <http://localhost:8000> and repeat the configuration steps from **``XXXXXX``**

1. Discover the IP address of your local server

   There are multiple commands to do this, and your computer may have multiple network interfaces and it will depend if it uses a wired or wireless connection.  

   - The address would likely be of the form “192.168.1.2” (as an example)
     - On Linux you can use:   *i**f**config*
     - On Windows you can use: *i**p**config*

1. **If** you are using **LocalWP**,
   - In the D.T’s Local Sites in the **Local** app, change the Site Domain to your IP address

   **If** you are using **Docker**,
   - login to wp-admin and go to  Settings > General and update the WordPress and Site Addresses to your servers IP address.  
   - As examples, if your address is `192.168.1.2` and no port number, then:
      - WordPress Address (URL):   `http://192.168.1.2`  
      - Site Address (URL):        `http://192.168.1.2`

    > NOTE: This [YouTube video](https://www.youtube.com/watch?v=1KJEOY5J3Sw&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=5&t=6m12s) shows the basic procedure.

## 3. Setup Source Code

Clone the development or master branch of <https://github.com/DiscipleTools/disciple-tools-mobile-app> to the folder where you want the source code to be stored.

This [YouTube video](https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=2m35) goes into much more detail.

```shell
> git clone https://github.com/DiscipleTools/disciple-tools-mobile-app.git
> cd ./disciple-tools-mobile-app/
> git checkout development
```

### Https workaround

Your local copy of DT does not have the correct https certificates so the mobile app will not be able to connect to it.  To work around this, use the http connection instead.

This is shown in this [YouTube video](https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=9m24s).

> **NOTE:** The app code is able to connect to the official demo server if you have an account, but will no longer be able to after these changes.

> **For Windows:** These are Linux commands. You will need execute these commands from the **git bash shell**, or another **Linux** shell

From the disciple-tools-mobile-app folder:

```shell
> cd store/sagas
> grep -rl https: . | xargs sed -i "s/https:/http:/g"
```

> **WARNING:** **Do not include these changes with any pull requests** to the main repository!  They will be rejected.

### Install Expo

See <https://expo.io/learn>

1. Expo requires NPM to be installed.  
   Download and setup from <https://nodejs.org/>

1. Use NPM to install expo:

```shell
   > npm install expo-cli -–global
```

3. *Create an account* if you do not have one (You do not have to create a project)

1. Install the Expo client on your mobile device (iOS or Android app stores)

### Install Dependencies

From within the *disciple-tools-mobile-app* cloned folder install project dependencies based on the package.json file

This is shown in this [YouTube video](https://www.youtube.com/watch?v=gdeJHI19F7A&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=4&t=5m53s)

Use the NPM install command:

   ```shell
   > npm install
   ```

This may take a while

## 4. Run the development environment
Use the NPM start command:
   ```shell
    > npm start
   ```

1. Wait for the GUI to display a QR code and then on your mobile device:

   - Again, this may take a while

   - **From iOS:** take picture of QR code

   - **From Android:** launch Expo app and take a picture of the QR code.

2. Wait for the DT android app to start and ask for you to connect to the server.

   - This may a while as well, but the main Expo GUI will provide a status, as will the terminal you started it on.

   - Log into the mobile app using the local DT Wordpress server ip address you set the server to previously **``XXXXXX``**.

> **NOTE:** The end of Part 5 as well as part 6 of the [YouTube videos](https://www.youtube.com/watch?v=1KJEOY5J3Sw&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=5&t=8m6s) give additional information about using the mobile development environment:
>
> [Part 7](https://www.youtube.com/watch?v=eM2zxplCaOE&list=PLNZnizaetELN6_2k3_iRxBhJuyavhqawE&index=7) shows you what is happening on the phone while this is happening:
