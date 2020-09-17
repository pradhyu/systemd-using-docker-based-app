#!/usr/local/env bash 

sudo cp systemd-service/docker-app.service /etc/systemd/system/docker-app.service
sudo chmod 644 /etc/systemd/system/docker-app.service

sudo cp systemd-docker-cleanup-service/docker-cleanup.service /etc/systemd/system/docker-cleanup.service
sudo chmod 644 /etc/systemd/system/docker-cleanup.service

sudo cp systemd-docker-cleanup-service/docker-cleanup.timer /etc/systemd/system/docker-cleanup.timer
sudo chmod 644 /etc/systemd/system/docker-cleanup.timer

# reload the system unit files
sudo systemctl daemon-reload

#start timer service
sudo systemctl status docker-cleanup.timer
sudo systemctl status docker-cleanup.service
# sudo systemctl disabled docker-cleanup.service
# the service needs to be enabled to start with timer
# timer controls the execution of the service 
# OnUnitInactiveSec means when since the last time it got stopped
# doesn't matter if you start or stop the service the timer continues from last time it got inactive
# sudo systemctl disable docker-cleanup.service
# sudo systemctl start docker-cleanup.service
# sudo systemctl stop docker-cleanup.service
sudo systemctl enable docker-cleanup.timer
sudo systemctl start docker-cleanup.timer


# view logs 
sudo journalctl -u docker-cleanup

