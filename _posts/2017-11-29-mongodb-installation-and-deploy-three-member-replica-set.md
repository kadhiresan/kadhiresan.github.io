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

**Deploying a Replica Set**
Now we are going to create replica set with these 3 mongodb instances, In order to do that we need to modify configuration of each of our mongodb instance

  - 1.Edit the mongo confi file [Ref Link](https://docs.mongodb.com/manual/tutorial/deploy-replica-set/)

    ```
      sudo vi /etc/mongod.conf
    ```

  - 2.Add your IP address to bindIP(Here i am using my private IP's) and set your replica set name
    **Note**
      - We have to modify 'bindIp' into IP of the instance.
      - Replica set name should be same for all the mongodb instance which you want to be a part of same replica set

      ```
        bindId: 172.0.0.1,<your private IP>
        replication:
          replSetName: <your replica set name>
      ```

  - 3.Folow the same step(1, 2) for remaining instances and restart the mongod service on each instance
  
  - 4.Start your mongod with --replSet
    
    ```
      sudo mongod --replSet <your replica set name>
    ```

  - 5.Start your mongo shell with --host
  
    ```
      mongo --host <ip address>
    ```

  - 6.Initiate the replica set

    ```
      rs.initiate( {
        _id : "religareMongoRepset",
        members: [ { _id : 1, host : "<private ip 1>:27017" } ]
      });
    ```
  
  - 7.Verify the initial replica set configuration. Using any on of the below cmd
    
    ```
      rs.status() OR rs.conf()
    ```
  
  - 8.Add the remaining members to the replica set.
  
    ```
    rs.add("<private ip 2>:27017");
    rs.add("<private ip 3>:27017");
    ```

**Notes:**

* For querying secondary run the following command first. After running this, you can do all regular stuff on secondary.
  
  ```
    rs.slaveOk()
  ```
* To see the replication status, run the following command on primary. This will show you if the secondaries are up to date or lagging.
    
  ```
    db.printSlaveReplicationInfo()
  ```
    
