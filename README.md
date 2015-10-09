AOSP 6.0
========

Build instructions
------------------

Download the AOSP 6.0 sources and sync:

    repo init -u https://android.googlesource.com/platform/manifest -b android-6.0.0_r1
    repo sync

Then add the manifest and sync again:

    mkdir .repo/local_manifests/
    curl https://raw.githubusercontent.com/marshmallow-og/manifest/master/geehrc.xml > .repo/local_manifests/geehrc.xml
    repo sync

Apply a patch required:

    cd frameworks/base
    git fetch https://gerrit.omnirom.org/android_frameworks_base refs/changes/71/14171/1 && git cherry-pick FETCH_HEAD
    cd ../..

Start build:

    source build/envsetup.sh && lunch aosp_geehrc-userdebug
    make otapackage
