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



## Developer Package

#### Mac & Ubuntu

| Name 						|  Short Description 	| Version	
| --------					| --------					|-------
| Top Programming Fonts | to look at something nice all day | [latest](https://github.com/hbin/top-programming-fonts)
| PyCharm 					| Python IDE | latest
| IntelliJ 					| Java IDE | latest
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
| Slack client 						| Slack communications
| Ubuntu version | LTS always. All softwares are guaranteed to work. Currently 14.04.2 LTS.  

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
```
