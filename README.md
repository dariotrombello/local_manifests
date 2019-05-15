# Manifests for dotOS Pie (a3xelte)

## 1. Set up all basic things
Set up a build environment based on this guide: https://wiki.lineageos.org/devices/bacon/build

## 2. Initialize the source
Execute this command from your folder where you want to have your dotOS build files placed. I recommend having it in /home/\<username\>/android/dot-p
```bash
repo init -u git://github.com/DotOS/manifest.git -b dot-p
```

## 3. Sync the sources
Then run the following command to download the source
```bash
repo sync
```

## 4. Clone the repository to the right path
```bash
git clone https://github.com/dariotrombello/local_manifests .repo/local_manifests
```

## 5. Sync again
Also sync the device specific sources
```bash
repo sync
```

## 6. Get ready to build
```bash
source build/envsetup.sh
```

## 7. Start building
```bash
lunch dot_a3xelte-userdebug
mka bacon
```

## Additional things
You also need following picks to get a usable experience on the phone due the Hardware Composer (HWC) has some issues. Create a script in the root directory of 
dot-p source called whatever you want to, paste in the code below, give the right permissions with `chmod +x <nameofthescript>.sh` and run it. Note that you need to 
execute it everytime you resync the sources. This is only a temporary solution and may be get fixed better in the future. Credits for it go to 
danwood76.

```bash
(cd hardware/interfaces; curl https://github.com/TeamNexus/android_hardware_interfaces/commit/4fa05e6ab7a1219dd33432abe653ad027fd93413.patch | git am)
(cd frameworks/native; curl https://github.com/TeamNexus/android_frameworks_native/commit/aa1fe72ba54b8f1ff94cbf0dea65bd463cd9010f.patch | git am)
```
