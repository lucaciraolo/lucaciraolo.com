# Unifi Server

I maintain and monitor a few different networks for clients and family. As I install Ubiquiti wireless access points, they can all be connected to a hosted Unifi server which means I can make changes and monitor them remotely. Of course, I found a docker container which makes setup easy. Here is the command to set up and run the container.

## Updating Unifi Version

- pull latest unifi image:
  `docker pull jacobalberty/unifi:latest`

- download a backup file of the config from the Unifi web interface

- `docker stop unifi`

- `docker rename unifi unifi.old`

- `docker run -d --init -p 8080:8080 -p 8443:8443 -p 3478:3478/udp -p 10001:10001/udp -e TZ='Europe/London' -v ~/luca/unifi:/unifi --name unifi --restart unless-stopped jacobalberty/unifi:latest`

- once everything works: `docker rm unifi.old`
