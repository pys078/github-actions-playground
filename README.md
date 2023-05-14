# github-actions-playground

在这里测试各种github actions

## show-power

看一下github actions提供的虚拟机配置如何

**内存信息**

`free -m`

```
              total        used        free      shared  buff/cache   available
Mem:           6943         602        4016          30        2324        6012
Swap:          4095           0        4095
```

实际内存给了6943MB

swap内存给了4095MB

免费的机器看起来内存已经给了不少了，秒杀大多数VPS了

**硬盘信息**

`df`

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/root       87204404 59394432  27793588  69% /
devtmpfs         3550832        0   3550832   0% /dev
tmpfs            3555312        4   3555308   1% /dev/shm
tmpfs             711064     1120    709944   1% /run
tmpfs               5120        0      5120   0% /run/lock
tmpfs            3555312        0   3555312   0% /sys/fs/cgroup
/dev/loop0         64896    64896         0 100% /snap/core20/1852
/dev/loop2         54528    54528         0 100% /snap/snapd/18933
/dev/loop1         94080    94080         0 100% /snap/lxd/24061
/dev/sda15        106858     6182    100677   6% /boot/efi
/dev/sdb1       14341128  4194336   9396508  31% /mnt
tmpfs             711060        0    711060   0% /run/user/1001
```

整个给了差不多83个G

**CPU信息**

`cat /proc/cpuinfo`

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 85
model name	: Intel(R) Xeon(R) Platinum 8272CL CPU @ 2.60GHz
stepping	: 7
microcode	: 0xffffffff
cpu MHz		: 2593.907
cache size	: 36608 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 21
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology cpuid pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single pti fsgsbase bmi1 hle avx2 smep bmi2 erms invpcid rtm avx512f avx512dq rdseed adx smap clflushopt avx512cd avx512bw avx512vl xsaveopt xsavec xsaves md_clear
bugs		: cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs taa itlb_multihit mmio_stale_data retbleed
bogomips	: 5187.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 46 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 85
model name	: Intel(R) Xeon(R) Platinum 8272CL CPU @ 2.60GHz
stepping	: 7
microcode	: 0xffffffff
cpu MHz		: 2593.907
cache size	: 36608 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 21
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology cpuid pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single pti fsgsbase bmi1 hle avx2 smep bmi2 erms invpcid rtm avx512f avx512dq rdseed adx smap clflushopt avx512cd avx512bw avx512vl xsaveopt xsavec xsaves md_clear
bugs		: cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs taa itlb_multihit mmio_stale_data retbleed
bogomips	: 5187.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 46 bits physical, 48 bits virtual
power management:
```

给了两个vCPU核心

**GPU信息**

`lspci`

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: Microsoft Corporation Hyper-V virtual VGA
```

看起来没有给GPU核心呢？可能是为了防止挖矿？

## ffmpeg-transcode

测试了一下转码和呈递文件，感觉使用github actions转码没啥优势啊

**转码前**

<img width="1072" alt="截屏2023-05-15 02 33 45" src="https://github.com/pys078/github-actions-playground/assets/7541452/34e0a3c4-3fee-4ef3-99ec-f39ca4de28f6">

**转码后**

<img width="1072" alt="截屏2023-05-15 02 31 27" src="https://github.com/pys078/github-actions-playground/assets/7541452/dfd4d9e3-3082-4b49-ba63-1df3e7f4b41d">

**使用github action的转码速度**

<img width="605" alt="截屏2023-05-15 02 37 26" src="https://github.com/pys078/github-actions-playground/assets/7541452/3e9bdf38-416d-4823-8a09-289a407ff8c8">

**使用我的MacBook Air的转码速度**

<img width="682" alt="截屏2023-05-15 02 36 22" src="https://github.com/pys078/github-actions-playground/assets/7541452/c6c4ba5f-3d62-4e45-af54-4e25e5be65db">

比我这i5还要慢，看来github actions只能用作自动化转码服务器来用了
