# NGinx

To add nginx yum repository, create a file named /etc/yum.repos.d/nginx.repo and
paste one of the configurations below:

CentOS:

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=0
    enabled=1

RHEL:

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/rhel/$releasever/$basearch/
    gpgcheck=0
    enabled=1

Nginx configuration:

    /usr/local/nginx/conf/nginx.conf
