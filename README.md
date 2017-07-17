# magento2-docker
Magento 2 Docker


#Setup (will soon be changed)
1) rename `docker-composer.ovveride.yml.dist` to `docker-composer.ovveride.yml`
2) add mysql and magento2 config parameters in the `env` folder
3) run `docker-compose run --rm setup` to start the setup
4) add your private and public keys when prompted for user and password
5) copy the magento2 files using the command `docker cp magento2docker_app_1:/var/www/html ./`
6) change the permissions `chmod -R 777 html`
7) start the app service `docker-compose up -d app`