# Unit Tests

## Setup testing environment

In the theme root within your environment \(localWP: "Open site shell" option\) run:

```bash
./tests/install-wp-tests.sh <db-name> <db-user> <db-pass> [db-host]
```

* `<db-name>` is the name of the db you want the run the tests in. We suggest creating a separate db form your dev db for testing.
* `<db-user>` Database username
* `<db-pass>` Database password
* `[db-host]` Database url and port. For localWP get the port from the url when opening Adminer.

Note for localWP on linux the command looks like this for localWP:  
`./tests/install-wp-tests.sh local-test root root localhost:10063`

Notes:  
- On localWP, make sure you are running from the "Open site shell" menu option, so the environment is loaded
- On localWP, remove `--protocal=tcp` on line \#141 of ./tests/install-wp-tests.sh  
- On localWP, you can get the database port from the browser url after opening adminer
- You may need to install svn: `sudo apt install subversion`
- If you get an error that looks like: `Could not find /{path}/wordpress-tests-lib /includes/functions.php, have you run tests/install-wp-tests.sh ?` delete the temp folder and run the install again.

## Running the tests

Run `phpunit` form the theme root.

The tests need phpunit v7. v8 and above currently don't work. You can install phpunit with:

```bash
composer global require "phpunit/phpunit=7.5.*"
```

## Writing tests

* tests are located in the theme ./tests folder
* unit test files need to start with 'unit-test'
* unit test function need to start with 'test\_'
* phpunit documentation [https://phpunit.readthedocs.io/en/7.5](https://phpunit.readthedocs.io/en/7.5)
* assertions: [https://phpunit.readthedocs.io/en/7.5/assertions.html](https://phpunit.readthedocs.io/en/7.5/assertions.html)

