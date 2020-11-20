# Docker

The client and server are available as dockerized images: 

+ [Server](https://hub.docker.com/r/unglue/server)
+ [Client](https://hub.docker.com/r/unglue/client)

## Docker-Compose Server

In order to create an unglue server inside a docker-compose file for local compiling:

```yaml
version: '3'
services:
  ...
  unglue:
    image: unglue/server
    ports:
      - "3000:3000"
```

## Docker-Compose Client and Server

Its very common to dockerize the client and server so its fast and does not require any additional installations.

```yaml
unglueserver:
  image: unglue/server
  ports:
    - "3000:3000"
unglueclient:
  image: unglue/client
  volumes:
    - ./:/app
```

## Docker

Run the docker image. Map port 3000 to local port 3000.

`docker run -d -p 3000:3000 unglue/server`

You should now be able to access `https://localhost:3000`.
