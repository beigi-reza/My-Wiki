# Nginx Refrence

<details><summary>Install Nginx</summary>
<p>

## Install Nginx On Server

``` bash
sudo yum install epel-release && yum install nginx   [On CentOS/RHEL]
sudo dnf install nginx                               [On Debian/Ubuntu]
sudo apt install nginx                               [On Fedora]
```
## Install and Run on Docker Commanmd

``` bash
docker run -itd --name nginx --hostname nginx \
-p 80:80 \
-p 443:443 \
-v /mnt/nginx/conf.d:/etc/nginx/conf.d \
-v /root/nginx/www:/var/www/html \
nginx:latest
```
## Install and Run on Docker-compose

```yml
version: "3.2"

services:

  nginx:
    restart: always
    image: nginx:latest
    container_name: nginx
    hostname: cntr-nginx
#    networks:
#       ronix-net:
#          ipv4_address: 150.50.50.10
    volumes:
     - /root/nginx/conf.d:/etc/nginx/conf.d
     - /root/nginx/www:/var/www/html
    ports:
     - 80:80
     - 443:443

#networks:
#  ronix-net:
#    external: true

```
  

</p>
</details>


## Check Nginx Version

```bash
nginx -v
docker exec -it nginx nginx -v
```

## Check Nginx Configuration Syntax

```bash
nginx -t
docker exec -it nginx nginx -t
```

## View All Nginx Config

```bash
nginx -T
docker exec -it nginx nginx -T
```

## Reload Config

```bash
nginx -s reload
docker exec -it nginx nginx -s reload
```

