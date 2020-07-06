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
- Add libncurses5 librairy (Ubuntu 20)

If error at compilation with Ubuntu 2020, check [this](https://groups.google.com/forum/#!msg/android-building/BaGEAAzcsyA/lbcRNhZXAQAJ) link
Add librairy with this command : `sudo apt install libncurses5`

## Compilation

- Command perhaps not necessary :
repo init -u https://android.googlesource.com/platform/manifest -b android-10.0.0_r39

| Command | Description |
| ------- | ----------- |
| make clobber | delete previous compiled files |
| lunch | lunch |
| 3 | Pixel 3 |
| m | make compilation|
