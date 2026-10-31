# OrangeFox Recovery — Android 16

Requires a Linux Android build environment, Git, and [Repo](https://source.android.com/source/using-repo.html).

## Sync

```bash
mkdir orangefox_16
cd orangefox_16
repo init -u https://gitlab.com/OrangeFox/Manifest.git -b fox_16.0
repo sync
```

Add `--depth=1` to `repo init` for a smaller shallow checkout.

## Build for Mondrian

Use Bash:

```bash
export FOX_BUILD_DEVICE=mondrian
source build/envsetup.sh
lunch twrp_mondrian-bp2a-eng
mka recoveryimage
```

Output: `out/target/product/mondrian/recovery.img`.

## Other devices

Add the device tree and its dependencies to a local manifest, then run `repo sync`.
Set `FOX_BUILD_DEVICE` and use `lunch twrp_<device>-bp2a-eng`.
Build `recoveryimage`, `bootimage`, or `vendorbootimage` according to the device's
recovery partition layout.
