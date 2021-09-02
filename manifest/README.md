# Oneplus 7 | Manifest
<br/>

## Build Instructions with manifest
<br/>

Initialize LineageOS repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u git://github.com/LineageOS/android.git -b lineage-18.1
```
<br/>

Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/daviiid99/device_oneplus_guacamoleb/lineage/manifest/gapps.xml > .repo/local_manifests/gapps.xml
```
<br/>

Download repos:

```
git clone -b lineage https://github.com/daviiid99/device_oneplus_guacamoleb device/oneplus/guacamoleb
git clone https://github.com/LineageOS/android_kernel_oneplus_sm8150 kernel/oneplus/sm8150
git clone https://github.com/yaap/vendor_oneplus vendor/oneplus
git clone -b Rika https://gitlab.com/baalajimaestro/vendor_oneplus_apps vendor/oneplus/apps
git clone https://github.com/LineageOS/android_device_oneplus_sm8150-common device/oneplus/sm8150-common
git clone https://github.com/LineageOS/android_device_oneplus_common device/oneplus/common
```

Sync repo:
```
repo sync
source build/envsetup.sh
```
<br/>

Apply patches:
```
patch -d frameworks/base -p1 < device/oneplus/guacamoleb/Disable_Wallpaper_Zoom.patch #Fixes Android R Wallpaper Zoom
 ```
 <br/>

(Optional) LineageOS Updater app shorcut in drawer
```
mkdir -p out/target/product/guacamoleb/system/product/priv-app
cd out/target/product/guacamoleb/system/product/priv-app
mkdir Up&& cd Up
wget https://github.com/daviiid99/daviiid99/releases/download/honami/Up.apk
cd ../../../../../../../../
```
 <br/>
 
(Optional) Replace Default Wallpaper
```
cd vendor/lineage/overlay/common/frameworks/base/core/res/res/drawable-hdpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-nodpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-sw600dp-nodpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-sw720dp-nodpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-xhdpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-xxhdpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-xxhdpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../

cd drawable-xxxhdpi
rm default_wallpaper.png
wget https://github.com/daviiid99/daviiid99/releases/download/honami/default_wallpaper.png
cd ../../../../../../../../../../
```

<br/>

(Optional) OpenGApps configure source
```
sudo apt install git-lfs
git lfs install
repo forall -c git lfs pull
```
<br/>

Build:
```
brunch guacamoleb
```

<br/>

