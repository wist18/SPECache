# Spectre Attack Implementation code on x86

Spectre attack is proposed by Paul Kocher et. al. in their research paper entitled, Spectre Attacks: Exploiting Speculative Execution at 40th IEEE Symposium on Security and Privacy (S\&P'19) in 2019. This attack exploits un-authorized access to program memery by exploiting branch prediction and using cache-based side channel attack (Flush+Reload) as covert channel. This implmenentation use same code as proposed by authors with some modifications as done by (https://github.com/crozone/SpectrePoC).

## Machine Specifications:

Intel Core i7_12700H CPU @ 3.40GHz
CPU: 10, L1d Cache: 480 KB, L1i Cache : 320 KB L2 Cache : 12.5 MB, L3 Cache : 24 MB
Ubuntu 16.04.3 LTS, Kernel: Linux 4.10.0-28-generic
CPU op-mode(s):        32-bit, 64-bit
Address sizes:         39 bits physical, 48 bits virtual
Byte Order:            Little Endian

## Attack


```
	make
	./spectre 180
```

Default threshold for Flush+Reload is 80 on this attack configurations, where on our machine, it is 180. You should use threshold according to your machine.
