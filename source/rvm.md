# RVM

# How to remove RVM itself

    rvm implode
    rm /etc/rvm.rc
    rm /etc/profile.d/rvm.sh
    rm /usr/local/rvm

# Rails express patch

    rvm reinstall ruby-1.9.3-p385 --patch railsexpress -j 3
