# Kernel Changelog

## 20210809

Changelog based on human brain :

- Use proton clang
- enable as many LLVM flags compiler as possible

<details>
<summary>List</summary>
AR=llvm-ar
NM=llvm-nm
OBJCOPY=llvm-objcopy
OBJDUMP=llvm-objdump
STRIP=llvm-strip
</details>

- update source to BUC1
- properly enable simple_lmk
- mbcache: Speed up cache entry creation
- set optimzied compiler to little cluster core

Changelog based on commit :

<details>
 <summary>Changelog</summary>

```
16583eae1c40 Revert "selinux: Relocate ss_initialized and selinux_enforcing to separate 4k"
175e32982ae9 Makefile: Optimize for sm8150's Kryo 485 CPU setup
036ac03493e0 kbuild: Disable stack conservation for GCC
0a2625829141 msm/sde/rotator: Remove unneeded PM QoS requests
d04d21772483 drm/msm/sde: Remove unneeded PM QoS requests
cae9116ed4c2 irqchip/gic-v3: Remove pr_devel message containing smp_processor_id()
8754bc781a2a mbcache: Speed up cache entry creation
080c0be868d2 pinctrl: msm: Remove explicit barriers from mmio ops where unneeded
45a0a134429c locking/rwsem: Don't hog RCU read lock while optimistically spinning
79fff6c36222 locking/mutex: Don't hog RCU read lock while optimistically spinning
e6499a9aafa0 arm64: Allow IPI_WAKEUP to be used outside of the ACPI parking protocol
1b6596576942 qos: Don't disable interrupts while holding pm_qos_lock
74352244c58e iommu: msm: Rewrite to improve clarity and performance
62c7e1698702 iommu: arm-smmu: fix check for need for preallocate memory
20cab04d9b71 iommu: arm-smmu: Preallocate memory for map only on failure
eea8a9c02a59 f2fs: Force strict fsync mode
38f42673c1b6 scatterlist: Don't allocate sg lists using __get_free_page
522e973655ca mm: kmemleak: Don't die when memory allocation fails
877277113205 msm: kgsl: Don't allocate memory dynamically for drawobj sync structs
67e0f0ffda96 msm: kgsl: Don't try to wait for fences that have been signaled
c19b6d5f209d cpuidle: lpm-levels: Remove debug event logging
6a808da49f87 dma-buf/sync_file: Speed up ioctl by omitting debug names
2c63a01b140c qos: Don't allow userspace to impose restrictions on CPU idle levels
c05b0f807c5d cpuidle: lpm-levels: Allow exit latencies equal to target latencies
b15ad05a3600 msm: kgsl: Remove sync fence names
ec9044758be4 msm: kgsl: Remove POPP
02093ea49338 msm: kgsl: Wake GPU upon receiving an ioctl rather than upon touch input
88792db68c42 cpufreq: Kill userspace CPU boosting entirely
e2a93c6cee33 msm: kgsl: Increase worker thread priority
79527d1e4045 defconfig: enable simple_lmk
859940c76419 mm: vmpressure: Don't export tunables to userspace
2a0e9fbe771e simple_lmk: Update Kconfig description for VM pressure change
f274473e9acb simple_lmk: Add !PSI dependency
cbf870a91c52 simple_lmk: Print a message when the timeout is reached
d3a0a105caf1 VFS: use synchronize_rcu_expedited() in namespace_unlock()
bdcabf841008 simple_lmk: Remove unnecessary clean-up when timeout is reached
2184db0d5f4b simple_lmk: Hold an RCU read lock instead of the tasklist read lock
3ce08e896f82 mm: Don't stop kswapd on a per-node basis when there are no waiters
48645a446823 simple_lmk: Consider all positive adjs when finding victims
4ce076b60a73 mm: vmpressure: Ignore allocation orders above PAGE_ALLOC_COSTLY_ORDER
c7609fb3ab9d mm: Don't warn on page allocation failures for OOM-killed processes
7c2bc094d22f mm: Adjust tsk_is_oom_victim() for Simple LMK
afdbe44df49f mm: vmpressure: Don't cache the window size
b00a59befb11 mm: vmpressure: Interpret zero scanned pages as 100% pressure
3e2cbde37721 mm: vmpressure: Don't exclude any allocation types
494a51408ebb simple_lmk: Update adj targeting for Android 10
472de8283d58 simple_lmk: Use vmpressure notifier to trigger kills
afccf2ce36cd mm: Stop kswapd early when nothing's waiting for it to free pages
19942336e8ca simple_lmk: Include swap memory usage in the size of victims
b895af0b30dd simple_lmk: Relax memory barriers and clean up some styling
0da42041f005 simple_lmk: Place victims onto SCHED_RR
97b6d8b93dbe simple_lmk: Add a timeout to stop waiting for victims to die
70d6aa042059 simple_lmk: Ignore tasks that won't free memory
0529c616a423 simple_lmk: Simplify tricks used to speed up the death process
d78e830238b6 simple_lmk: Report mm as freed as soon as exit_mmap() finishes
801dcb37e84e simple_lmk: Mark victim thread group with TIF_MEMDIE
89b888dfc6f7 simple_lmk: Disable OOM killer when Simple LMK is enabled
58ba6d00d986 simple_lmk: Print a message when there are no processes to kill
f8646ca223fe simple_lmk: Remove compat cruft not specific to 4.14
1c901e1d01e7 simple_lmk: Update copyright to 2020
45f09f8db341 simple_lmk: Don't queue up new reclaim requests during reclaim
d694fbfb7b12 simple_lmk: Increase default minfree value
2d8d4730d0e6 simple_lmk: Clean up some code style nitpicks
c5f01e3f015f simple_lmk: Make reclaim deterministic
7ee375930c24 simple_lmk: Fix broken multicopy atomicity for victims_to_kill
c736829602a9 simple_lmk: Use proper atomic_* operations where needed
4c0deb4dee3d simple_lmk: Remove kthread_should_stop() exit condition
27c9781dc0db simple_lmk: Fix pages_found calculation
01053a176444 simple_lmk: Introduce Simple Low Memory Killer for Android
1d78f9012b0e defconfig: enable overlayFS
22306023fa38 input: y771: Use KEY_POWER for DT2W/AOT * based on r5q changes
053690c390a8 battery: sec_battery: export {CURRENT/VOLTAGE}_MAX to sysfs
99e1d7904c89 Add toggle for disabling newly added USB devices
12bd8ae231f0 drivers: usb: add separated Samsung MTP option Do not use this on samsung roms
df69642ae2eb ARM64: configs: Enable support for sdFAT filesystem  * Update default charset for FAT to UTF-8, matching sdFAT's default.
8a0bc1944389 fs: sdfat: Add MODULE_ALIAS_FS for supported filesystems
9eaed5ecf545 fs: sdfat: Add config option to register sdFAT for VFAT
c1bc735f2d6b fs: sdfat: Add config option to register sdFAT for exFAT
21b13f418468 cpuidle: don't disable cpuidle when entering suspend
7c6409636722 cpuidle: Do not select menu and ladder governors
b9360a0e9499 Makefile.lib: Stop calling size_append
de7aa098e02e drivers: gpu/msm: further disable coresight
439e5f124d64 drivers: gpu/msm, esoc: allow CORESIGHT to be disabled
11626ab7f07d defconfig: Adjust qcacld configuration
5f6fdfa29d33 qcacld: nuke Kconfig-based configuration entirely
4714ba617cd5 qcacld: Disable build timestamp
08b383ff4a46 qcacld: always force user build
2edae03d8d4b qcacld: check if auth_tag_len exceeds sizeof(hash)
f25bede868f6 ARM64: configs: Disable redundant Spectre variant 2 mitigations
4ca24958409a techpack: audio: Remove build timestamp injection
fe439690c2ac defconfig: disable unnecessary modules
8552f84d4005 net: make knox function toggle-able
893fbf6f8741 defconfig: disable samsung's specific security features
5226f2ac11ff defconfig: built overlay_dt
1689f31fca31 defconfig: use savedefconfig
a3eb6a5b90dd scripts: silence dtc warnings
6d428da62b71 msm: cleanup: struct gsi_wdi2_channel_scratch2_reg
3a21a45403a3 msm: cleanup: union gsi_wdi_channel_scratch3_reg
70d3689f3c52 msm: cleanup: struct gsi_mhi_channel_scratch
8d82c9d7f31a msm: cleanup: union gsi_evt_scratch
41265696cbfb msm: cleanup: struct gsi_wdi3_channel_scratch2_reg
8de67ed97946 msm: cleanup: union gsi_channel_scratch
1e7257075af8 Revert "scripts: gcc-wrapper: Use wrapper to check compiler warnings"
01d82478d8a2 Android.bp: remove it prevent confliction with other kernel tree
bc4f7ef04f23 Source A715FXXU3BUB5 CIS_RR caf tag LA.UM.9.1.r1-07300-SMxxx0.0
```

</details>

## 20210331

- Initial release
