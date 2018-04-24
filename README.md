# Start Docker Compose on Ubuntu Boot
Script example for Docker-Compose starting on boot.

Two scripts are provided
1. docker-compose-app-background.service - Run docker-compose in background (-d option)
2. docker-compose-app-foreground.service - Run docker-compose in foreground

## Installation

First install dcoker && docker Compose
`apt-get install docker.io docker-compose`

Then clone the repository
`git clone https://github.com/hongkongkiwi/docker-compose-startonboot.git`

Copy the script you want (e.g. run in background)
`cp docker-compose-app-background.service /etc/systemd/system/docker-compose-app.service`

(optional) By default, the script looks for the docker-compose file in /app, if your location is different for example /opt/myappdir then edit the script and update the name of your app
`sed -i s#WorkingDirectory=/app#WorkingDirectory=/opt/myappdir# /etc/systemd/system/docker-compose-app.service`

Enable the script to start on Boot
`systemctl enable docker-compose-app`

And your done! If you want to start the script now you can use
`systemctl start docker-compose-app`

If you make any changes after the daemon is enabled you will need to RUN
`systemctl daemon-reload`
