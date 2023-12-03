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

3. Check status of Nginx

```
sudo systemctl status nginx
```

4. Enable the Nginx server to ensure Nginx server auto-restarts upon crashing

```
sudo systemctl enable nginx
```

5. Set the Nginx configuration
   In Nginx we have two important directory, one is **sites-available** and another is **sites-enabled**. In **sites-enabled** we'll make our configuration and in **sites-enabled** we need to make a **softlink** of our config file from **sites-available**. By default, there is a file named **default** in the **sites-available** directory, which we need to remove from **both directories** to set up our own configuration file. To configure our new file, we need to execute the following command:

   ```
   cd /etc/nginx/sites-available
   vim your_config_name

   # OR

   vim /etc/nginx/sites-available/you_config_name
   ```

   It's the best practice to make a new file with the name of your own application or domain name in the following directory.
   Now in your config file write down the following lines:

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

   Setting up a server block is easy! First, we just need to specify the port for listening to the server. By default, nginx listens on port 80. Then, we can specify the domains on which the server will listen. Don't forget to set up your access and error logs in the third and fourth lines. Next, we'll need to specify the root directory and the index file of our application. Finally, let's indicate the location from where to take the necessary files.
   That's it!

6. Save the config file

7. Make softling of the config file in **sites-enabled**

   ```
   sudo ln -s /etc/nginx/sites-available/your_config_file /etc/nginx/sites-enabled/
   ```

8. Now best practice is test the nginx config

   ```
   sudo nginx -t
   ```

9. Another best practic to **soft reload** the server to identify any uncaught errors after testing

   ```
    sudo nginx -s reload
   ```

10. Restart Nginx server and check the status
    ```
    sudo systemctl restart nginx.service
    sudo systemctl status nginx
    ```

That's it.

**#Happy_automating_on_your_DevOps_adventure**
