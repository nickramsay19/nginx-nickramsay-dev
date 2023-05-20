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
sudo cp -f ./conf.d/* /etc/nginx/conf.d/
sudo cp -f ./nginx.conf /etc/nginx/
```

Restart nginx with new config.
```sh
sudo systemctl restart nginx
```
