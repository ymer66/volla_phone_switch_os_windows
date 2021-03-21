# Install Sailfish to Volla Phone under Windows 10

## VollaOS to Sailfish OS ##

- download Adroid Platform Tools for Windows and extract the ZIP file [https://developer.android.com/studio/releases/platform-tools](https://developer.android.com/studio/releases/platform-tools)
- download the Google USB Driver and extract the ZIP file [https://developer.android.com/studio/run/win-usb](https://developer.android.com/studio/run/win-usb)
- Download Sailfish for Volla [https://gitlab.com/sailfishos-porters-ci/yggdrasil-ci/-/jobs/artifacts/master/download?job=run-build-lvm](https://gitlab.com/sailfishos-porters-ci/yggdrasil-ci/-/jobs/artifacts/master/download?job=run-build-lvm%5C%5C)

    and unzip the files under "sfe-yggdrasil\Sailfish_OS in the same directory as the Android Platform Tools

- Enable Developer Mode on the Volla Phone: Settings → System → Advanced → About phone → tap 7 times on Build number until you get "You are now a developer".
- Enable "OEM unlocking" and "USB debugging" under the "Developer options": Settings → Advanced → Developer options → turn on "OEM unlocking" and turn on "USB debuggging"
- Put the phone in "Fastboot" by turning the phone off. Connect the USB cable while holding the volume up on the phone. Once you see the menu use volume up do bring the arrow to "Fastboot mode" and push volume down to select. You will receive confirmation for "→FASTBOOT mode..."
- Open the Windows Device Manager and look for "Other devices", "Android". Right click and choose "Update driver", "Browse my computer for drivers", "Let me pick from a list of available drivers on my computer", "Show all devices", "Have Disk...", navigate to the directory where you have unzipped the Google USB Driver and select "Android ABD Interface". Finish installation.
- Start a command line and navigate to where you unzipped the Android Platform tools and the Sailfish files and run:

```bash
fastboot devices
```

You must see the phone listed in fastboot mode: "GS290xxxxxxxx  fastboot"

- Unlock with bootloader with:

```bash
fastboot flashing unlock
```

confirm on the phone with volume up.

## SailfishOS to VollaOS (untested) ##

- item from Sailfish install
- Download TWRP https://volla.tech/filedump/twrp.img
- Download latest VollaOS https://ota.volla.tech/builds
- Start phone in fastboot and execute:
fastboot recovery twrp.img
- Start phone in recovery mode
- Select Advanced ADB Sideload / wipe both
adb sideload volla-9.0-....


- Run following commands:

```bash
fastboot flash boot hybris-boot.img
fastboot flash userdata sailfish.img001
fastboot flash logo logo.bin
fastboot flash lk lk-yggdrasil.img
fastboot reboot
```
