# Plex

The setup I use for running a Plex server at home using Docker.

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
sudo ufw allow 32400
```

## Access outside of home network

To access these Plex libraries outside of the LAN you will need to port forward `32400` on your router. 