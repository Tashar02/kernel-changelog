## Build Information

```
Kernel: Scarlet-X Kernel
Type: Stable
Devices: Mi A2, Mi 6X, Redmi Note 5 Pro & Redmi Note 6 Pro
Compiler: Neutron Clang 16
Compiler specific optimization goodies: Clang LTO (Full), Polly Optimizer Flags & LLD 16
Kernel Source: https://github.com/Atom-X-Devs/android_kernel_xiaomi_scarlet
Kernel Branch: default-QTI, default-QPNP
```
## Instructions for using the kernel source

```
If you want to inline Scarlet-X with your rom, kindly use the default branch or ask the maintainer (@Tashar02) about it. Use the dedicated wayne-perf_defconfigs for different camera blobs support.

wayne-perf_defconfig -> newcam
wayne-old-perf_defconfig -> oldcam
wayne-oss-perf_defconfig -> osscam
```

## Flashing Process

* Reboot to recovery.
* Backup your `boot` image (so that you can restore it later to go back to your previous kernel in case something goes wrong).
* Flash the kernel zip.
* Reboot to system.
* Let the device be idle for few mins and use the device.

## Changelogs

**v7.0 - 01/12/2022**

* Merged tag `v4.19.267` from ACK's android-4.19-stable branch.
* Merged tags `LA.UM.11.2.1.r1-02500-sdm660.0` & `LA.UM.10.2.1.r1-04900-sdm660.0` from CodeLinaro's msm-4.19 branch treewide, including wifi drivers.
* Upstreamed F2FS from ACK's `upstream-f2fs-stable-linux-4.19.y` branch.
* Upstreamed exFAT from linux-exfat-oot.
* Updated Kprofiles to upstream version `5.0.0`.
* Added backported Jump Label patches from k5.4 (backported by UtsavBalar1231).
* Enabled Jump Label.
* Added backported locking patches from k5.4 (backported by UtsavBalar1231).
* Synced block patches with ChromeOS-4.19.
* Backported latest zRAM patches from mainline.
* Imported ARM64 v8 ASM LZ4 decompression acceleration.
* Reduced LZ4 memory usage to 1KB.
* Backported latest random patches from mainline.
* Backported i2c patches from mainline and msm-5.10.
* Removed pm_wakeup_event() support at qrtr.
* Updated DTC to upstream version `v1.6.1-63-g55778a0`.
* Fixed some minor issues at Makefile.
* Removed extra reserved space in cpu_hwcaps*.
* Disabled debug at sdcardfs.
* Removed duplicate buff_err usage at camera drivers.
* Fixed uninitialized spinlock usage at qcacld-3.0.
* Marked availability of FSA4490 i2c node as unlikely.
* Replaced stub codec with TAS2557 codec.
* Dropped Atheros WLAN card support.
* Switched back to using string argument comparison method to fix modem crash.
* Tuned Simple Low Memory Killer (SLMK).
* Reverted some scheduler patches.
* Brought minor improvements to WALT.
* Increased accuracy of cpuidle predictions.
* Refactored goodix and fpc fingerprint sensors.
* Improved charging speed and temperature limits.
* Cleaned up some Xiaomi changes at power and batterydata drivers.
* Slightly cleaned up the DTS.
* Improved haptic feedback.
* Removed unused reserved memory for wlan_msa_guard.
* Configured hw based attention light.
* Added support for dynamic partition.

**v6.0 - 27/09/2022**

