# nginx-nickramsay-dev

## Setup
Install nginx.
```sh
sudo apt update
sudo apt upgrade

sudo apt -y install nginx
sudo systemctl start nginx
```

Copy the configuration files into `conf.d`.
```sh
sudo cp nickramsay-dev.conf /etc/nginx/conf.d/
sudo cp console-nickramsay-dev.conf /etc/nginx/conf.d/
```

Restart nginx with new config.
```sh
sudo systemctl restart nginx
```
