# Evozon Magento 2 Setup with Docker Compose

## Introduction

The role of this project is to provide a quick development setup for Magento 2 with or without sample data using Docker Compose.

We used Mage Inferno approach from https://github.com/mageinferno/docker-magento2-php and defined our solution. Some files in this project are kept the same as the ones that are used by Mage Inferno.

The main reason we didn't used the Mage Inferno docker images, it's because we want some level of control when we build the images and have a quick Magento 2 installation that will need minimal configuration.

The minimal configuration required is the username and password keys from repo.magento.com.

**PLEASE DO NOT USE THIS ON PRODUCTION!!!**

## Development environment

The application will use the next configuration:
* Nginx 1.11
* Php FPM 7.0.*
* Percona with Mysql 5.7 (On Windows OS if you use Docker for Windows (NOT Docker Toolbox) you need to change the percona version to percona:5.6.35 in docker-compose.yml file - kown issues - https://github.com/docker-library/percona/issues/42)
* last version of Composer
* Magento CE 2.1.7 (the last stable version in July 2017)

The default Magento configuration use by this project has:
* Database name set to __magento__
* Database username set to __magento__
* Database password set to __magento__
* Base url set to http://magento.dev/
* Admin username set to __admin__
* Admin password set to __Admin123admin__

The Magento 2 files will be installed on directory __html__.

## Requirements

This project requires the Docker and Docker Compose installed on the machine. Please follow the Docker installation steps from https://docs.docker.com/engine/installation/ and docker compose installation steps from https://docs.docker.com/compose/install/.

## Installation

Please follow the next steps:
1. Download or clone this project in the directory you want to have the Magento 2 installed.
2. Open the file `auth.json` from directory .composer and add your [repo.magento.com](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html) credentials

            "username": "YOUR_USERNAME_USED_ON_REPO_MAGENTO",
            "password": "YOUR_PASSWORD_USED_ON_REPO_MAGENTO"

3. Open a terminal that allows you to run Docker Compose CLI application.
4. Change directory in terminal to the directory where the step 1 was performed.
5. Build the docker images with next command:

`docker-compose up -d --build app`

6. Download and install Magento CE 2 with next command

`docker-compose run setup`

7. Add the next text in hosts file of your OS system:

`127.0.0.1 magento.dev`

8. Open the browser and type the next link: http://magento.dev/


## How to use composer application

In order to run composer commands you need to be in the directory of the project(where this docker compose file is used) and type this:

`docker-compose exec -u www-data phpfpm composer [composer CLI options]`

Example of composer update command:

`docker-compose exec -u www-data phpfpm composer update`

## How to use Magento 2 CLI

The next command can be used in the directory of the project (where this docker compose file is used):

`docker-compose exec phpfpm magento [magento CLI options]`


## Suggestions
Try using CLI aliases for the composer and magento.

Example for linux Mint:

 1. Open the __.bashrc__ file
 2. Add the next text at the end of the file:

`alias magento-cli='docker-compose exec phpfpm magento'`

`alias composer='docker-compose exec -u www-data phpfpm composer'`

 3. Restart or open again the terminal window.
 4. Change directory to project location.
 5. Run `composer` or `magento-cli` commands.
 
