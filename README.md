### Hi there <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="25px">
These are my notes giving various tutorials when using debian linux i.e kali. Most of the instructions can be found online in the official websites or with a little bit of googling.

## Linux Permissions
[User:r/w/x] [group:r/w/x] [everyone:r/w/x]  
■ ■ Read ( r ): 4  
■ ■ Write ( w ): 2  
■ ■ Execute ( x ): 1  
r =4, w =2, and x =1  

### To change the permissions of the previous file based on the formula ( r =4, w =2, and x =1), use this:
User:4+2+1=7; Group:4+2+1=7; Everyone:4
```console
> chmod [permissions numbers] [file name]
> chmod 774 test.sh
```

### giving execute permission to all user groups
```console
> chmod +x test.sh
```


## NMAP
```console
> nmap -sV {target_IP}
```


## Remove entire directory and contents
```console
> sudo rm -rv /path-to-directory
```
***example***
```console
> sudo rm -rv /opt/utorrent-server-alpha-v3_3/ /usr/bin/utserver
```


## Telegram Desktop
### Installation
```console
> sudo apt install snapd
> sudo systemctl start snapd.service
> sudo systemctl enable snapd.service
> sudo snap install telegram-desktop
```
### Running
```console
> snap run telegram-desktop
```
### Uninstall
```console
> sudo snap remove telegram-desktop
```
### Update
```console
> sudo snap refresh telegram-desktop
```


## Installing .tar.gz files in /opt
### Extract into opt
```console
> tar -xzvf /path-to-tar.gz-file -C /opt
```
### Create Symbolic link -- Enables launch from Terminal
```console
> sudo ln -sf -v /opt/extracted-tar-folder/program /usr/bin/program
```
### Create desktop icon
```console
> sudo cp -r -v /opt/extracted-tar-folder/program.desktop /home/s_ntaks/.local/share/applications/
```
### Else Create .desktop file in **/home/s_ntaks/.local/share/applications/**
```console
> sudo subl /home/s_ntaks/.local/share/applications/program.desktop
```
### Removing
```console
> rm -r ~/.config/discord
> sudo rm -rf /usr/bin/Discord
> sudo rm /usr/bin/Discord
> sudo rm /home/s_ntaks/.local/share/applications/discord.desktop
```


## [Github Overview Page (Spice up Profile Page)](https://betterprogramming.pub/3-steps-to-improve-your-github-overview-page-950c64d4d465)
Ways to create an awesome github overview page


## Path to SecLists in kali linux
```console
> ls -lh /usr/share/seclists/Discovery/Web-Content
```


## ffuf - Fuzz Faster U Fool
> ffuf is a fest web fuzzer written in Go that allows typical directory discovery, virtual host discovery (without DNS records) and GET and POST parameter fuzzing.



## [Installing MongoDB on Debian](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/)
### Import public key used by the Package Management System
```console
> wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```
The operation respond with an ```OK```

***However, if you receive an error indicating that*** ```gnupg``` ***is not installed, you can:***
 - Install gnupg and its required libraries using the following command:

```console
> sudo apt-get install gnupg
```

- Once installed, retry importing the key:

```console
> wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```

### Create a ```/etc/apt/sources.list.d/mongodb-org-5.0.list``` file for MongoDB.
```console
> echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```

### Reload local package database
```console
> sudo apt-get update
```

### Install MongoDB packages
```console
> sudo apt-get install -y mongodb-org
```

### Start, Stop, Restart MongoDB
```console
> sudo systemctl start mongod
> sudo systemctl stop mongod
> sudo systemctl restart mongod
```

### MongoDB session
```console
> mongosh
```