* Merged tag `v4.19.259` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.10.2.1.r1-04600-sdm660.0` from CodeLinaro's msm-4.19 branch.
* Upstreamed F2FS from ACK's `upstream-f2fs-stable-linux-4.19.y` branch.
* Backported RW Semaphore from Mainline.
* Fixed a memleak at DesignWare USB3 DRD Core.
* Disabled preemption before request_fn calls as per jasmine-q-oss.
* Riced sdcardfs from Moto Kernel.
* Fixed pageblock heuristic of mm.
* Backported some zsmalloc and zram patches from mainline.
* Updated LZ4 module to `v1.9.4`
* Enabled timer migration.
* Improved the scheduler.
* Improved software interrupts.
* Synced schedhorizon with latest schedutil codes.
* Added a whitelist for devfreq governors at KGSL.
* Removed unused debug codes from lpm-levels.
* Backported binder from ACK's android14-5.15 branch.
* Micro-optimized compiler specific instructions.
* Reverted a potential call trace causing use-after-free fix at FUSE.
* Enabled AICL trip via HDC from smb2 to fix fast charging.
* Imported Xiaomi changes for pstore from jasmine-q-oss.
* Aborted reinitialization of failed ramoops.
* Brought improvements to the ispif and cpp timeout of camera.

**v5.0 - 05/08/2022**

* Merged tag `v4.19.254` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.10.2.1.r1-04000-sdm660.0` from CodeLinaro's msm-4.19 branch.
* Upstreamed F2FS from ACK's `upstream-f2fs-stable-linux-4.19.y` branch.
* Fixed data corruption at certain apps.
* Redid the FUSE backports.
* Revised commit "irqchip: Conditionally compiled SDM660 specific GIC chip data for MPM".
* Backported RNG from mainline.
* Disabled SRANDOM and switched to HW_RANDOM.
* Brought minor improvements to scheduler.
* Fixed big cluster shutting down below 10% battery.
* Backported some devfreq patches from msm-5.10.
* Switched to latest implementation to configure USB data.
* Micro optimized DesignWare USB3 DRD Core.
* Prevented reordering of some I/O writes.
* Backported latest LZ4 patch from mainline.
* Backported latest WireGuard patch from mainline.
* Micro optimized compiler instructions.
* Updated DTC to upstream version v1.6.1-44-ged31080.
* Backported some mm patches from mainline.
* Backported some KGSL patches from msm-5.10.
* Brought improvements to F2FS.
* Improved kernel logs dumping during panic.
* Backported some pstore patches from mainline.
* Micro optimized interrupt path of FPC fingerprint driver.
* Riced smb1351 charger driver from Moto Kernel.
* Backported binder from android12-5.10-lts.
* Removed more debugs from binder.
* Converted some locks to raw spin locks.
* Micro optimized and fixed wakeup event logic for Novatek Panels.
* Debloated QCACLD.
* Debloated defconfigs.
* Debloated the clock drivers.
* Compiled out useless MDSS PLLs and adreno drivers.

**v4.0 - 08/06/2022**

* Merged tag `v4.19.246` from ACK's android-4.19-stable branch.
* Forbade userspace init from messing with I/O scheduler and load scale of WALT.
* Removed alarmtimer codes from QTI QMI Rmnet Helpers.
* Backported some smp2p patches from msm-5.4.
* Brought improvements to watchdog and process freezing.
* Limited concurrency of workqueues freeing buffers asynchronously at ION.
* Backported some memory management patches from mainline.
* Set ZSTD compression level to 2.
* Switched back to LZ4 as default zram compression algorithm.
* Debloated the defconfig further.
* Switched to step-wise thermal governor.
* Backported some thermal core driver patches from mainline and msm-5.4.
* Brought some improvements to the scheduler.
* Reverted some problematic commits.
* Set performance mode by default at kprofiles.
* Brought some improvements to Berkeley Packet Filter.
* Conditionally compiled SDM660 specific GIC chip data for MPM.
* Silenced many uneeded logspams.
* Fixed some warnings from the compiler and sparse.
* Fixed a memory leak at dmaengine.
* Passed some new feature modifiers to -march parameter at Makefile.
* Dropped WQ_HIGHPRI from kgsl-workqueue.
* Dropped round-robin scheduling for kgsl worker thread.
* Updated Embedded Trace Macrocell IDs from sdm660-coresight for coresight placeholder.
* Fixed dead mic and speaker audio during calls.
* Fixed invalid inode logspam from FUSE.

**v3.0 - 30/04/2022**

