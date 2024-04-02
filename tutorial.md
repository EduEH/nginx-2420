# nginx-2420

# Creating a demo page with nginx with simple steps

1) Start by making sure your system is updated by using the command `sudo pacman -Syu`.
	- **sudo**: Runs the command with admin permissions.
	- **pacman**: This is Arch's package manager, used to install the packages.
	- **-Syu**: System update.  
2) Install vim with the command `sudo pacman -S vim`.
	- **-S**: Used with pacman to install a package.
3) Install nginx with `sudo pacman -S nginx`.
4) Use `systemctl status nginx.service` to check if nginx was installed.
	- **systemctl:** Is a tool to manage services.
	- **status**: Checks whether a service is activated or not. 
5) Make sure you are in the nginx directory with `cd /etc/nginx`.
	- **cd:** Changes to the specified directory.
6) Use the command `sudo mkdir -p ./web/html/nginx-2420` to make a series of directories inside the nginx one.
	- **mkdir:** Makes a directory with the specified name.
	- **-p:** With mkdir, makes all the dependend directories. In this case, it creates "nginx-2420" and all the directories above it(web and html).
	- **. :** The period makes sure the path starts at the current directory. DON'T FORGET THE PERIOD.
7) `cd ./web/html/nginx-2420` to go to the nginx24-20 directory.

99) Use `cd /etc/nginx` to access the directory with nginx's configuration file.
) Use `sudo vim nginx.conf` to open the configuration file.
) Inside the http{} block you should see a server{} block. Add the following code inside the http block, after the server block:
```
server {
    listen 80;
    listen [::]:80;
    server_name domainname1.tld;
    root /usr/share/nginx/domainname1.tld/html;
    location / {
        index index.php index.html index.htm;
    }
}
``` 