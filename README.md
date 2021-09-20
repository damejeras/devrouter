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

Certificates are loaded from `certs/` and `traefik/tls.yml`

Easiest way to generate self signed ceritificates is with [mkcert](https://github.com/FiloSottile/mkcert).

```
mkcert install
cd certs/
mkcert test.localhost
```
