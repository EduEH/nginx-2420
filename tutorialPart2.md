# nginx-2420

# Setting up a firewall and reverse proxy
**Make sure your system is updated with `sudo pacman -Syu` before starting**

1) Download the hello-server backend file
2) Long into your droplet using sftp instead of ssh
    -**sftp**: Used for transferring files between your machine adn the server.
3) `cd /home/YOUR_USERNAME/bin`
4) `put hello-server`
    -**put**: Transfers the file to the server.
5) `cd /etc/systemd/system/`
6) `sudo vim hello-server.service` to create a service file
7) Copy the following code to it and save with `:wq`:
```
[Unit]
Description=Starts hello-server

[Service]
Type=oneshot
ExecStart=/home/YOUR_USERNAME/bin/hello-server

[Install]
WantedBy=multi-user.target

```
8) Install UFW with `sudo pacman -S ufw`
) `sudo vim nginx-2420` to open the file used in part 1.

) Add the following to it, after the "location /" block:
```
location /hey {

    proxy_pass http://127.0.0.1:8080;

}
location /echo {

    proxy_pass http://127.0.0.1:8080;

}

```

) `sudo pacman -S ufw`