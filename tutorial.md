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
8) `sudo vim index.html` to create the html file and open it in vim.
	- **vim:** Opens the designed file in vim.
9) Copy the following code into it:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2420</title>
    <style>
        * {
            color: #db4b4b;
            background: #16161e;
        }
        body {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            text-align: center;
            font-family: sans-serif;
        }
    </style>
</head>
<body>
    <h1>All your base are belong to us</h1>
</body>
</html>
```
10) Press excape and type :wq, then press enter to quit vim and save the file. 

11) Use `cd /etc/nginx` to access the directory with nginx's configuration file.
12) Use `sudo vim nginx.conf` to open the configuration file.
13) Inside the http{} block you should see a server{} block. Add the following code inside the http block, after the server block:
```
server {
    listen 80;
    server_name YOUR DROPLET IP;
    root /web/html/nginx-2420;
    location / {
        index.html;
    }
}
``` 