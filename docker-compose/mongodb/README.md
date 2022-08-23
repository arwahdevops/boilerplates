### Create network & volume
```
docker network create --name=staging
docker volume create --name=mongodb-vol-staging
```
### Exec container
`docker exec -it mongo-staging /bin/bash`
### Login mongodb
`mongo admin -u root -p rootpassword`