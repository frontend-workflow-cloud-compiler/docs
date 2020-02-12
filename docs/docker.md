# Docker Client and Server

Its very common to dockerize the client and server so its fast and does not require any additional installations.

## Docker Compose

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
