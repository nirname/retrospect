# Chrome

## Add repository

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'

## Install

sudo apt-get update
sudo apt-get install google-chrome-stable
