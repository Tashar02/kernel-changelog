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

**v2.1 - 17/07/2025**

* Fix kernel panic caused by kshrinkd by temporarily moving slab shrinkers out of kshrinkd and getting rid of it (until we get a solution).

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
* Add back necessary input listeners for Goodix touchscreen driver.
* Fix some GCC warnings.
* Disable unused L2TP.
* Upstream KernelSU to rsuntk/KernelSU.
* Switch to scope-minimized manual KernelSU hooks.
* Implement an LTO-specific version of READ_ONCE() that provides acquire semantics.
* Disable wakeup_irq if port is closed for msm_geni_serial.
* Add some missing mm reverts for PSI.
* Add support for Userfaultfd GC (ROM requires `ro.dalvik.vm.enable_uffd_gc=True` in system.prop).

**v1.0 - 04/03/2025**

* Rebase the kernel on the CLO tag `LA.UM.9.14.r1-25800-LAHAINA.QSSI15.0`.
* Add exFAT driver.
* Add a custom haptic_hv driver (thanks to Divyanshu-Modi).
* Debloat Wi-Fi drivers.
* Import Xiaomi changes while minimizing unnecessary code.
* Port the FocalTech 3680 touchscreen driver from ruby-s-oss.
* Debloat defconfig.
* Set Westwood as the default TCP congestion control algorithm.
* Set LZ4 as the default zram compression algorithm.
* Update dtc to upstream version `v1.7.0-60-g95c74d7`.
* Optimize various compiler-specific instructions.
* Fix all KASAN warnings.
* Fix multiple memory leaks.
* Optimize memory and string utility functions.
* Fix various compiler warnings.
* Improve graphics rendering performance.
* Switch to SBalance instead of msm_irqbalance.
* Backport Binder from msm-5.15.
* Add support for Fuse Passthrough.
* Set the default I/O scheduler to SSG.
* Add HPB driver for SK Hynix UFS variants (8/256 GB).
* Upstream UFS to msm-5.10.
* Update LZ4 to v1.9.4 with V8 ASM decompression acceleration.
* Upstream multiple Qualcomm OSS drivers (thanks to Divyanshu-Modi).
* Align inline encryption for UFS with the upstream version.
* Backport zsmalloc from mainline.
* Backport zram from mainline.
* Hardcode zram size to 4GB.
* Upstream uid_sys_stats to android-mainline.
* Optimize F2FS's garbage collector.
* Remove excessive debugging bloat.
* Fix and silence excessive spam in dmesg.
* Remove CAF's tracing from EXT4 and F2FS.
* Switch to stack memory and kmem cache usage in multiple drivers to minimize dynamic memory allocation.
* Mitigate msm-5.4's memory management issues.
* Backport scheduler from msm-5.15.
* Backport RCU from msm-5.10.
* Recalculate the energy model manually using CoreMark.
* Add Capacity Aware Superset Scheduler.
* Backport EEVDF from mainline.
* Set s2idle as the default sleep state instead of deep suspend.
* Enforce WFI idle state when the screen is on.
* Enable threaded NAPI for IPA.
* Add KernelSU-Legacy (fork by rsuntk), which is disabled by default in the repository.
