## Build Information

```
Kernel: Scarlet
Type: Stable
Devices: POCO X5 Pro / Redmi Note 12 Pro Speed (redwood)
Compiler: Eva GCC 16.0.0 with Eva Binutils (GNU ld) 2.44.50
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

**v2.0 - 16/07/2025**

* Rebase kernel on `LA.UM.9.14.r1-26100-LAHAINA.QSSI15.0` with wifi, audio, camera, dataipa, datarmnet, display, video driver from `LA.UM.9.14.r1-26000-LAHAINA.QSSI15.0`.
* Fix broken VoWiFi originating from fw-api.
* Redo old mm patchset.
* Fix build with GCC LTO that requires 4-way interleave using PMULL for crc32.
* Switch back to deep suspend since s2idle causes black screen of death and reboot when device enters deep sleep when battery is less than 5%.
* Set ssg's max available ratio back to 100 again.
* Enable UFS clock scaling.
* Fix timestamps on panic logs.
* Fix console-ramoops generation.
* Fix kernel panic caused by a race in __power_supply_changed_work().
* Fix kernel panic caused by subsystem crash.
* Fix stack depot reaching limit capacity by set __exception_irq_entry with __irq_entry as a default.
* Update lz4 to v1.10.0.
* Backport zsmalloc from mainline.
* Backport zram from mainline.
* Backport timer from linux-6.7.
* Upstream binder to android-mainline.
* Upstream EEVDF to mainline.
* Upstream scheduler to `android14-6.1`.
* Fix the usage of CPUFREQ_NEED_UPDATE_LIMITS in sched.
* Port tapered DVFS headroom from gs201 and fine-tune it.
* Disable big tasks rotation since it negatively affects the active load balancer.
* Fix tons of uninitialized variables, NULL pointer dereferences and OOB accesses in qcacld-3.0 and qcacmn.
* Add support for NCM USB tethering.
* Fix clkgating for ufs.
* Fix refount leaks in of/irq.
* Fix a deadlock in USB dwc3 core.
* Discard contiguous clusters in batches in exfat.
* Increase priority of glink worker thread.
* Avoid race for intent lock in glink.
* Fix various data races in swap code.
* Introduce __cma_alloc API to avoid prolonged stalls resulting from blocking pages.
* Remove __GFP_NORETRY flag from kgsl_system_alloc_pages.
* Fix system crash caused by KASAN with a dirty hack.
* Introduce Simple Low Memory Killer, fine-tune it and disable PSI.
* Rewrite goodix fingerprint driver to improve clarity and performance.
* Update rq stats way less frequently.
* Rework GPU target frequency calculation for high refresh rates to reduce overly aggresive frequency requests in some games.
* Use pipes rather than temporary files for intermediate steps.
* Disable cleancache since we don't have a proper backened or any usability.
* Upstream KernelSU to rsuntk/KernelSU at commit fea6b79743809.

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
