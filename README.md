# Watchtower

Quick Start¶
With watchtower you can update the running version of your containerized app simply by pushing a new image to the Docker Hub or your own image registry. Watchtower will pull down your new image, gracefully shut down your existing container and restart it with the same options that were used when it was deployed initially. Run the watchtower container with the following command:


## docker run
```
$ docker run -d \
--name watchtower \
-v /var/run/docker.sock:/var/run/docker.sock \
containrrr/watchtower
```
## docker-compose.yml  
docker-compose up -d
```
version: "2.2"
services:
  portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer
    volumes:
      - /path/to/data:/data
      - /var/run/docker.sock:/var/run/docker.sock
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 8000:8000
      - 9000:9000
    restart: unless-stopped
```


## update-portainer_ce.yaml  
run
```
services:
    watchtower:
        volumes:
            - /var/run/docker.sock:/var/run/docker.sock
        image: containrrr/watchtower
        command: --run-once portainer_ce
```
