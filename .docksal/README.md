# Docksal powered Drupal 8 installation from Composer.

This is a sample Drupal 8 installation pre-configured for use with [Docksal](http://docksal.io/) - Docker based environments.

Features:

- Example [Docksal](http://docksal.io/) setup for D8
- Example D8 composer from https://github.com/drupal-composer/drupal-project (fork).
- Example Drupal 8 site ready for testing

## Setup instructions

### Prerequisites: Docksal (fin) for Mac, Windows 7 and 10.

**This is a one time setup - skip this if you already have a working Docksal environment.**  

Follow [Docksal environment setup instructions](https://github.com/docksal/docksal/blob/develop/docs/env-setup.md)

### D8 site install using Docksal fin 

1. Clone this repo into your Projects directory

    ```
    git clone https://github.com/docksal/drupal-project
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


