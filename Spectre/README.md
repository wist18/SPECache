# Spectre Attack Explained

Spectre is a type of security vulnerability that affects modern computer processors, including those made by Intel, AMD, and ARM. It was first publicly disclosed in January 2018 and is caused by a design flaw in the way that CPUs execute instructions. At a high level, Spectre takes advantage of a performance optimization feature in modern CPUs known as speculative execution. Speculative execution is a technique that allows a processor to start executing instructions before it is certain that they will actually be needed. This can help improve overall performance by reducing the amount of time that the CPU spends idle, waiting for instructions to be completed.

The problem with speculative execution is that it can also introduce security vulnerabilities. Specifically, Spectre allows an attacker to trick a processor into speculatively executing malicious code, even if that code would not normally be allowed to run. By doing so, an attacker can potentially gain access to sensitive data, including passwords, encryption keys, and other confidential information.

There are two main variants of the Spectre vulnerability: Spectre Variant 1 (CVE-2017-5753) and Spectre Variant 2 (CVE-2017-5715). Variant 1 is caused by a flaw in the way that processors handle branch predictions, while Variant 2 is caused by a flaw in the way that processors handle indirect branches.

Variant 1 (also known as Bounds Check Bypass) exploits the fact that modern CPUs use branch prediction to try to predict the outcome of conditional statements in code, such as if-else statements. The CPU will then execute instructions based on this prediction, even before it is known whether the condition is true or false. If the CPU predicts that the condition will be true, it will speculatively execute the instructions inside the if statement, even if those instructions would not normally be executed if the condition were false. However, if the prediction turns out to be wrong, the CPU will discard the speculatively executed instructions and resume execution at the correct point. Unfortunately, the discarded instructions may still leave behind traces in the CPU's cache and registers, which can be exploited by an attacker. By carefully crafting code that causes the CPU to speculatively execute instructions that access sensitive data, an attacker can then use a side-channel attack to read the data from the cache.

Variant 2 (also known as Branch Target Injection) exploits the fact that modern CPUs use branch prediction to try to predict the target address of indirect branches. An indirect branch is a jump instruction that jumps to a memory location determined at runtime, rather than a fixed memory address. The CPU will try to predict the target address of the jump based on past behavior, and then speculatively execute instructions at that location before the target address is known. An attacker can then use a side-channel attack to manipulate the CPU's branch prediction and cause it to speculatively execute code at an arbitrary location. By carefully controlling the instructions that are speculatively executed, an attacker can gain access to sensitive data that would not normally be accessible.

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
