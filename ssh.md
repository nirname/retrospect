# SSH

    sudo vi /etc/ssh/sshd_config
    ssh-keygen -t rsa -C "email@example.com"

## SSH tunnels

    # create
    ssh -fg user@1.2.3.4 -L 8888:5.6.7.8:22 -N

    # connect
    ssh -p 8888 user@localhost
