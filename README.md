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
 PATH=/home/<username>/Android/Sdk/platform-tools:$PATH
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
repo init -u https://android.googlesource.com/platform/manifest -b android-10.0.0_r30
- Command : source build/envsetup.sh

| Command | Description |
| ------- | ----------- |
| make clobber | delete previous compiled files |
| lunch | lunch |
| 3 | Pixel 3 |
| m | make compilation|

- After a long time, you may have that kind of message:
- [100% 88813/88813] Target vbmeta image: out/target/product/blueline/vbmeta.img
- #### build completed successfully (05:45:48 (hh:mm:ss)) ####

## Emulation

- ~/Documents/aosp_build$ emulator
- emulator: ERROR: Can't get kernel version from the kernel image file: '/home/<username>/Documents/aosp_build/prebuilts/qemu-kernel/arm64/ranchu/kernel-qemu'

- In Android Studio (lunch with studio command), install un AVD (Android Virtual Device) ie.Pixel 3 API 29

- You have to use the qemu-kernel for x86_64 made in the aosp_build/prebuits folder

- Make a bash file 'emulator_toto_1':
```bash
- /home/<username>/Android/Sdk/emulator/emulator -avd Pixel_3_API_29 -partition-size 2048 -kernel /home/<username>/Documents/aosp_build/prebuilts/qemu-kernel/x86_64/current/kernel-qemu2 -system /home/<username>/Documents/aosp_build/out/target/product/blueline/system.img -initdata /home/<username>/Documents/aosp_build/out/target/product/blueline/userdata.img -sdcard /home/<username>/.android/avd/Pixel_3_API_29.avd/sdcard.img -verbose
```

- Lunch :
- ~/Documents/aosp_build$ ./emulator_toto_1
- and the simulated phone may appear

