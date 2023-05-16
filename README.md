# nginx-nickramsay-dev

## Setup
### 1. Install nginx
```sh
sudo apt update
sudo apt upgrade

sudo apt -y install nginx
sudo systemctl start nginx
```

### 2. `/etc/nginx/conf.d/reverse-proxy.conf`
```
# reverse proxy all http port 80 requests to localhost:8000
server {
    listen 80;
    listen [::]:80;

    server_name nickramsay.dev;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

# do the same for https port 443
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;

    server_name nickramsay.dev;

    ssl_certificate /path/to/your/certificate.crt;
    ssl_certificate_key /path/to/your/private_key.key;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

# reverse proxy console.nickramsay.dev connections to a different port 8001
server {
    listen 80;
    listen [::]:80;
    server_name console.nickramsay.dev;

    location / {
        proxy_pass http://127.0.0.1:8001;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
