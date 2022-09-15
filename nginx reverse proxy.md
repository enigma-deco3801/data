# nginx reverse proxy
___
### Setup
```
sudo apt-get install nginx

# remove default configuration
sudo rm /etc/nginx/sites-enabled/default

# make our own node configuration
sudo vim /etc/nginx/sites-available/node
```

### Content
```
server {
    listen 80;
    server_name <DOMAIN_OR_DNS_ADDR>;

    location / {
        proxy_set_header   X-Forwarded-For $remote_addr;
        proxy_set_header   Host $http_host;
        proxy_pass         "http://127.0.0.1:<PORT>";
    }
}
```

Next, we need to symlink our configuration to `sites-enabled` for it to be used by Nginx, since it's currently in `sites-available`:

```
sudo ln -s /etc/nginx/sites-available/node /etc/nginx/sites-enabled/node
```

### Apply the configuration
```
sudo service nginx restart
```

