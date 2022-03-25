## Build Information

```
Kernel: Scarlet-X Kernel
Type: Stable
Devices: Mi A2, Mi 6X, Redmi Note 5 Pro, Redmi Note 6 Pro & Redmi Note 7
Compiler: Atom-X Clang 15
Compiler specific optimization goodies: Clang LTO (Full), Polly Optimizer Flags & LLD
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

**v1.0 - 02/03/2022**

* Rebased kernel off LA.UM.10.2.r1-03300-SDM660.0.
* Merged ACK v4.19.231.
* Imported S Wifi Drivers based on LA.UM.10.2.r1-03300-SDM660.0.
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
* Added cpuidle, kgsl, mm, usb, mdss optimizations from @kerneltoast.
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