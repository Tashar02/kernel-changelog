## Build Information

```
Kernel: Scarlet-X Kernel
Type: Stable
Devices: Mi A2, Mi 6X, Redmi Note 5 Pro, Redmi Note 6 Pro & Redmi Note 7
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

* Reboot to recovery
* Backup your `boot` image (so that you can restore it later to go back to your previous kernel in case something goes wrong).
* Flash the kernel zip.
* Reboot to system.
* Let the device be idle for few mins and use the device.

## Changelog

**v4.0 - 08/06/2022**

* Merged tag `v4.19.246` of android-4.19-stable.
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

* Merged tag `v4.19.240` of android-4.19-stable.
* Merged tag `LA.UM.10.2.1.r1-03600-sdm660.0` of CodeLinaro-4.19 treewide, including wifi and audio drivers.
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

* Merged tag `v4.19.236` of android-4.19-stable.
* Upstreamed F2FS from jaegeuk/f2fs-stable.
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

* Rebased kernel off `LA.UM.10.2.r1-03300-SDM660.0`.
* Merged ACK `v4.19.231`.
* Imported S Wifi Drivers based on `LA.UM.10.2.r1-03300-SDM660.0`.
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
* Added srandom.
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
