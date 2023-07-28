# Overview

This is a WIP manifest file that sets up Lugy's attempt at building a custom AOSP/AAOS build.

Lugy's additions: 
  - buildable automotive and "regular" flavour of android
  - "generalKenobi" - a hello world app designed to test how we build apps
  - fast-dds with dependencies (TBD)
  - a DDS app that talks with a dds network (prototype for car integration) - TBD
  - integration of the above DDS app with VehicleHAL (on AAOS) - TBD

# Building

1. Install repo tool as described [here](https://gerrit.googlesource.com/git-repo#install), follow "manual installation" steps
2. Create and enter the build directory (e.g. ~/AOSP-13-lugy)
3. checkout the repository  
   ```
   ~/.bin/repo init -u https://github.com/stekliPes/lugy-android-manifest.git -b refs/tags/stable
   repo sync

   ```
4. Setup environment
   ```
   . ./build/envsetup.sh
   ```
5. Choose variant to build
   ```
   lunch aosp_lugy_car_x86-eng
     or
   lunch aosp_lugy_x86-eng
   ```
6. Build OS, SDK and emulator image package
   ```
   m
   m sdk sdk_repo
   m emu_img_zip
   ```
   - you might want to add -j4 to the m commands if you keep getting error 137 while building
7. you will find the emulator image that you can add to your android studio at out/target/product/[variant you chose at step 5]/sdk-repo-linux-system-images-eng.[$USER].zip
