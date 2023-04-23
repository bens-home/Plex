# Plex

The setup I use for running a Plex server at home using Docker. It's a docker-compose that uses the [linuxserver/plex](https://hub.docker.com/r/linuxserver/plex) image.

*Note*: You will likely need to update the `volume` mappings in the `docker-compose.yml` file to point to the correct directories where the media is stored on your server.

## Getting Started

To start this service run:

```
docker-compose up -d
```

Which will run the container detached on the command line. It's set up to restart unless it is explictly stopped, so it will be started any time the host machine is rebooted. 

It will put all the config stuff in a `plex_config` directory, relative to the `docker-compose.yml` file. This config folder is ignored in the `.gitignore`.

Once running, it will be running Plex on port `32400` on the host machine, so make sure to allow it through the firewall if necessary:

```
sudo ufw allow 32400 comment "Plex public server"
```

## Access outside of home network

To access these Plex libraries outside of the LAN you will need to port forward `32400` on your router. 

Make sure to share your libraries with any users that you want to!

## Access when you have no internet

Plex will normally require you to authenticate with an account when signing in. If your ISP goes out and you lose internet 
but still want to watch stuff locally, then you need to specify some allow devices. 

In the web interface for Plex, go the server settings > Network. Towards the bottom is "List of IP addresses and networks that are allowed without auth". Add the following to that box:

```
192.168.1.1/255.255.255.0
```

This will allow any device that is connected to your router to keep connected. You can also add just specific devices if you want
