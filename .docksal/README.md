# Docksal powered Drupal 8 installation from Composer.

This is a sample Drupal 8 installation pre-configured for use with [Docksal](http://docksal.io/) - Docker based environments.

Features:

- Example Docksal http://docksal.io setup for D8
- Example D8 composer from https://github.com/drupal-composer/drupal-project (fork).
- Example Drupal 8 site ready for testing

## Setup instructions

### Prerequisites: Docksal (fin) for Mac, Windows 7 and 10.

Follow [Docksal environment setup instructions](https://github.com/docksal/docksal/blob/develop/docs/env-setup.md). This is a one time setup - skip this if you already have a working Docksal environment.

### D8 site install using Docksal fin 

1. Clone this repo into your Projects directory

    ```
    git clone https://github.com/dashav/drupal-project
    cd drupal-project
    ```

2. Initialize the site

    ```
    fin up
    fin init
    ```
	
    - `fin up` will initialize Docker based local environment 
    - `fin up` will run `composer install` and `drush site-install`
	
	When the automated install is complete the command line output will display the admin username and password.

3. **On Windows** add `192.168.64.100  drupalproject.docksal` to your hosts file

4. Point your browser to

    ```
    http://drupalproject.docksal
    ```

### Alternative initial setup instructions

As alternative, instead of cloning this repo you can do `composer create-project` into fresh git repo.

1. Start a new repo `git init`

	```
	git init
	```

2. Create a `.docksal/docksal.env` file (see [example](https://github.com/dashav/drupal-project/blob/8.x/.docksal/docksal.env) in this repo) && initialize Docker based local environment

	```
    fin up
	```

3. Create project from composer template for Drupal projects.

	```
    fin exec "composer create-project drupal-composer/drupal-project:8.x-dev tmp --stability dev --no-interaction"
    fin exec "mv tmp/* ."
    fin exec "cp -rT tmp/* ."
    fin exec "rm -rf tmp"
	```
	
	- Current issue: `composer create-project` needs an empty dir on the same level as `/var/www`. 
	- Temporary solution: run `create-project` into the `tmp` dir and copy it over to `/var/www` after.
	
4. Commit result to the `composer create-project` to your new repo.

	```
	git add .
	git commit -m "Initial commit from drupal composer project."
	```

5. (optional) Install Drupal either manually at `http://drupalproject.docksal` or via drush. At this point you have fully functional test site. 

5. (optional) Modify `web/sites/default/setting.php`, if needed.

7. Create `.docksal/init` (see [example](https://github.com/dashav/drupal-project/blob/8.x/.docksal/commands/init) in this repo) and run site install:

	```
	fin init
	```
