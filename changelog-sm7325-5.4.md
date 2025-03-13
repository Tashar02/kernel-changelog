## Build Information

```
Kernel: Scarlet
Type: Stable
Devices: POCO X5 Pro / Redmi Note 12 Pro Speed (redwood)
Compiler: Eva GCC 15.0.1 with Eva Binutils (GNU ld) 2.44.50
Compiler specific optimization: DCE and GCC LTO
Kernel Source: https://github.com/Atom-X-Devs/scarlet_xiaomi_sm7325.git
Kernel Branch: redwood
```
## Instructions for using the kernel source

### Branch
```
redwood: Includes the stable release of each update.
staging: An experimental branch that is NOT recommended for use until it has been merged into the 'redwood' branch.
```

### Defconfig
```
xiaomi-qgki_defconfig and redwood.config
```

## Flashing Process

* Reboot to recovery, connect to adb and `adb sideload Scarlet-*.zip` from platform-tools.
* Alternatively, use Franco Kernel Manager's built-in flasher to flash the kernel (requires root). 
* After flashing, unlock the device and let it idle for 2-3 minutes to allow Android processes to properly initialize before using it.

## Changelogs

**v1.1 - 14/03/2025**

* Reset CLO tag for fw-api to `LA.UM.9.14.r1-25500-LAHAINA.QSSI15.0` to fix VoWiFi.
* Added back necessary input listeners for Goodix touchscreen driver.
* Fixed some GCC warnings.
* Disabled unused L2TP.
* Upstreamed KernelSU to rsuntk/KernelSU.
* Switched to scope-minimized manual KernelSU hooks.
* Implemented an LTO-specific version of READ_ONCE() that provides acquire semantics.
* Disabled wakeup_irq if port is closed for msm_geni_serial.
* Added some missing mm reverts for PSI.
* Added support for Userfaultfd GC (ROM requires `ro.dalvik.vm.enable_uffd_gc=True` in system.prop).

**v1.0 - 04/03/2025**

* Rebased the kernel on the CLO tag `LA.UM.9.14.r1-25800-LAHAINA.QSSI15.0`.
* Added exFAT driver.
* Added a custom haptic_hv driver (thanks to Divyanshu-Modi).
* Debloated Wi-Fi drivers.
* Imported Xiaomi changes while minimizing unnecessary code.
* Ported the FocalTech 3680 touchscreen driver from ruby-s-oss.
* Debloated defconfig.
* Set Westwood as the default TCP congestion control algorithm.
* Set LZ4 as the default zram compression algorithm.
* Updated dtc to upstream version `v1.7.0-60-g95c74d7`.
* Optimized various compiler-specific instructions.
* Fixed all KASAN warnings.
* Fixed multiple memory leaks.
* Optimized memory and string utility functions.
* Fixed various compiler warnings.
* Improved graphics rendering performance.
* Switched to SBalance instead of msm_irqbalance.
* Backported Binder from msm-5.15.
* Added support for Fuse Passthrough.
* Set the default I/O scheduler to SSG.
* Added HPB driver for SK Hynix UFS variants (8/256 GB).
* Upstreamed UFS to msm-5.10.
* Updated LZ4 to v1.9.4 with V8 ASM decompression acceleration.
* Upstreamed multiple Qualcomm OSS drivers (thanks to Divyanshu-Modi).
* Aligned inline encryption for UFS with the upstream version.
* Backported zsmalloc from mainline.
* Backported zram from mainline.
* Hardcoded zram size to 4GB.
* Upstreamed uid_sys_stats to android-mainline.
* Optimized F2FS's garbage collector.
* Removed excessive debugging bloat.
* Fixed and silenced excessive spam in dmesg.
* Removed CAF's tracing from EXT4 and F2FS.
* Switched to stack memory and kmem cache usage in multiple drivers to minimize dynamic memory allocation.
* Mitigated msm-5.4's memory management issues.
* Backported scheduler from msm-5.15.
* Backported RCU from msm-5.10.
* Recalculated the energy model manually using CoreMark.
* Added Capacity Aware Superset Scheduler.
* Backported EEVDF from mainline.
* Set s2idle as the default sleep state instead of deep suspend.
* Enforced WFI idle state when the screen is on.
* Enabled threaded NAPI for IPA.
* Added KernelSU-Legacy (fork by rsuntk), which is disabled by default in the repository.
