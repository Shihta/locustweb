# Locust Website

Locust software is a simply powerful software for every platform. Here is a note to show how to build this website.

## Platform

* [Raspberry Pi 2]
* [RASPBIAN] 

## Nginx

The original version of Nginx in repository is outdated. Here is how to build the last stable version on RPi2.

Added new file: /etc/apt/sources.list.d/nginx.list[1]
```sh
deb-src http://nginx.org/packages/debian/ wheezy nginx
```

Added key:
```sh
wget http://nginx.org/keys/nginx_signing.key
apt-key add nginx_signing.key
```

Building commands:
```sh
apt-get update
apt-get build-dep nginx
apt-get source -b nginx
```

Added nginx config: /etc/nginx/conf.d/locust.stark.tw.conf
```sh
server {
    listen       80;
    server_name  locust.stark.tw;
    location / {
        root   /usr/src/locust;
        index  index.html index.htm;
    }
}
```

## Python Virtual Environment

Start by installing the **virtualenv** and **pip**:
```sh
apt-get install virtualenvwrapper python-pip
```

I think pip version is washed out:
```sh
pip install --upgrade pip
```

There is a little problem occurred because python version is [old]:
```sh
apt-get install python-dev libffi-dev libssl-dev
pip install ndg-httpsclient
```

[RASPBIAN]:https://www.raspberrypi.org/downloads/
[Raspberry Pi 2]:https://www.raspberrypi.org/products/raspberry-pi-2-model-b/
[1]:http://nginx.org/en/linux_packages.html
[old]:http://stackoverflow.com/questions/29099404/ssl-insecureplatform-error-when-using-requests-package

