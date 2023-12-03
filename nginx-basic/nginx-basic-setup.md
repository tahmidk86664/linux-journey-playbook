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
  root /var/www/html

  location / {}
}
```
