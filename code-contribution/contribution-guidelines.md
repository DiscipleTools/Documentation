# Contribution Guidelines

Thank you for joining us in contributing to Disciple.Tools! These are the guidelines we expect you to follow in writing code that will be used in or with D.T

## Translations

D.T is already being used in multiple languages. Please help us make D.T translable by taking full advantage of Wordpress’ translatable strings. Any string that will be read by the user must be marked as translatable. Ex: `<label class="section-header"><?php esc_html_e( 'Other', 'disciple_tools' )?></label>`

Make sure you look for these in PHP, HTML and JavaScript code.

## PHPCS

We use [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer) and [PHPCS WordPress Coding Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards) to test for syntax errors, security vulnerabilities and some styling rules. We expect your commits to pass these tests.

Run `composer install` or `composer update` first.

In the theme you can run `./tests/test_phpcs.sh` or create a pull request to our repo and Travis CI will run the tests for you.

If you are working on a plugin based off our starter plugin run `./includes/admin/test/test_phpcs.sh`

Note: rules for PHPCS are located in the `phpcs.xml` file. We sometimes update the rule list as PHPCS updates. We’ll update the [starter plugin](https://github.com/DiscipleTools/disciple-tools-starter-plugin) `phpcs.xml`, you might want to look there to get the latest version.

Run phpcbf to auto-fix some phpcs issues:
`vendor/bin/phpcbf --standard="phpcs.xml" dt-core/`

## Missing WP functions errors

If all of the WP functions are showing up as errors saying that the function is undefined, you can try adding the entire WP site to your editor, so that it can automatically pick up the WP function definitions from `wp-include`, `wp-admin` etc.

## PHPCS sniff errors

If you get errors such as, `phpcs Referenced sniff "WordPress" does not exist` this could be due to your editor not using the correct `phpcs` or `phpcs.xml` file. It could be using a globally installed version instead.

Make sure that you point your editor to the local phpcs file in `vendor/bin/phpcs` and phpcs config file `phpcs.xml` in the `disciple-tools-theme` directory.

In vscode the settings look roughly like this, depending on your setup and where the settings are being kept. In this example a directory specific settings.json file is being used in the root of the website. The paths, may need to be the full absolute paths or relative paths to where the settings file is.

```
    "phpcs.executablePath": "wp-content/themes/disciple-tools-theme/vendor/bin/phpcs",
    "phpcs.standard": "wp-content/themes/disciple-tools-theme/phpcs.xml"
```

## GitHub and Commits

For new plugins copy our [starter plugin](https://github.com/DiscipleTools/disciple-tools-starter-plugin).

To commit to the theme or an existing plugin start by creating a fork of the repository. When you are ready, create a pull request into our repo.

Note: Depending on your context you may wish to use an anonymous GitHub account.

## `WP_DEBUG`

Enable `WP_DEBUG` in your `wp-config.php`: `define('WP_DEBUG', true);` Checking out a PR and seeing the orange debug table is disappointing.

We look forward to hearing from you!

