# SonarQube Community Docker Compose

## Add config virtual memory 
```
sudo nano /etc/sysctl.conf
```
Add the following lines to the bottom of that file :
```
vm.max_map_count=262144
fs.file-max=65536
```
## Login
Login : admin \
Password : admin