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

## Install AOSP source files
- Follow official documentation [Link](https://source.android.com/setup/start)

## Adaptation to phone target
- Look on your phone the build number: ie Pixel 3 => QQ2A.200305.002
- Get the 'Driver Binaries for Nexus and Pixel Devices' files:
-    'google_devices-blueline-qq2a.200305.002-Ocd2f1f1.tgz'   =>   vendor image   =>   Google
-    'qcom-blueline-qq2a.200305.002-bb1bc1fd.tgz'   =>   GPS, audio, camera...   =>   Qualcomm
- Extract the 2 files .sh (right click -> extract...)
- Put the 2 files .sh at the root (for us: 'Documents/aosp_build')
- Use the terminal and go to the root (gotoa)
 `./extract-google-devices-blueline.sh`
 `./extract-qualcom-blueline.sh`

## Compilation

- Command (perhaps not necessary) :
repo init -u https://android.googlesource.com/platform/manifest -b android-10.0.0_r39
- Command : source build/envsetup.sh

| Command | Description |
| ------- | ----------- |
| make clobber | delete previous compiled files |
| lunch | lunch |
| 3 | Pixel 3 |
| m | make compilation|

- After a long time, you may have that kind of message:
- #### build completed successfully (05:45:48 (hh:mm:ss)) ####
