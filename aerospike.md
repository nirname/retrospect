# Aerospike

## Ubuntu Install Steps

**Step 1:**

First, on our Linux Ubuntu server we will download the Aerospike database software. Navigate to your preferred directory and run:

    wget -O aerospike.tgz 'http://aerospike.com/download/server/latest/artifact/ubuntu12'

**Step 2:**

Next, we will un-tar the file. Run:

    tar -xvf aerospike.tgz

**Step 3**:

Our next step will be to cd into the directory and run the install.

    cd aerospike-server-community-*-ubuntu12
      sudo ./asinstall # will install the .rpm packages

**Step 4**:

Our last step is to start our Aerospike Database service.

    sudo service aerospike start && \
      sudo tail -f /var/log/aerospike/aerospike.log | grep cake
      # wait for it. "service ready: soon there will be cake!"

** Note that root access (sudo) is required to install packages.
Need more help?

## Commands

**Start Aerospike Server**

For Aerospike Enterprise, start instructs the server to Fast Restart, if running Aerospike Community or running a namespace that isn't supported this command behaves the same as coldstart. For more information regarding restart modes, see Restart Modes.

To start aerospike database service:

    /etc/init.d/aerospike start

**Coldstart Aerospike Server**

For Aerospike Enterprise, coldstart forces the server to rebuild the in-memory index by scanning the persisted records. This may take a significant amount of time depending on the size of the data. For Aerospike Community this is the same behavior as start.

    /etc/init.d/aerospike coldstart

**Get Running Status of Aerospike Server**

To determine if the Aerospike Daemon is currently running, use the status command:

    /etc/init.d/aerospike status

The status command doesn't inform you when the service port is ready, instead use the STATUS info command which will return "OK" when ready:

    asinfo -v STATUS

**Restart Aerospike Server**

The restart command is equivalent to running stop followed by start:

    /etc/init.d/aerospike restart

**Stop Aerospike Server**

To shutdown the Aerospike Server use the stop command:

    /etc/init.d/aerospike stop
