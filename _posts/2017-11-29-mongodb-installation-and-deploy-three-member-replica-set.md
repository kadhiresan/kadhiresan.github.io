---
layout: post
title: MongoDB and Replica Set
---

**MongoDB:**
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas.

**Table of contents**

  1. Mongodb Installation on linux (red-hat-linux system)
  2. MongoDB Manipulation
  3. Describes how to create a three-member replica set (create 3 ec2 instances)


**MongoDB Installation**


* STEP 1: Install MongoDB on each system (Here i am going to install MongoDB 3.4)
  - [Ref Link](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/)
  - Configure the package management system (yum):
    - Create a /etc/yum.repos.d/mongodb-org-3.4.repo file so that you can install MongoDB directly, using yum.
    
    ```
      sudo vi /etc/yum.repos.d/mongodb-org-3.4.repo
    ```
* STEP 2: Add below lines into your file and save
  
  ```
    [mongodb-org-3.4]
    name=MongoDB Repository
    baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
    gpgcheck=1
    enabled=1
    gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
  ```
* STEP 3: Install the MongoDB packages and associated tools:

  ```
    sudo yum install -y mongodb-org
  ```

**MongoDB Manipulation**
  
  - Start MongoDB:
    
    ```
      sudo service mongod start
    ```
  - Verify that MongoDB has started successfully:
    
    ```
      sudo tail -f /var/log/mongodb/mongod.log  (OR) sudo service mongod status
    ```
  - Stop MongoDB:
    
    ```
      sudo service mongod stop
    ```
  - Restart MongoDB:
    
    ```
      sudo service mongod restart
    ```