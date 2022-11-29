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



## How to translate strings in JS files

1. Open ```dt-assets/functions/enqueue_scripts.php```.
2. Search for the if statement that looks for the PHP file that calls your JS script. If it doesn't appear in ```enqueue_scripts.php```, you will have to create an if statement that looks for it. Live examples of these if statements already exist in this file. You can use them as a reference.
3. Inside the if statement, make sure that your JS script is added with ```dt_theme_enqueue_script()```. We're going to need the handle parameter for the next step (the first parameter in the ```dt_theme_enqueue_script()``` function).
### Example:
```
dt_theme_enqueue_script('my_js_script', 'path/to/script/my-js-script.js' );
```
4. Create a ```$translations``` array that contains the keys and values for what you want the string to show. 
### Example:
```
$translations = [
		'hello_world' => __( 'Hello, World!', 'disciple_tools' ),
		'hello_user', => _x( 'Hello, %s!', 'disciple_tools' ),
		];
```
5. If it's not already there, add a ```wp_localize_script()``` function to localize your script. Script localization passes values obtained through PHP to your JS script.
6. The ```wp_localize_script()``` should have the handle from step 3 passed as the first parameter. The second parameter should be ```new_record_localized``` and the third parameter should be the information you want to localize. See example below.
```
wp_localize_script( 'my_js_script', 'new_record_localized', array(
            'translations'  =>  $translations,
        ) );
```
7. Now we move to the JS file, find the place that contains the string you wish to translate and replace it with the translated string. Translated strings are inside the ```window.new_record_localized.translations``` object.
### Example:
```
function say_hello_world() {
    return window.new_record_localized.translations['hello_world'];
    // This returns 'Hello, World!'
}

function say_hello_to_user(username) {
    return window.new_record_localized.translations['hello_user'].replace('%s', username);
    // username = 'Bob', this returns: 'Hello, Bob!'
}
```
