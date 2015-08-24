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
