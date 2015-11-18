# Nodejs

**Nodejs & npm**

Remove `nodejs`

    which nodejs

Install a new one

    sudo apt-get install curl
    curl --silent --location https://deb.nodesource.com/setup_4.x | sudo bash -
    sudo apt-get install --yes nodejs

Check npm version

    npm -v

Check installation path

    npm config get prefix

Reassure you are an owner

    sudo chown -R user /home/user/.node # Replace user to real user name

Add to `.bashrc`

    export PATH="$HOME/.node/bin:$PATH"
    source ~/.bash_profile

**Bower**

Installing bower

    npm install -g bower ember-cli

Check bower version

    bower -v

**Usage**

Go to a project, update node modules & start the project

    cd project/
    rm -rf node_modules
    npm i # npm install
    ember s # ember server

# Grunt

    sudo apt-get install python-software-properties python g++ make
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs

    npm install -g uglify-js

    sudo npm install -g bower
    bower install

    sudo npm install grunt-cli -g
    sudo npm install grunt -g
    npm install grunt
    npm install
