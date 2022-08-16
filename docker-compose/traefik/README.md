# Traefik
Traefik Reverse Proxy

### Traefik Password
Use `apache2-utils` to generate password. \
Example : `htpasswd -nb admin admin12345` \
admin:$apr1$fTlK/yNA$mms3yMHUvf3BwfYVHb6Jz.

### How to Run
docker network create proxy \
docker-compose up -d