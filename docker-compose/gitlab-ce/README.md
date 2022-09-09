## Setup Docker
```
# Setup Docker & docker-compose
sudo apt update
sudo apt install docker.io containerd docker-compose
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
# Setup datetime
sudo timedatectl set-timezone Asia/Jakarta
sudo timedatectl set-ntp on
```
## Setup SSL
```
sudo apt install certbot

sudo certbot certonly --rsa-key-size 2048 --standalone --agree-tos --no-eff-email --email yourmail@gmail.com -d gitlab.xrick.xyz

sudo mkdir -p /srv/gitlab/config/ssl/

sudo cp /etc/letsencrypt/live/gitlab.xrick.xyz/fullchain.pem /srv/gitlab/config/ssl/

sudo cp /etc/letsencrypt/live/gitlab.xrick.xyz/privkey.pem /srv/gitlab/config/ssl/

sudo openssl dhparam -out /srv/gitlab/config/ssl/dhparams.pem 2048
```
### Run
```
docker-compose up -d

docker-compose ps
```
### Get root password
```
docker exec -it gitlab-ce grep 'Password:' /etc/gitlab/initial_root_password
```
### Test
https://gitlab.xrick.xyz

## Sample setup gitlab runner

docker exec -it gitlab-runner bash
```
gitlab-runner register

Enter the GitLab instance URL (for example, https://gitlab.com/): 
https://gitlab.xrick.xyz
Enter the registration token: 
token
Enter a description for the runner: 
runner-1
Enter tags for the runner (comma-separated): 
runner-1
Enter an executor: 
docker
Enter the default Docker image (for example, ruby:2.7): 
alpine:latest
```