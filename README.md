#nAOSP 7.1.1 for Sony Xperia S and Acro S

near AOSP ROM 7.1.1
The purpose of this ROM is to provide support for Xperia Acro S

##Build

```
repo init -u https://github.com/hitman-xda/android_manifest -b master
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch aosp_hikari-userdebug

make otapackage
```

##Rebase issue for manifest

```
cd .repo/manifests
git rebase --abort
git reset --hard origin/nAOSP-7.1.1
cd -

```


##Jack Xmx issue

```
out/host/linux-x86/bin/jack-admin stop-server
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"
out/host/linux-x86/bin/jack-admin start-server

make otapackage
```
