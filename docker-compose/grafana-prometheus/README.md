# Monitoring docker container using prometheus, garana, cAdvisor & node-exporter
## Setup IP
- edit `server-ip` on `prometheus.yml`
- edit grafana password `GF_SECURITY_ADMIN_PASSWORD=password` on docker-compose.yml
## Run
`docker-compose up --build -d`