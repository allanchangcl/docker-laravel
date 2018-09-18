# install docker, docker-compose for Linux platform
```
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"

sudo apt-get update

sudo apt-get install docker-ce

sudo systemctl enable docker 

sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo usermod -a -G docker $USER 
```
Note: 
Need to reboot to be added into docker group, if not, permission error when running docker commands.
Docker service already running after install

# test docker installation
```
docker-compose -v
docker -v
```


# download laravel, /home/$USER/webdev/docker
curl -L https://github.com/laravel/laravel/archive/v5.7.0.tar.gz | tar xz

# Supporting files
You will need:
docker-compose.yml
app.dockerfile
web.dockerfile
vhost.conf

# composer install 
cd into the folder where you untar laravel, then run composer install
```
docker run --rm -v $(pwd):/app composer install
```
Note: will download all the required files

# env
Rename .env.example to .env
```
docker-compose exec app php artisan key:generate
```

# updata permissions
```
// get container is
docker ps

// execute container shell
docker exec -it <CONTAINERID> bash

// update permission
chown -R www-data:www-data /var/www
```

# test site
In your browser, http://0.0.0.0:8080