* Merged tag `v4.19.240` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.10.2.1.r1-03600-sdm660.0` CodeLinaro's msm-4.19 branch treewide, including wifi and audio drivers.
* Backported some FUSE patches from mainline.
* Backported new WireGuard patches from mainline.
* Rebased the kernel source.
* Enabled GENERIC_FIND_FIRST_BIT.
* Improved integer sqrt speed.
* Re-calculated legacy energy model using freqbench.
* Removed useless userspace spam from net.
* Fixed tons of memory leaks.
* Disabled Qualcomm Thermal Limiter.
* Reverted "sched: modify capacity_margin for SDM636".
* Reverted "sched: separate capacity margin for boosted tasks".
* Skipped superfluous acquire barrier in ttwu.
* Disabled CPUFreq times driver.
* Reverted "block: Queue requests on their origin CPU".
* Reverted "block: Do not wake the request CPU if idle".
* Limited max active to 1 for the buffer freeing workers at ION.
* Increased F2FS's checkpoint interval to 200s.
* Upgraded srandom to upstream version 1.41.0.
* Enabled Ultra High Speed mode at srandom.
* Re-enabled PSI & MEMCG.
* Dropped Simple Low Memory Killer in favor of LMKD.
* Reverted memory management upstreams by CodeLinaro honoring Google.
* Implemented Multigenerational LRU from ChromeOS Kernel.
* Implemented KernelSpace Profile Mode (Visit support group to know how to use it).
* Rolled back some scheduler backports from k5.4.
* Added global atomic count to scm call at memlat.

**v2.0 - 25/03/2022**

* Merged tag `v4.19.236` of ACK's android-4.19-stable branch.
* Upstreamed F2FS from ACK's `upstream-f2fs-stable-linux-4.19.y` branch.
* Disabled Spectre-BHB mitigation.
* Reverted "mm: Perform PID map reads on the little CPU cluster".
* Disabled zram writeback.
* Reverted "input: fingerprint: Affine IRQ to the perf CPU cluster"
* Replaced flex array usage with kvmalloc at selinux.
* Reworked on the FUSE Passthrough backports.
* Converted printk -> pr_* at FUSE.
* Enabled Garbage Collector for user space wakeup sources.
* Separated capacity margin for boosted tasks.
* Added SDM636's modified capacity margin by @Reinazhard (works good on SDM660 too).
* Fixed lavender's xiaomi longcheer imports (Now kernel can be compiled for lavender without any build errors).
* Omitted CR 2040904 fixes for Schedhorizon.
* Brought some improvements to the scheduler from k5.4.
* Reduced verbosity of logging.
* Enabled Ftrace (as per Android 12's needs).
* Added the revised warning fix at zstd (from @cyberknight777).
* Removed URLs from LINUX_COMPILER macro.

**v1.0 - 02/03/2022**

* Rebased kernel off `LA.UM.10.2.r1-03300-SDM660.0` from CodeLinaro's msm-4.19 branch.
* Merged tag `v4.19.231` of ACK's android-4.19-stable branch.
* Imported Android-12 Wifi Drivers based on `LA.UM.10.2.r1-03300-SDM660.0` CLO tag.
* Merged f2fs-stable of jaegeuk/f2fs-stable.
* Added exFAT driver.
* Debloated wifi drivers.
* Cleaned up overlayed dtsi.
* Enabled BCL Peripheral.
* Optimized bootargs.
* Calculated legacy energy model using freqbench.
* Added support for New, Old and OSS camera blobs.
* Optimized audio-kernel.
* Enabled QPNP and QTI haptics on dedicated builds.
* Imported Novatek touchscreen driver from CAF and optimized it.
* Configured wakeup IRQ properly.
* Optimized fpc and goodix fingerprint drivers.
* Optimized ION.
* Backported exFAT patches from mainline.
* Set GPU idle timeout to 64 ms.
* Removed auditing.
* Debloated defconfig.
* Set westwood as default TCP congestion algorithm.
* Added power efficient workqueues treewide.
* Relaxed and disabled some unwanted wakelocks.
* Removed unnecessary HIGHPRI flag from many workqueues.
* Optimized EXT4.
* Removed CAF's tracings from EXT4 & F2FS.
* Introduced rapid GC for F2FS.
* Moved many driver inits to async and sync probes.
* Fixed tons of logspams at dmesg.
* Silenced many unwanted logs.
* Killed tons of debug bloats.
* Updated dtc to upstream version v1.6.1-30-g45f3d1a.
* Backported WireGuard from mainline.
* Added Backported Clang's Link Time Optimization (LTO) patches from mainline (Backported by @OGIndian).
* Optimized compiler specific instructions for SDM660.
* Added Polly Optimizer Flags.
* Optimized inlining.
* Lower kernel gzip compression to fastest.
* Added some fq_codel backports (from @Panchajanya1999).
* Added SRANDOM.
* Added BFQ upstream patches (from @Reinazhard) & enabled BFQ.
* Backported some Kyber patches from mainline & set as default I/O Scheduler.
* Backported kallsyms from mainline.
* Backported scripts/setlocalversion from mainline.
* Backported Fuse Passthrough from linux-5.10.
* Resolved many compiler given warnings.
* Backported ZRAM from mainline.
* Add Backported ZSTD patches from mainline (Backported by @ElectroPerf & @cyberknight777) and set as default ZRAM compression algorithm.
* Enabled BPF JIT.
* Added and tuned Simple Low Memory Killer (SLMK).
* Backported binder patches from mainline.
* Added cpuidle, kgsl, mm, usb, mdss optimizations (from @kerneltoast).
* Added cpumasks for big, LITTLE CPU clusters.
* Added bi-cluster API to affine IRQs and kthreads to fast CPUs.
* Affined unbound workqueues to little CPUs by default.
* Removed L2PC PM QoS from kgsl.
* Removed PM QoS from vidc, audio & qcacld.
* Added devfreq boost.
* Optimized the fair scheduler.
* Enabled Window Assisted Load Tracking (WALT).
* Optimized Schedutil CPU governor and set by default.
* Added schedhorizon CPU governor, synced with latest Schedutil changes and tuned for efficiency.
* Added some dynamic memory allocation avoidance commits by @kerneltoast.
