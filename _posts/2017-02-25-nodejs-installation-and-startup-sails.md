---
layout: post
title: Node JS Installation and Setup the sails js project
---

**Node Js:**
Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world. - [from nodejs.org!](https://nodejs.org/en/)

**Table of contents**

  1. Installing NodeJS and setup the sails on Local
  2. Installing NodeJS and setup the sails on AWS EC2


**Installing NodeJS and setup the sails on Local**

  - We can download the Node.js source code or a pre-built installer for your platform. for([Downloads](https://nodejs.org/en/download/)).
  - it's always better to download *stable version* of any software, i would suggest you do the same.


* Step 1
  - Download your nodejs source code or pre-built installer for your platform
* Step 2
  - Install the node software, you downloaded from the above link, you will see this type of screen in your last step in installation.

  ![_config.yml]({{ site.baseurl }}/images/nodejs_installation/nodejs-setup.png)

* Step 3
  - Make sure you have Node and NPM installed by running simple commands to see what version of each is installed and to run a simple test program
  - Open the terminal or any similar command line tool, and type below commands

  ```
  $ node -v
   $ npm -v
  ```
* Step 4
  - To Install the Sails js globally type below command

  ```
  $ npm install sails -g
  ```

* Step 5
  - To generate a new app, just cd into the directory where you want it to be, and type:

  ```
  $ sails new [project-name]
  ```
  - If its done, you will get message like this
  > info: Created a new Sails app `[project-name]`!

* Step 6
  - To startup your sails app run below commands

  ```
  $ cd test-project
   $ sails lift
  ```

  -Cool, All Done. Now you will see this output from you terminal

  ![_config.yml]({{ site.baseurl }}/images/nodejs_installation/sails-lift.png)

* Step 7
  - Start your coding, njoy :)


**Installing NodeJS and setup the sails on AWS EC2**

  - Here, we can download the Node.js via NVM 
  - Node Version Manager (NVM) is a little bash script that allows you to manage multiple versions of Node.js on the same box. A version manager really helps to test our applications under different versions of the related software. [more info on NVM](https://github.com/creationix/nvm)

* Step 1
  - create AWS EC2 instance and connect to server via ssh

* Step 2
  - We just have to use the "apt" package manager. We should refresh our local package before install anything from the repositories

  ```
  $ sudo apt-get update
   $ sudo apt-get install build-essential libssl-dev
  ```
* Step 3
  - Install the NVM

  ```
  $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
  ```

* Step 4
  - Install the Node js

  ```
  $ nvm install stable
  ```

  - it will install latest stable version of the node

* Step 5
  - Install the Sails js globally, To install

  ```
  $ npm
  ```

* Step 6
  - Make sure you have Node and NPM installed by running simple commands to see what version of each is installed and to run a simple test program

  ```
  $ node -v
   $ npm -v
  ```

* Step 7
  - To generate a new app, just cd into the directory where you want it to be, and type:

  ```
  $ sails new [project-name]
  ```
  - If its done, you will get message like this
  > info: Created a new Sails app `[project-name]`!

* Step 8
  - To startup your sails app run below commands

  ```
  $ cd test-project
   $ sails lift
  ```

  -Cool, All Done. Now you will see this output from you terminal

  ![_config.yml]({{ site.baseurl }}/images/nodejs_installation/sails-lift.png)

* Step 9
  - Oops, in ordr to see our output on web browser, we need to Set Up Reverse Proxy Serve.
  - So, install Nginx using apt-get

  ```
  $ sudo apt-get install nginx
  ```

* Step 10
  - Now open the default server block configuration file for editing and add our localhost:1337

  ```
  $ sudo vi /etc/nginx/sites-available/default
  ```

  - Add this line inside "location/" - proxy_pass http://localhost:1337;

  ![_config.yml]({{ site.baseurl }}/images/nodejs_installation/proxy_serve.png)

  - Once you are done adding the location blocks for your applications, save and exit.

* Step 11
  - Now restart Nginx

  ```
  $ sudo service nginx restart
  ```
  - Now try it out by accessing your web server's URL (its public IP address or domain name).



