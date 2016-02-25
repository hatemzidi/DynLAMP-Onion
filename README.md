[![Docker Pulls](https://img.shields.io/docker/pulls/hatemzidi/dynlamp-onion.svg)](https://hub.docker.com/r/hatemzidi/dynlamp-onion/)
[![Docker Stars](https://img.shields.io/docker/stars/hatemzidi/dynlamp-onion.svg)](https://hub.docker.com/r/hatemzidi/dynlamp-onion/)
[![](https://badge.imagelayers.io/hatemzidi/dynlamp-onion:latest.svg)](https://imagelayers.io/?images=hatemzidi/dynlamp-onion:latest)

DynLAMP Onion (In Progress)
============

Dockerfile for a stack with a separate containers for Apache, PHP-FPM and MySQL

The image is available directly from https://hub.docker.com/

##Pre-Requisites

- install docker-compose [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
- install dsnmasq
- modify the ```VIRTUALHOST``` in ```docker-compose.yml``` to match with webserver hostname

##Installation Steps
###dnsmasq
tbd
###docker
tbd


##Usage

Start a cluster:

- ```docker-compose up -d ```


Destroy a cluster:

- ```docker-compose stop```



##Running On Mac

- install a VM
- install docker
- share your workspace





