# android_manifest
AOSP version 11 (Android R) for Khadas vim1s.
- Edited to **not** download darwin prebuilts
- AOSP Source uses revision "android-11.0.0_r46"
- Khadas Source uses revision "khadas-vim1s-r"

Recommended steps:

```
mkdir </path/to/where-ever>
cd $_
repo init -u https://github.com/jake5253/android_manifest -b vim1s -c --no-clone-bundle --no-tags --no-repo-verify
repo sync -n
repo sync -j$(( $(nproc) - 1 )) -l
```
- the `init` line arguments speed up the next step considerably
- `sync -n` only performs network (download) portion of sync
- `sync -l` only performs local (extraction) portion of sync
  - Leaves a core available for other tasks.

```
cd vendor/amlogic/common
git lfs pull
cd -
cd device/khadas
git lfs pull
cd -
```
... i'm just gonna make a script. jeesh!
