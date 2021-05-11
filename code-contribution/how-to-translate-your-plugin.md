# How to translate your plugin

You finished coding your Disciple.Tools plugin and now you want to make it accessible to the whole community. Before uploading it, you can add translations in order to make the content understadable for every user.

There are a few different ways of translating your plugin. Here are a few.

## Using Poedit Software

1. Download Poedit: [link here](https://poedit.net/download/)
2. Open the software and select the ```Edit a translation``` option
3. Select the ```default.pot``` file in your plugin's ```/languages``` folder
4. Go to the ```Catalog``` menu and click on ```Update from Source Code```. You should see the strings used in your plugin's code.
5. Click the ```Create New Translation``` button at the bottom and select the language you want to translate into
6. Translate each string by clicking on them and add its respective translation in the ```Translation``` text area
7. After translating every string, save the file. Poedit will suggest a file name that is the language code you selected for your translation. Don't delete or modify that text. Write your plugin name before it making sure you only use lowercase and replace spaces with hyphens. (```eg. my-plugin-name-es_ES.po```)
8. Make sure your code echoes the translated strings with the following format:
```<?php echo esc_html__( 'Hello, World!', 'my-plugin-name' ); ?>```
9. Done! Your translation should appear for your plugin on the Disciple.Tools theme.



## Using Poedit & Poeditor Website for community translations

1. Register in www.poeditor.com and create a new project for your plugin
2. Add a new language
3. In Poedit, load the ```default.pot``` file in your plugin's ```/languages``` folder
4. Go to the ```Catalog``` menu and click on ```Update from Source Code```. You should see the strings used in your plugin's code.
5. Save the ```default.pot``` file with the imported strings
6. In poeditor.com, go to the translation project for your plugin and upload the ```default.pot``` file by clicking the ```Import``` button. Your plugin's terms should have been added automatically.
7. Translate all the terms and export the ```.po``` and ```.mo``` files from the project language menu. These files should be saved in your plugin's ```/languages``` folder. The file name should be your plugin's name in lowercase and with hyphens instead of spaces followed by the language code. (eg. ```my-plugin-name-es_ES.po```)
8. Make sure your code echoes the translated strings with the following format:
```<?php echo esc_html__( 'Hello, World!', 'my-plugin-name' ); ?>```
9. Done! Your translation should appear for your plugin on the Disciple.Tools theme.