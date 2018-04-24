# Start Docker Compose on Ubuntu Boot
Script example for Docker-Compose starting on boot. I always need this for my virtual machines but couldn't find a simple example.

Two scripts are provided
1. [docker-compose-app-background.service](docker-compose-app-background.service) - Run docker-compose in background (-d option)
2. [docker-compose-app-foreground.service](docker-compose-app-background.service) - Run docker-compose in foreground

## Installation

First install docker.io and docker Compose

`apt-get install docker.io docker-compose`

Then clone the repository

`git clone https://github.com/hongkongkiwi/docker-compose-startonboot.git`

Copy the script you want (e.g. run in background)

`cp docker-compose-app-background.service /etc/systemd/system/docker-compose-app.service`

(optional) By default, the script looks for the docker-compose file in /app, if your location is different for example /opt/myappdir then edit the script and update the name of your app

`sed -i s#WorkingDirectory=/app#WorkingDirectory=/opt/myappdir# /etc/systemd/system/docker-compose-app.service`

Enable the script to start on Boot

`systemctl enable docker-compose-app`

## Other handy commands

And your done! If you want to start the script now you can use

`systemctl start docker-compose-app`

If you make any changes after the daemon is enabled you will need to run this command

`systemctl daemon-reload`

You can make sure your dockers are running by using

`docker ps`

## Special Thanks

Script example is from [this StackOverflow Post](https://stackoverflow.com/questions/43671482/how-to-run-docker-compose-up-d-at-system-start-up).
