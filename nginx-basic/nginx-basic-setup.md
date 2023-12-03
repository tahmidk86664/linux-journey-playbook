# Nginx Server Setup

To setup a basic Nginx server, we just need to proceed by completing the following steps (assuming that we're using Ubuntu as OS):

1. Update the repository

```
sudo apt update
```

2. Install Nginx

```
sudo apt install nginx
```

3. Check status of nginx

```
sudo systemctl status nginx
```

4. Update the nginx configuration

```
server {
    listen 80;
    server_name your_domain;

    access_log /var/log/nginx/your_access_log_file.log;
    error_log  /var/log/nginx/your_error_log_file.log;

    root directory_of_your_application;
    index index_file;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
