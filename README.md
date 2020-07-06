# aosp_build

[Link](https://source.android.com/setup/start) of the official documentation

## Create USB stick with ubuntu
- Install rufus
- Create USB Stick ISO

## Install Ubuntu

## Configure Ubuntu
- Install Android Studio
- Modify the file ~/.bashrc by adding at the end the lines :
 
 ```bash
 alias finder='nautilus --browser .'
 alias goto='cd ~/'
 alias gotod='cd ~/Desktop'
 alias gotow='cd ~/Documents'
 alias gotoa='cd ~/Documents/aosp_build'
 alias studio="~/Documents/android-studio/bin/studio.sh"
    
 PATH=~/Documents/aosp_build/bin:$PATH
```
- Add librairy

If error at compilation with Ubuntu 2020, check [this](https://groups.google.com/forum/#!msg/android-building/BaGEAAzcsyA/lbcRNhZXAQAJ) link
