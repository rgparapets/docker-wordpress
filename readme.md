# Docker WordPress Environment

This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/), [phpMyAdmin](https://www.phpmyadmin.net/) and [Xdebug](https://xdebug.org/).

## Table of Contents

- [Introduction](#docker-wordpress-environment)
  - [Services](#services)
- [Requirements](#requirements)
- [Usage](#usage)
  - [Variables](#variables)
- [Contributing and Support](#contributing-and-support)

---

> **Disclaimer:** This project is meant to be used for development purposes only. It's **not** meant to be used in production.

---

### Services

Docker services used on [docker-compose. yml](https://github.com/sarahcssiqueira/docker-wordpress/blob/master/docker/docker-compose.yml):

- **db**

The MYSQL official image.

- **phpMyAdmin**

Intended to handle the administration of MySQL, in this case through port 80, on browser [localhost:8080/](localhost:8080/).

- **WordPress**

Uses the official WordPress latest docker image.

- **WP-CLI**

The **wpcli container** was added to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`

## Requirements

- [Docker](https://www.docker.com/) hub installed.

## Usage

Clone this repository `git clone https://github.com/sarahcssiqueira/docker-wordpress`
then cd the **docker folder** `cd docker` and set up your chosen variables on the .env file.

### Variables

The variables used for WordPress installation are the following ones, you can use the same or change them, it's up to you.

```
MYSQL_DATABASE_NAME=exampledatabase
MYSQL_USER=exampleuser
MYSQL_PASSWORD=examplepass
WORDPRESS_PORT=8000
```

---

> WARNING: DO NOT store your variables on a .env file if it's not a local development environment, for other cases, the appropriate method is to add the .env file to a .gitignore and store the variables as [encrypted secrets.](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

---

After setting your variables, run `docker-compose up -d` to start the docker.

When docker finished their work (which can take a few minutes the first time, depending on your connection and machine) by opening your browser through http://localhost:8000, you should see the WordPress default installation screen.

Finish WordPress installation and in your terminal, cd the root project folder again type `cd ..` to start working on your plugins and/or themes.

For using wp-cli, use `docker-compose run --rm wpcli command` as it was added to only run one-off commands

The wp-core is synchronized too, just in case you need to check and/or debug something.

# Contributing and Support

It's **work in progress.** Feel free to contribute informing about [issues](https://github.com/sarahcssiqueira/docker-wordpress/issues) or even through [pull requests](https://github.com/sarahcssiqueira/docker-wordpress/pulls) for improvements.

# Docker WordPress Environment

This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/), [phpMyAdmin](https://www.phpmyadmin.net/) and [Xdebug](https://xdebug.org/).

## Table of Contents

- [Introduction](#docker-wordpress-environment)
  - [Services](#services)
- [Requirements](#requirements)
- [Usage](#usage)
  - [Variables](#variables)
  - [WordPress Debug](#debug)
  - [Xdebug for VSCode](#xdebug)
- [Contributing and Support](#contributing-and-support)

---

> **Disclaimer:** This project is meant to be used for development purposes only. It's **not** meant to be used in production.

---

### Services

Docker services used on [docker-compose. yml](https://github.com/sarahcssiqueira/docker-wordpress/blob/master/docker/docker-compose.yml):

- **db**

The MYSQL official image.

- **phpMyAdmin**

Intended to handle the administration of MySQL, in this case through port 80, on browser [localhost:8080/](localhost:8080/).

- **WordPress**

Uses the official WordPress latest docker image.

- **WP-CLI**

The **wpcli container** was added to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`

## Requirements

- [Docker](https://www.docker.com/) hub
- [Xdebug](https://xdebug.org/docs/install)
- [PHP Debug Extension](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)

## Usage

Clone this repository `git clone https://github.com/sarahcssiqueira/docker-wordpress`
then cd the **docker folder** `cd docker` and set up your chosen variables on the .env file.

### Variables

The variables used for WordPress installation are the following ones, you can use the same or change them, it's up to you.

```
MYSQL_DATABASE_NAME=exampledatabase
MYSQL_USER=exampleuser
MYSQL_PASSWORD=examplepass
WORDPRESS_PORT=8000
```

---

> WARNING: DO NOT store your variables on a .env file if it's not a local development environment, for other cases, the appropriate method is to add the .env file to a .gitignore and store the variables as [encrypted secrets.](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

---

After setting your variables, run `docker-compose up -d` to start the docker.

When docker finished their work (which can take a few minutes the first time, depending on your connection and machine) by opening your browser through http://localhost:8000, you should see the WordPress default installation screen.

Finish WordPress installation and in your terminal, cd the root project folder again type `cd ..` to start working on your plugins and/or themes.

For using wp-cli, use `docker-compose run --rm wpcli command` as it was added to only run one-off commands

## Debugging in WordPress

The wp-core is synchronized through the docker-composer.yml just in case you need to check and/or debug something. After running `docker-compose up -d`, you will be able to change the [WordPress debug mode](https://wordpress.org/documentation/article/debugging-in-wordpress/) by changing the following lines on the wp-config.php file.

By default, the wp-config.php generated by Docker will look something like this:

```
define( 'WP_DEBUG', !!getenv_docker('WORDPRESS_DEBUG', '') );
```

Replace it with the following:

```
define( 'WP_DEBUG', true);

define( 'WP_DEBUG_LOG' , true );

define ( 'WP_DEBUG_DISPLAY', true );
```

More info about **debugging in WordPress** you can find [here](https://wordpress.org/documentation/article/debugging-in-wordpress/).

## Xdebug for VSCode

Xdebug is enabled and configured to work on VSCode using the extension PHP Debug.

### Remote Host Debugging

```
"pathMappings": {
  "/var/www/html": "${workspaceFolder}",
}
```

# Contributing and Support

It's **work in progress.** Feel free to contribute informing about [issues](https://github.com/sarahcssiqueira/docker-wordpress/issues) or even through [pull requests](https://github.com/sarahcssiqueira/docker-wordpress/pulls) for improvements.
