# Evozon Magento 2 Setup with Docker Compose
Evozon Magento 2 Setup with Docker Compose

This file represent a Magento CE 2 setup with Docker Compose. The role of this project is to provide a quick development setup for Magento 2 with or without sample data.

We used Mage Inferno approach in https://github.com/mageinferno/docker-magento2-php and defined our images. Some files in this project are keep the same as are used by Mage Inferno.

The main reason why we didn't used the Mage Inferno docker images for magento 2 is because we want some level of control when we build the images on local and make a quick Magento 2 application that will need minimal configuration. The minimal configuration required is the username and password keys for repo.magento.com.





docker-compose up -d --build app

docker-compose run setup

alias

alias magento-cli='docker-compose exec phpfpm magento'
alias composer='docker-compose exec -u www-data phpfpm composer'


#Setup (will soon be changed)
1) rename `docker-composer.ovveride.yml.dist` to `docker-composer.ovveride.yml`
2) add mysql and magento2 config parameters in the `env` folder
3) run `docker-compose run --rm setup` to start the setup
4) add your private and public keys when prompted for user and password
5) copy the magento2 files using the command `docker cp magento2docker_app_1:/var/www/html ./`
6) change the permissions `chmod -R 777 html`
7) start the app service `docker-compose up -d app`