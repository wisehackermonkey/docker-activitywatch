# Activity Watch Docker file

### build
```bash
docker build . -t aw-server_image
```

### run 
#### Compose 
```bash
docker run -d  --restart=unless-stopped -v ./.aw-server-data:/root/.local/share/activitywatch/aw-server/ -p 5600:5600 --name activitywatch aw-server 

docker run -it --rm -p 5600:5600 --name aw-server aw-server_image

  aw-server:
    build: .
    container_name: activitywatch
    image: aw-server
    ports:
      - "5600:5600/tcp"
    restart: unless-stopped
    volumes:
      - ./.aw-server-data:/root/.local/share/activitywatch/aw-server/

```