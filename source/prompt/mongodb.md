# Install MongoDB

## Import the public key used by the package management system

The Ubuntu package management tools (i.e. dpkg and apt) ensure package consistency and authenticity by requiring that distributors sign packages with GPG keys. Issue the following command to import the MongoDB public GPG Key:

    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

## Create a list file for MongoDB

Create the /etc/apt/sources.list.d/mongodb-org-3.0.list list file using the following command:

    echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list

    echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list

## Reload local package database

Issue the following command to reload the local package database:

    sudo apt-get update

## Install the MongoDB packages

You can install either the latest stable version of MongoDB or a specific version of MongoDB.

### Install the latest stable version of MongoDB

Issue the following command:

    sudo apt-get install -y mongodb-org

### Install a specific release of MongoDB

Specify each component package individually and append the version number to the package name, as in the following example:

    sudo apt-get install -y mongodb-org=3.0.1 mongodb-org-server=3.0.1 mongodb-org-shell=3.0.1 mongodb-org-mongos=3.0.1 mongodb-org-tools=3.0.1

### Pin a specific version of MongoDB

Although you can specify any available version of MongoDB, apt-get will upgrade the packages when a newer version becomes available. To prevent unintended upgrades, pin the package. To pin the version of MongoDB at the currently installed version, issue the following command sequence:

    echo "mongodb-org hold" | sudo dpkg --set-selections
    echo "mongodb-org-server hold" | sudo dpkg --set-selections
    echo "mongodb-org-shell hold" | sudo dpkg --set-selections
    echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
    echo "mongodb-org-tools hold" | sudo dpkg --set-selections

Versions of the MongoDB packages before 2.6 use a different repo location. Refer to the version of the documentation appropriate for your MongoDB version.

# Run MongoDB

The MongoDB instance stores its data files in /var/lib/mongodb and its log files in /var/log/mongodb by default, and runs using the mongodb user account. You can specify alternate log and data file directories in /etc/mongod.conf. See systemLog.path and storage.dbPath for additional information.

If you change the user that runs the MongoDB process, you must modify the access control rights to the /var/lib/mongodb and /var/log/mongodb directories to give this user access to these directories.

## Start MongoDB

Issue the following command to start mongod:

    sudo service mongod start

## Verify that MongoDB has started successfully

Verify that the mongod process has started successfully by checking the contents of the log file at /var/log/mongodb/mongod.log for a line reading

    [initandlisten] waiting for connections on port <port>

where `<port>` is the port configured in `/etc/mongod.conf`, 27017 by default.

    mongod --version

## Stop MongoDB

As needed, you can stop the mongod process by issuing the following command:

    sudo service mongod stop

## Restart MongoDB

Issue the following command to restart mongod:

    sudo service mongod restart

## Begin using MongoDB

To begin using MongoDB, see Getting Started with MongoDB. Also consider the Production Notes document before deploying MongoDB in a production environment.

Later, to stop MongoDB, press Control+C in the terminal where the mongod instance is running.
