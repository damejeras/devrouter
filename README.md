# devrouter for local development with TLS

Example `docker-compose.yml`:
```
version: "3.7"

services:
  test:
    build:
      dockerfile: Dockerfile
    networks:
      - devrouter
    labels:
      - "traefik.enable=true"
      - "traefik.docker.network=devrouter"
      - "traefik.http.routers.test.rule=Host(`test.localhost`)"
      - "traefik.http.routers.test.tls=true"

networks:
  devrouter:
    external: true

```

# Run devrouter
```
mkcert install
cd certs/
mkcert localhost *.localhost
cd ..
docker network create devrouter
docker-compose up -d
```
