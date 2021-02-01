# Express-ES6-Server-Install-Tutorial

In this Tutorial I show you how to install a ES6 Nodejs Server on a
Server with Express. Also a little guid for running an express app on port 80. 

# Install

```shell
    § sudo apt update
```

```shell
    § sudo apt install nodejs npm
```

```shell
    § curl -sL https://deb.nodesource.com/setup_12.x | sudo bash - // Set the nodejs package to the v12
```

```shell
    § sudo apt install nodejs
```

```shell
    § nodejs --version
```

Now we see the v12 from nodejs. The right one for ES6

# Upload

Now upload your project on your server with git or sftp. Now navigate to the folder

## Start

```shell
   $ npm i // Install all packages from the package.json
```

```shell
    $ nodemon
```

Great it works! look in your browser: http://ip_adress:port or http://domain.net:port

# Background process

For run your app in the background in a process use **pm2**

[PM2 Github Link](https://github.com/Unitech/pm2)

So install PM2

```shell
    $ npm install pm2 -g
```

For starting the express server with pm2

```shell
    $ pm2 start index.js // Replace the main js file when your name is not index.js
```

Fine! The Express Server run now in a background process and you can also stop it.

```shell
    $ pm2 stop index.js
``` 

# Set a default 80 port

I think, you don't want to run your app on port 3000 or some other ports. The default http port is 80
but you can't change the express port to 80. So you can install a package called libcap2-bin

 [Website of libcap2-bin](https://packages.debian.org/de/sid/libcap2-bin)
 
 First **stop** your app and install it
 
```shell
    $ sudo apt install lib2cap-bin
```

Now you need to setcap 

```shell
    $ sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``
```

Now you need to edit a file. You can choose nano or other editors link vim.

```shell
    $ sudo vim index.js
```

By vim press **i** to edit and change the express port to **80**.

Then Save the file with ESC, write :X and press Enter.

Now start the background process again and view your page.

```shell
    $  pm2 start index.js
```

🎉 Nice! Your web page is on http://ip_adress or http://domain.net

