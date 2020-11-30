# 使用Nginx-UI
[GitHub](https://github.com/schenkd/nginx-ui)
## Authentication

[BasicAuth with nginx](https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/)

In general, this app does not come with authentication. However, it is easy to setup basic auth to restrict unwanted access.
Here is how this can be done when using nginx.

### Configure the auth file

1. Verify that `apache2-utils` (Debian, Ubuntu) or `httpd-tools` (RHEL/CentOS/Oracle Linux) is installed
2. Run the htpasswd utility to create a new user and set a passwort.
    - Make sure, that the directory exists
    - Remove the `-c` flag, if you have created a user before, since it creates the inital user/passwort file
    - `sudo htpasswd -c /etc/apache2/.htpasswd user1`

### Configure nginx

The following example adds basic auth to our nginxui app running in a docker container with a mapped port 8080.
In this case, it will be accessible via nginx.mydomain.com

```none
server {
    server_name nginx.mydomain.com;

    location / {
        proxy_pass http://127.0.0.1:8080/;
    }

    auth_basic "nginxui secured";
    auth_basic_user_file /etc/apache2/.htpasswd;

    # [...] ommited ssl configuration
}
```

1. Add above nginx conf to your `/etc/nginx/my.conf` file
2. Run `nginx -t` to make sure, that your config is valid
3. Run `systemctl restart nginx` (or equivalent) to restart your nginx and apply the new settings
4. Your nginx ui is now accessible at nginx.mydomain.com and will correctly prompt for basic auth