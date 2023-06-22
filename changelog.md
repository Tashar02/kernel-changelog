## Build Information

```
Kernel: Scarlet-X Kernel
Type: Stable
Devices: Mi A2, Mi 6X, Redmi Note 5 Pro & Redmi Note 6 Pro
Compiler: Neutron Clang 17
Compiler specific optimization goodies: Clang LTO (Full), Polly Optimizer Flags & LLD 17
Kernel Source: https://github.com/Atom-X-Devs/android_kernel_xiaomi_scarlet
Kernel Branches: a13/dynamic, a13/qti-haptics & a13/qpnp-haptics
```
## Instructions for using the kernel source and choosing the appropriate branch

```
a13/dynamic: Supports dynamic partition, EROFS & qti-haptics.
a13/qti-haptics: Supports qti-haptics.
a13/qpnp-haptics: Supports qpnp-haptics.

• Use the dedicated wayne-perf_defconfig(s) for different camera blobs support on Mi A2 / Mi 6X.

wayne-perf_defconfig -> newcam
wayne-old-perf_defconfig -> oldcam
wayne-oss-perf_defconfig -> osscam

Note: If you have any doubt, ask me (@Tashar02) at https://t.me/AtomX_Discussion.
```

## Flashing Process

* Reboot to recovery.
* Backup your `boot` image (so that you can restore it later to go back to your previous kernel in case something goes wrong).
* Flash the kernel zip.
* Reboot to system.
* Let the device idle for a few mins and use the device.

## Changelogs

**v10.0 - 06/07/2023**
* Merged tag `v4.19.288` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.11.2.1.r1-04100-sdm660.0` from CodeLinaro's msm-4.19 branch treewide, including wifi and audio drivers.
* Backported RCU from linux-5.4.
* Offloaded RCU callback processing from all CPUs.
* Made the RCU grace period workers unbound again.
* Backported some irq_work patches from mainline.
* Backported jump label from mainline.
* Backported latest binder patches from mainline.
* Fixed some UAF, NULL pointer dereference and memory leaks in thermal/core.
* Backported zsmalloc from mainline.
* Merged latest changes for Simple Low Memory Killer (SLMK).
* Eliminated dynamic memory allocation at getcwd() system call in vfs.
* Set LZ4 memory usage conditionally based on EROFS's availability.
* Disabled USB LPM on bus_suspend with ADB.
* Added hibernation support for rtc-pm8xxx.
* Forwardported MSM UART High Speed Serial Driver from linux-[4.4, 4.9, 4.14].
* Fixed incorrect usage of PM QoS requests in camera.
* Optimized memory allocation for small buffers in legacy camera stack.
* Fixed compiler warnings.
* Reverted many useless and faulty patches.
* Reduced freeze timeout to 0.5 seconds at fuse's request_wait_answer().
* Fixed the incomplete cpuidle patchset from dereference23.
* Mirco-optimized the scheduler.
* Fixed cpupri MAX_RT_PRIO evaluation.
* Ensured the minimal frequency is lower than the maximal frequency for ROMs that come with libperfmgr.
* Stopped using WQ_CPU_INTENSIVE for verify_wq in dm-verity.
* Removed PM QoS usage from adsprpc and audio-kernel completely.
* Added missing FM recording mixer setup.
* Reduced lsm-client wakelock to 500ms.
* Fixed incorrect pair of PM operations for ipa_v2.
* Fixed a faulty error handling in msm bus.
* Removed the DISABLE_LTO filtering from vDSO.
* Fixed userspace log filter and silenced some bothersome logs.
* Implemented userspace vibration control for QTI Haptics.
* Fixed and optimized regulators handling in fpc fingerprint driver.
* Fixed fpc fingerprint driver being unable to write to irq sysfs node.
* Fixed placement of always_inline instructions.
* Fixed Global and Indian device variant detection algorithm for the power drivers.
* Removed enforcement of warm reboot.
* Removed useless boot arguments from the kernel cmdline.
* Disabled NAN for qcacld-3.0.
* Disabled media ancillary drivers autoselecting support.
* Disabled media usb bus support.
* Enabled BLAKE2b support.
* Disabled EROFS (for the roms that do not support it).

**v9.0 - 22/04/2023 [EID MUBARAK]**
* Merged tag `v4.19.280` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.11.2.1.r1-03400-sdm660.0` from CodeLinaro's msm-4.19 branch treewide, including wifi and audio drivers.
* Upstreamed exFAT to namjaejeon/linux-exfat-oot.
* Upstreamed Kprofiles to `v5.0.3`.
* Updated DTC to upstream version `v1.7.0-19-g2cdf93a`.
* Fixed remaining compiler warnings.
* Reverted many useless patches.
* Backported latest hwrng patches from mainline.
* Backported latest random patches from mainline.
* Backported latest cpufreq stats patches from mainline.
* Opted for modern assember annotations at some more places.
* Reverted all fuse backports from linux-5.4 except Fuse Passthrough.
* Fixed a call trace caused by a prolonged wait time at fuse's request_wait_answer().
* Implemented high-prio per-CPU kthread workers for EROFS.
* Cleaned up Xiaomi's horrible F2FS changes.
* Switched back to normal memory mode for F2FS.
* Added support to report a fake kernel version to fsck at F2FS.
* Opted for ARM64 v8 ASM to accelerate lz4 decompression treewide.
* Reduced SYN resend delay at TCP.
* Switched to SSD mode and entropy gathering.
* Implemented fast refcount checking.
* Backported latest RW Semaphore patches from mainline.
* Improved locking and relaxed tight loops.
* Micro-optimized the scheduler.
* Micro-optimized the memory management.
* Micro-optimized devfreq framework.
* Mirco-optimized KGSL.
* Removed a pointless DT property aquisition at adsprprc.
* Fixed race conditions at adsprpc and qcacmn.
* Improved camera startup speed.
* Decreased wakeup event duration at smp2p_sleepstate.
* Fixed a NULL pointer exception and many dereferences at USB.
* Fixed a false-positive call trace for IPA v2.
* Optimized Novatek touchpanel and fingerprint drivers further.
* Removed deprecated patches for audio-kernel.
* Built missing audio entries.
* Fixed incorrect jeita fcc ranges.
* Re-calculated legacy energy model using freqbench.
* Dropped useless HDR10 support.
* Dropped unsupported feature modifiers and crypto extensions for SDM660.
* Disabled PPP.

