# Информация о версиях

Ноут: macOS Sequoia 15.7.4
VirtualBox: 7.2.4 r170995 (Qt6.8.0 on cocoa)

Проблем с установкой не было никаких.

# Настройки Virtualbox

```
RAM:		4 GB
Storage:	25 GB
CPU:		2 cores
```

# Процессор

## `cat /proc/cpuinfo`

Вывод:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 158
model name	: Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
stepping	: 10
microcode	: 0xfa
cpu MHz		: 2602.790
cache size	: 12288 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch pti fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt arat md_clear flush_l1d arch_capabilities
bugs		: cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit srbds mmio_stale_data retbleed gds bhi spectre_v2_user its
bogomips	: 5205.58
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 158
model name	: Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
stepping	: 10
microcode	: 0xfa
cpu MHz		: 2602.790
cache size	: 12288 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch pti fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt arat md_clear flush_l1d arch_capabilities
bugs		: cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit srbds mmio_stale_data retbleed gds bhi spectre_v2_user its
bogomips	: 5205.58
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:


``` 

# Память

## `free -h`

Вывод:

``` 
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       1.0Gi       1.6Gi        34Mi       1.4Gi       2.8Gi
Swap:             0B          0B          0B
```

# Сеть

## `ip a`

Вывод:

``` 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:e5:31:c0 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute enp0s3
       valid_lft 85880sec preferred_lft 85880sec
    inet6 fd17:625c:f037:2:108:6889:efaa:dc26/64 scope global temporary dynamic 
       valid_lft 86322sec preferred_lft 14322sec
    inet6 fd17:625c:f037:2:a00:27ff:fee5:31c0/64 scope global dynamic mngtmpaddr 
       valid_lft 86322sec preferred_lft 14322sec
    inet6 fe80::a00:27ff:fee5:31c0/64 scope link 
       valid_lft forever preferred_lft forever
```

# Хранилище

## `df -h`

Вывод:

``` 
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           392M  1.5M  391M   1% /run
/dev/sda2        25G  5.6G   18G  24% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           392M  116K  392M   1% /run/user/1000
```

# ОС и ядро

## `uname -a`

Вывод:

``` 
Linux osman 6.17.0-14-generic #14~24.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jan 15 15:52:10 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

# Виртуальная машина

## `systemd-detect-virt`

Вывод:

``` 
oracle
```

# Полезные команды

Наиболее полезные команды на мой взгляд это команды для просмотра памяти, хранилища и информации о процессоре, потому что удобно видеть всю эту информацию разом. Например, если моросит, узнать что там с оперативкой.


