## Install Google Chrome browser on Debian

Following http://www.tecmint.com/install-google-chrome-in-debian-ubuntu-linux-mint/ (accessed 20170403).

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```
(Already included in installation guide for Debian on chrooted Chromebook.

[end]
