# Step-by-step Server Setup Guide #
Assuming you do everything as root.

Each line in code snippet is a separate command in a terminal, so you should run em separately, line by line.

### Setting up Python3 ###
Ubuntu 14 should have Python3 installed by default so we only need to set it up for our needs.

* Updating package management tool 
```bash
apt-get update
apt-get -y upgrade
```
* Install pip3 - python 3 package manager
```bash
apt-get install -y python3-pip
```
* Install various dev tools
```bash
apt-get install -y build-essential libssl-dev libffi-dev python-dev
```
* Install LXML:
```bash
apt-get install -y libxml2-dev libxslt1-dev
```
```bash
apt-get install python3-lxml
```

### Installing MongoDB ###

* Import public key:
```bash
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
```
* Create a list file for MongoDB:
```bash
echo "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```
* Reload local package database:
```bash
apt-get update
```
* Install the MongoDB packages:
```bash
apt-get install -y mongodb-org
```
* Start MongoDB:
```bash
service mongod start
```

### Installing Python3 modules ###

* Install Requests:
```bash
pip3 install requests
```
* Install Selenium:
```bash
pip3 install selenium
```
* Install BeautifulSoup:
```bash
pip3 install bs4
```
* Install PyMongo:
```bash
pip3 install pymongo
```


### Installing and setting up Firefox (if you are going to use semrush scraper) ###

* Install Firefox
```bash
apt-add-repository ppa:mozillateam/firefox-next
apt-get update
apt-get install firefox xvfb
```
* Run Xvfb in the background and specify a display number
```bash
Xvfb :10 -ac &
```
* Set the display variable to the number you chose
```bash
export DISPLAY=:10
```
* Install GeckoDriver by first getting download link to linux geckodriver binary from here https://github.com/mozilla/geckodriver/releases
After you get the link (in my case its https://github.com/mozilla/geckodriver/releases/download/v0.16.1/geckodriver-v0.16.1-linux64.tar.gz) download geckodriver tar file to the server into, for example, var folder
```bash
cd /var
wget https://github.com/mozilla/geckodriver/releases/download/v0.16.1/geckodriver-v0.16.1-linux64.tar.gz
tar -xvzf geckodriver*
chmod +x geckodriver
export PATH=$PATH:/var/geckodriver
```