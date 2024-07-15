
### URL

http://43.206.238.11/


## Prerequisites

- Docker installed on your system. [Installation guide](https://docs.docker.com/get-docker/)
- Docker Compose installed. [Installation guide](https://docs.docker.com/compose/install/)

## Setup Instructions

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/nginx-docker.git
cd nginx-docker


Step 2: Create docker-compose.yml
Create a docker-compose.yml file with the following content:

version: '3.8'

services:
  nginx:
    image: nginx:latest
    container_name: nginx_server
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
      - ./logs:/var/log/nginx
    ports:
      - "80:80"
    networks:
      custom_network:
        ipv4_address: 172.20.8.2

networks:
  custom_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.8.0/24

Step 3: Create nginx.conf
Create an nginx.conf file with the following content:

user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;

        location / {
            root   /usr/share/nginx/html;
            index  index.html index.htm;
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   /usr/share/nginx/html;
        }
    }
}

Step 4: Create Logs Directory
Create a logs directory to store Nginx logs:

mkdir logs

Step 5: Start the Nginx Server
Start the Nginx server using Docker Compose:

docker-compose up -d
