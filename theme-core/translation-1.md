# Translation

### Overview

Disciple.Tools is built on WordPress and uses the WordPress translation strategy. Extensive resources can be found on [WordPress.org](https://wordpress.org/) giving explanations and help for translators. [WordPress Translation Resources](https://make.wordpress.org/polyglots/handbook/tools/glotpress-translate-wordpress-org/)

We invite you to [contribute a new translation](https://poeditor.com/join/project/KcPvw3oaKD) to Disciple.Tools, and it does not require writing code! You can submit completed translations through Github or through email, and our commit team will review it and add it to the project.

### Current Available Translations

Disciple.Tools is currently available in the following languages, for both the WordPress theme and the mobile app.

* English
* Arabic
* French
* Spanish
* Turkish
* Russian
* Dutch
* Portuguese
* Chinese \(simplified\)
* Chinese \(tranditional\)
* Persian
* Swahili

Note

As Disciple.Tools develops, additional translation commits will be needed.

### How to contribute

We are using an online tool called [POEditor](https://poeditor.com/). No downloading, changing, or uploading of files necessary. No coding skills needed either.

To get started visit the main [Disciple.Tools WordPress theme translation project](https://poeditor.com/join/project/KcPvw3oaKD) and the much smaller [D.T app translation project](https://poeditor.com/join/project/dQzfAs5uNc).

Either select an existing language from the displayed list or click **“Click here to suggest a new language”** link to add the language you want Disciple.Tools to be translated in to. Enter your email and name and then click “Join this project”

We will receive your request and approve your account as soon as possible. Once approved, you will be free to start translating.

Your translations will become available to everyone when we push a release for the theme

### POEditor: How to do a translation

1. Log in to [https://poeditor.com/login/](https://poeditor.com/login/) and find the translation you have access to. You will arrive at a page like the following:

![POEditor projects](https://disciple-tools.readthedocs.io/en/latest/_images/poeditor-projects.png)

1. Click on the **flag** the represents the language you want to translate.
2. You will arrive at a screen that looks like the following:

![POEditor translations](https://disciple-tools.readthedocs.io/en/latest/_images/poeditor-translations.png)

In the _“big empty box”_, type in the translation of _“the string”_ \(a word or phrase\) that is displayed on the left side.

**For example**: The first string is `Location Grid Meta`. Type your translation of that phrase into the “big empty box” to the right. Once you are happy with what you have typed, click out side of the box, and the translation will be saved automatically. If you need to change it, simply click on the _string_, and the box will become editable again.

On the far right side of each row, there are a few icons that can be used to sort the list.

The `A` icon means “automatic translation” when highlighted will be set to orange in colour and means that the _string_ was automatically translated. When you make a change to the string, the `A` will be unset. When you review a string that was marked as translated automatically, please untick the orange `A` icon to indicate that the string is correct.

The `Comments` icon \(represented by the speech bubbles icon\) indicates if a comment has been written by any translators relating to this _string_. If you have a question or comment to make about the string, click the `Comments` icon and write your comment \(or question\) in the popup window. Your comment will be sent to the main editor for the language project who will reply ASAP, if needed.

The `F` icon means “Fuzzy” which you can toggle to indicate that you aren’t sure if this _string_ has been translated correctly. You can later review or have others easily find the strings that need revision.

### What are those wonky characters?

In POEditor, you will see some strings that look like this:

`Sorry, you don't have permission to view the %1$s with id %2$s.`

What do I do with the `%1$s` and `%2$s` and what do they mean?

These are placeholders that will be replaced with a something else.

Here this sentence in English could be :

* Sorry, you don’t have permission to view the contact with id 4344.
* Sorry, you don’t have permission to view the group with id 493.

In this case, `%1$s` corresponds to “contact” or “group”. `%2$s` corresponds to the id of the record

This message can be displayed for a contact or a group. And we don’t know before hand the ID of the record. This lets you, the translator, make a sentence that is gramatically correct while still using placeholders.

To translate the sentence, just copy and paster the characters \( %s, %1$s, %2$s \) to into your translation.

In french this sentence would give:

`Désolé, vous n'avez pas l'autorisation d'afficher le %1$s avec l'id %2$s.`

