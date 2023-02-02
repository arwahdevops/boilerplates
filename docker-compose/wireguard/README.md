## Setup Wireguard VPN Server
```
docker volume create wireguard-vol 
docker-compose up --build -d
```
#### Exec container
```
docker exec -it wireguard bash
```
#### Profile
cat /config/peer1/peer1.conf