**v8.0 - 11/02/2023**

* Merged tag `v4.19.272` from ACK's android-4.19-stable branch.
* Merged tag `LA.UM.11.2.1.r1-03000-sdm660.0` from CodeLinaro's msm-4.19 branch treewide, including wifi drivers.
* Upstreamed exFAT from linux-exfat-oot.
* Upstreamed Kprofiles from dakkshesh07/Kprofiles.
* Imported mm reverts from Google's Redbull kernel.
* Improved memory management drastically.
* Tuned Simple Low Memory Killer further.
* Backported latest zRAM patches from mainline.
* Backported library optimization patches from mainline.
* Added support for EROFS (Enhanced Read-Only File System).
* Increased LZ4 memory usage to 37 KB again.
* Backported latest kallsyms patches from mainline.
* Patched qcacld-3.0 and qcacmn for Android 13 VTS.
* Fully disabled PM QoS at qcacld-3.0 !CLD_PM_QOS.
* Backported latest binder patches android13-5.10 branch of ACK.
* Reserved caches for small, high-frequency memory allocations.
* Robustified compiler hints.
* Set F2FS uncongestion timeout to 6 ms.
* Set F2FS GC urgent sleep time to 5 ms.
* Removed unneeded dynamic memory allocation at EXT4.
* Improved QoS with Sultan's patches.
* Do not queue everything on system's power efficient workqueue.
* Synced and adapted to floral's devfreq boost.
* Tuned devfreq boosting based on Kprofiles selections.
* Increased scheduler tick rate to 300 Hz.
* Enabled support for NTFS.
* Disabled RAS.
* Disabled ION_POOL_AUTO_REFILL.
* Added support for 32 bit DMA_BUF_SET_NAME ioctl.
* Fixed tons of warnings reported by both Clang and GCC.
* Reverted some redundant commits.
* Fixed qos warning at camera.
* Corrected some GPU frequencies.
* Imported dts for m6100cos battery of lavender.
* Tuned charging speed and temperature limits further.
* Silenced some annoying usb logspams.
* Refactored Xiaomi's thermal changes.
* Fixed cpu limits set current frequency.
* Mirco-optimized the scheduler.
* Removed cpuidle's idle prediction feature.
* Removed cpuidle's sleep bias feature.
* Enforced cpuidle to use WFI only.

**v7.0 - 01/12/2022**

* Merged tag `v4.19.267` from ACK's android-4.19-stable branch.
* Merged tags `LA.UM.11.2.1.r1-02500-sdm660.0` & `LA.UM.10.2.1.r1-04900-sdm660.0` from CodeLinaro's msm-4.19 branch treewide, including wifi drivers.
* Upstreamed F2FS from ACK's `upstream-f2fs-stable-linux-4.19.y` branch.
* Upstreamed exFAT from linux-exfat-oot.
* Updated Kprofiles to upstream version `5.0.0`.
* Added backported Jump Label patches from k5.4 (Backported by UtsavBalar1231).
* Enabled Jump Label.
* Added backported locking patches from k5.4 (Backported by UtsavBalar1231).
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
