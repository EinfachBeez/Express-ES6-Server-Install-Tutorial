# Express-ES6-Server-Install-Tutorial

In this tutorial, I will show you how to install an ES6 Nodejs Server on a server with Express.
On the bottom, there is also a guide on how to run your express app on port 80.

# Install

```shell
    $ sudo apt update
```

```shell
    $ sudo apt install nodejs npm
```

```shell
    $ curl -sL https://deb.nodesource.com/setup_current.x | sudo bash - #Install the current version of NodeJS
```

```shell
    $ sudo apt install nodejs
```

```shell
    $ nodejs --version
```

Now we can see the current version (_v16_) from NodeJS. The right one is for ES6.

# Upload

Now upload your project on your server with git or sftp. After that, navigate to the folder

## Start

```shell
   $ npm i # Install all packages from the package.json
```

```shell
   $ nodemon
```

Great, it should work now! Look it up in your browser ( _http://ip_adress:port or http://domain.tld:port_ )

# Background process

To run your app in the background process we are going to use **PM2**

[PM2 Github Link](https://github.com/Unitech/pm2)

Therefore install PM2

```shell
   $ npm install pm2 -g
```

For starting the express server with pm2, run:

```shell
   $ pm2 start index.js #Replace the main js file when your name is not index.js
```

Fine! The Express Server run now in a background process and you can also stop it.

```shell
   $ pm2 stop index.js
```

# Set default http port (80)

You probably don't want to run your app on port 3000 or any other, non-default HTTP port.
The default HTTP port would be 80 but you can't change the express port to 80.
To make it happen you can install a package called **libcap2-bin**

 [Website of libcap2-bin](https://packages.debian.org/de/sid/libcap2-bin)

 First **stop** your app and install the package

```shell
   $ sudo apt install lib2cap-bin
```

Now you need to use **setcap**

```shell
   $ sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``
```

After that, you need to edit the file. You can choose your favourite editor like _nano_ or _vim_

```shell
   $ sudo vim index.js
```

With vim, press **i** to edit and now change the express port to **80**.

Then save the file by pressing **ESC**, write **:X** and press enter.

Now start the background process again.

```shell
   $  pm2 start index.js
```

🎉 Nice! Your web page should be available on _http://ip_adress_ or _http://domain.tld_
