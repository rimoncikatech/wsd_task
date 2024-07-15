
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
