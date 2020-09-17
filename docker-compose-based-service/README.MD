# install docker 
[centos@centos8 docker-compose-based-service]$ sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
Adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
[centos@cen

# install docker compose 
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

cd /usr/local/bin/
sudo chmod 655 docker-compose

docker-compose version

# start the application with docker-compose 
cd docker-compose-based-service
docker-compose up -d