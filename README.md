[![dockeri.co](https://dockerico.blankenship.io/image/reth01/caddy-cloudflare)](https://hub.docker.com/r/reth01/caddy-cloudflare)

# Docker
## Docker-cli
```
docker run --rm -it \
  --name caddy \
  --net=host \
  -v /root/caddy/data:/data \
  -v /root/caddy/config:/config \
  -v /root/caddy/Caddyfile:/etc/caddy/Caddyfile \
  -e CF_API_TOKEN= \
  reth01/caddy-cloudflare:latest
```

## Docker-compose
```
version: '3.3'
services:
    alist-proxy:
        image: 'reth01/caddy-cloudflare:latest'
        container_name: caddy
        environment:
            - CF_API_TOKEN=
        volumes:
          - ./Caddyfile:/etc/caddy/Caddyfile
          - ./site:/srv
          - ./data:/data
          - ./config:/config
        restart: unless-stopped
        network_mode: "host"
```
