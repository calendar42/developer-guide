# Software Package Guide

At C42 we work with prepared installations for our team that contain different packages of software depending on the role of the team member. Within this setup, both Mac and Ubuntu are supported. This guide is constantly updated to keep up-to-date with the agile software world. These updates are reflected in the [changenotes](#make-me-work).


## The different software packages

* **General package**: Installed for all team members
* **Developer package**: Installed for team members touching and testing code
* **UX package**: Installed team members people design User experiences
* **Bizdev package**: Installed for team members that are developing business

## Todo's in this document

* Extend list
* Define minimum versions of software
* Add all the links to the different software

## General Package

#### Mac & Ubuntu

| Name 						|  Short Description 		| Version
| --------					| --------					|------------------
| Chrome | Browser | [latest](https://www.google.nl/chrome/browser/desktop/)
| Flux| Automatic screen dimmer | [latest](https://justgetflux.com/)
| LastPass Chrome extension | Password manager | [latest](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd)
| lastpass-client 	| Password manager command line | [latest](https://lastpass.com/misc_download2.php)
| Sublime Text 3^	| Text editor | [latest](www.sublimetext.com/3)
| Skype	| VOIP | [latest](http://www.skype.com/en/download-skype/skype-for-computer/)
| HipChat | Chat app | [latest](https://www.hipchat.com)
| Slack | Chat app | [latest](https://slack.com)

_^ Yes, anyone at C42 should at least have the unpaid version of Sublime Text. In the end the computer is just a digital type writer, everybody needs a good text editor. Others are also allowed of course ;)_

#### Mac only

| Name 						|  Short Description 		| Version
| --------					| --------					  | --------
| Clipmenu 				| Clipboard manager   | [0.4.3](https://dl.dropboxusercontent.com/u/1140644/clipmenu/ClipMenu_0.4.3.dmg)
| BetterTouchTools 			| Workspace shortcuts for keyboard and mouse | [latest](http://www.bettertouchtool.net)
| Adium 					| Chat messaging (XMPP) | [latest](https://adium.im)
| Lastpass App				| Password manager | latest on App Store


#### Ubuntu only

| Name 						|  Short Description 		
| --------					| --------					
| Pidgin 					| Chat messaging (XMPP)
| Thunderbird					| Mail program
| Terminator 					| Terminal
| Diodon 					| Clipboard manager


## Developer Package

#### Mac & Ubuntu

| Name 						|  Short Description 	| Version	
| --------					| --------					|-------
| Top Programming Fonts | to look at something nice all day | [latest](https://github.com/hbin/top-programming-fonts)
| PyCharm 					| Python IDE | latest
| IntelliJ 					| Java IDE | latest
| Android Studio 				| Android IDE | latest
| command-line: git 		| | latest
| command-line: hg 			| | latest
| command-line: lastpass-cli| | latest
| command-line: subl 		| | latest
| command-line: python-2.7 	| | latest
| command-line: ssh-copy-id | | latest
| command-line: ssh 		| | latest
| command-line: node 		| | latest
| command-line: virtualenv 	| | latest
| command-line: virtualenvwrapper | | latest
| command-line: vim 		| | latest
| command-line: npm 		| | latest
| command-line: grunt 		| | latest
| command-line: ruby 		| | latest
| command-line: ADT 		| | latest
| command-line: Cordova 	| | latest
| submlime-extension: SublimeLinter | | latest
| apache server  		| Up and running installation | latest
| MySQL server 			| | latest
| postgresQL with postGIS   	| | 9.4
| Chromium 			| Development version of Chrome |
| Poedit			| i18n editor | latest
| Tortoise HG 			| Visual HG manager | latest
| Chrome Extension Postman | |
| Chrome Extension DevDocs | |
| Chrome Extension JSON editor | |
| Chrome Extension Less editor | |
| Chrome Extension RegExp Tester App | |
| Chrome Extension JSFiddle | |
| Chrome Extension Python Fiddle | |

#### Mac only

| Name 						|  Short Description 	| Version	
| --------					| --------					|---------
| xCode & development utils | Needed for a lot of low-level development stuff | latest
| command-line: brew 		| Package manager | [latest](http://brew.sh/)
| iTerm 					| Improved terminal | [latest](https://iterm2.com/downloads.html)
| java for OSX | Java runtime | [latest](http://apple.com)



#### Ubuntu only

| Name 						|  Short Description 		
| --------					| --------					
| Meld 						| Diffing tool
| Slack client 					| Slack communications
| gitg						| Visual GIT Manager
| Ubuntu version | LTS always. All softwares are guaranteed to work. Currently 14.04.2 LTS. 
| Compiz settings manager | 

## UX Package

#### Mac only

| Name 						|  Short Description 		
| --------					| --------					
| Adobe Creative Cloud 		| The hardcore design tools

## BizDev Package

#### Mac only

| Name 						|  Short Description 		
| --------					| --------					
| Microsoft Office 			| The tools for the office


## Other things that might be automated

* Automatically generated public key with passphrase on lastpass
* Automatically add to calendar42 github account and also upload public key
* Automatically create a folder structure: ~/Developer/Calendar42
* 

## Initial package installations on Mac

This is what I (Jasper) did on my new machine to install the first necessary command line tools. Node js, can't be installed like this sadly, for that you need to download a dmg.

```
# First make sure xcode is installed (through app store)
# then...
# accept dev tools license
sudo xcodebuild -license
# install brew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# install hg
brew install hg
# install lastpass-cli
brew install lastpass-cli
# install ssh-copy-id
brew install ssh-copy-id
brew install libtiff libjpeg webp little-cms2
# install postgres and postgis
xcode-select --install
brew install postgresql
brew install postgis
brew install gdal
brew install libgeoip
# install libyaml
brew install libyaml
# install pip
sudo easy_install pip
# install virtualenv
sudo pip install virtualenv
# install virtualenvwrapper
sudo pip install virtualenvwrapper
# Create public key
ssh-keygen -t rsa -b 4096 -C "jasper@calendar42.com"
# copy public key for use in github account
pbcopy < ~/.ssh/id_rsa.pub
# have sublime in the terminal (Requires Sublime 3 to be installed)
mkdir ~/bin
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
sudo echo "~/bin" >> /etc/paths
```

## .bash_profile example

Can also be put in `/etc/profile` to be system wide instead of per user

```
# System-wide .profile for sh(1)

if [ -x /usr/libexec/path_helper ]; then
	eval `/usr/libexec/path_helper -s`
fi

if [ "${BASH-no}" != "no" ]; then
	[ -r /etc/bashrc ] && . /etc/bashrc
fi


##### General commands

# Navigation and listing util alias
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ~='cd ~'

#Add sudo in front of the previous written command. Doesn't work with commands with lots of arguments.
alias fuck='sudo $(history -p \!\!)'

#forward a port, example of usage: forwardPort42 6543 alpha
function forwardPort42(){
    ssh -L $1:localhost:$1 $2.c42.it
}

#Add sudo in front of the previous written command. Doesn't work with commands with lots of arguments.
alias fuck='sudo $(history -p \!\!)'


##### Fixes, comment in as necessary

# For making nodejs and bootstrap work on Mac (https://github.com/react-bootstrap/react-bootstrap/issues/538)
# ulimit -n 2560

# For python virtualenv
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
WORKON_HOME=/Users/$USER/Developer/virtualenvs
source /usr/local/bin/virtualenvwrapper.sh # the answer to  which virtualenvwrapper.

##### Logging in commands

alias alpha="ssh $USER@alpha.calendar42.com -4"
alias beta="ssh $USER@beta.calendar42.com -4"
alias prod="ssh $USER@calendar42.com -4"
alias production="prod"
alias port_alpha="ssh -L 6543:localhost:6543 alpha.calendar42.com"
alias port_beta="ssh -L 6543:localhost:6543 beta.calendar42.com"

##### Version control commands

# hg and file management alias
alias hgPullAndUp='hg pull -u'
alias rmorig='find . -name "*.orig" -delete'
alias removepyc='find . -name "*.pyc" -delete'


##### Mac specific commands

alias clear_dns_cache='dscacheutil -flushcache'


##### Program specific commands

#Runs the yuidocs in the current folder and makes it available in the port 5000
alias yuidocserver='yuidoc . --server 5000'

# Run python tests
alias testAll='python -m unittest discover testing/'

# run chromium browser with no security mode on
alias chromium-browser-no-web-security='chromium-browser --disable-web-security &'

alias chrome='open -a Google\ Chrome\ Canary --args --disable-web-security -–allow-file-access-from-files'


# got to and serve RTD documentation
alias cddocs="cd /Users/$USER/Developer/Calendar42/Calendar42-documentation/; workon c42_docs; echo 'TO RUN: mkdocs serve --verbose'"

# Go to django app
alias cdprivate="cd /Users/$USER/Developer/Calendar42/django_app/; workon c42_django_app"

# Fix virtualenv permissions
alias fixpermissionsvirtualenv="sudo chmod -R 775 /Users/$USER/virtualenvs; sudo chown -R $USER:staff /Users/$USER/virtualenvs*;"

# Git aware prompt (requires https://github.com/jimeh/git-aware-prompt)
# export HISTTIMEFORMAT="%d/%m/%y %T "
# export GITAWAREPROMPT=~/.bash/git-aware-prompt
# source $GITAWAREPROMPT/main.sh
# export PS1="\u@\h \w \[$txtcyn\]\$git_branch\[$txtred\]\$git_dirty\[$txtrst\]\$ "

# Use sublime for commands that prompt input (requires sublime and subl being symlinked)
# export EDITOR='subl -w'

####### Plannerstack commands
alias plannerstack_build_client="open http://10.42.2.12:9050/"
alias plannerstack_build_graylog="open http://10.42.3.16:9000/dashboards/542d71f8e4b07cc749537ec4"
alias plannerstack_build_server="ssh c42@10.42.2.12"
alias plannerstack_build="plannerstack_build_wiki && plannerstack_build_graylog && plannerstack_build_client && plannerstack_build_server"

```

## Global hg config

**~/.hgrc**

```
[ui]
ignore = ~/.hgignore
username = FirstName LastName name@calendar42.com
```

**~/.hgignore**

```
syntax: glob

.gitignore
node_modules
.c9revisions
.DS_Store
Thumbs.db

*.pyc
*.pyo
*.pyd

# C extensions
*.so

# Packages
*.egg
*.egg-info
.idea
dist
build
eggs
parts
bin
var
sdist
develop-eggs
.installed.cfg
lib
lib64
include
man
__pycache__

# Installer logs
pip-log.txt

# Unit test / coverage reports
.coverage
.tox
nosetests.xml

# Translations
*.mo
```

# Ubuntu kickstart %post

%post
##achter grond C42
mkdir /home/background
chown -R nobody /home/background
wget --directory-prefix=/usr/share/backgrounds http://res.cloudinary.com/hrscywv4p/image/upload/c_limit,f_auto,h_540,q_80,w_720/v1/252744/Calendar42_icon_u0aiwr.png

yes "yes"|wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
yes "yes"|add-apt-repository -y ppa:tortoisehg-ppa/releases
yes "yes"|add-apt-repository "deb http://archive.canonical.com/ubuntu/ $(lsb_release -sc) partner"

sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'

apt-get update -y
apt-get upgrade -y
apt-get dist-upgrade -y
apt-get check
ubpt-get autoclean -y
apt-get autoremove -y
aptitude install ubuntu-desktop -y
apt-get install xorg gnome-core gnome-system-tools gnome-app-install -y
apt-get install ubuntu-session -y
apt-get install git -y
yes "yes" |git clone https://accict:MwHjD5x-TBWAjUZ@github.com:/calendar42/developer-guide
echo "Last change ca6d563011036d1e9365abcff325df0ec22d8094" /




apt-get install ubuntu-session -y
apt-get install python-pip -y
apt-get vim -y
apt-get install node -y
apt-get install gksu -y
apt-get install meld  -y
apt-get install slack -y
apt-get install Pidgin -y
apt-get install Terminator -y
apt-get install Diodon -y
apt-get install openssl libcurl3 libxml2 libssl-dev libxml2-dev libcurl4-openssl-dev pinentry-curses xclip -y
apt-get install libxss1 libappindicator1 libindicator7 -y
apt-get install google-chrome-stable -y
apt-get install mercurial tortoisehg -y
apt-get install skype -y
apt-get install virtualenvwrapper -y

##/usr/share/gnome-background-properties/ubuntu-wallpapers.xml

##toevoeging
##repository
yes "yes"|add-apt-repository ppa:kilian/f.lux
wget -O - https://www.hipchat.com/keys/hipchat-linux.key | apt-key add -
echo "deb http://downloads.hipchat.com/linux/apt stable main" > \
  /etc/apt/sources.list.d/atlassian-hipchat.list
yes "yes"|apt-add-repository ppa:paolorotolo/android-studio
yes "yes"|add-apt-repository ppa:webapps/preview
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" >>/etc/apt/sources.list.d/pgdg.list
yes "yes"|apt-add-repository ppa:mercurial-ppa/releases
yes "yes"|add-apt-repository ppa:chris-lea/node.js

apt-get update
##flux https://justgetflux.com/linux.html
apt-get install fluxgui -y
##lastpass cli lpass
wget https://launchpad.net/ubuntu/+archive/primary/+files/lastpass-cli_0.5.0-1_amd64.deb
dpkg -i lastpass-cli_0.5.0-1_amd64.deb

##subline
wget http://c758482.r82.cf2.rackcdn.com/sublime-text_build-3083_amd64.deb
dpkg -i sublime-text_build-3083_amd64.deb

##Hipchat
apt-get install hipchat -y

##Top Programming Fonts
curl -L https://github.com/hbin/top-programming-fonts/raw/master/install.sh | bash

##pycharm
wget -q -O - http://archive.getdeb.net/getdeb-archive.key
sh -c 'echo "deb http://archive.getdeb.net/ubuntu trusty-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
apt-get update
##apt-get install pycharm -y hier moeten nog wat yes states bij
apt-get install pycharm --force-yes -y
##android-studio
apt-get install android-studio -y

##IntelliJ

yes "yes"|add-apt-repository ppa:webupd8team/java &&
apt-get update &&
yes "yes"|apt-get install oracle-java7-installer &&
echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections &&
update-java-alternatives -s java-7-oracle &&

wget -O /tmp/intellij.tar.gz http://download.jetbrains.com/idea/ideaIC-12.0.4.tar.gz &&
tar xfz /tmp/intellij.tar.gz &&
cd idea-IC-123.169/bin &&
./idea.sh

##mysql
##apt-get install mysql-server -y
echo "mysql-server-5.5 mysql-server/root_password nopass root" | debconf-set-selections
echo "mysql-server-5.5 mysql-server/root_password_again nopass root" | debconf-set-selections
apt-get -y install mysql-server-5.5

##postgresql
apt-get install postgresql-9.4 pgadmin3 postgresql-contrib -y

##poedit
apt-get install poedit -y

##meld
apt-get install meld -y

##Chrome Extension
##/usr/bin/google-chrome --load-extension=<path to extension directory>

##npm
apt-get install npm -y

##grunt

apt-get install nodejs -y
npm install -g grunt-cli

##ruby

apt-get install ruby-full -y

##cordova
npm install -g cordova

##chromium-browser
apt-get install chromium-browser -y

##ADT
##http://techtach.com/2014/05/install-android-sdkadt-bundle-on-ubuntu/ (moet nog in het script verwerkte worden)


##apache2
apt-get install apache2 -y


##gitg
apt-get install gitg -y


##background
echo "$(cat /etc/hostname | sed 's/^...//') ALL=(ALL)       NOPASSWD: ALL " >>/etc/sudoers
echo "accict ALL=(ALL)       NOPASSWD: ALL " >>/etc/sudoers
echo "Last change ca6d563011036d1e9365abcff325df0ec22d8094" >> /home/background/git_versie
dpkg -i /sublime-text_build-3083_amd64.deb
wget --directory-prefix=/usr/share/backgrounds http://res.cloudinary.com/hrscywv4p/image/upload/c_limit,f_auto,h_540,q_80,w_720/v1/252744/Calendar42_icon_u0aiwr.png
echo "gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/Calendar42_icon_u0aiwr.png" >>/etc/profile.d/C42-background.sh
echo "sudo apt-get install xbacklight -y" >>/etc/profile.d/C42-background.sh
echo "sudo xbacklight -set 100" >>/etc/profile.d/C42-background.sh
echo "sudo rm -f /etc/profile.d/C42-background.sh" >>/etc/profile.d/C42-background.sh

reboot


