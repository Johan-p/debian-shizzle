# debian-shizzle

#guest additions

echo deb http://ftp.debian.org/debian stretch-backports main contrib > /etc/apt/sources.list.d/stretch-backports.list
apt update
apt install virtualbox-guest-dkms virtualbox-guest-x11 linux-headers-$(uname -r)

#google-chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
dpkg -i google-chrome-stable_current_amd64.deb 
apt-get install libappindicator3-1
apt-get install libdbusmenu-glib4 libdbusmenu-gtk3-4 libindicator3-7
apt --fix-broken install
dpkg -i google-chrome-stable_current_amd64.deb 

which google-chrome
export PATH=$PATH:/usr/bin/google-chrome

#pip and selenium
apt-get install python-pip
pip install pyvirtualdisplay selenium

#sublime text
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
apt-get update
apt-get install sublime-text

#chromedriver
#check latest version at https://chromedriver.storage.googleapis.com/index.html 
wget -N https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip -P ~/Downloads
unzip ~/Downloads/chromedriver_linux64.zip -d ~/Downloads
chmod +x ~/Downloads/chromedriver
mv -f ~/Downloads/chromedriver /usr/local/share/chromedriver
ln -s /usr/local/share/chromedriver /usr/local/bin/chromedriver
ln -s /usr/local/share/chromedriver /usr/bin/chromedriver
