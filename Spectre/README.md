# Spectre Attack Explained

Spectre is a type of security vulnerability that affects modern computer processors, including those made by Intel, AMD, and ARM. It was first publicly disclosed in January 2018 and is caused by a design flaw in the way that CPUs execute instructions.

At a high level, Spectre takes advantage of a performance optimization feature in modern CPUs known as speculative execution. Speculative execution is a technique that allows a processor to start executing instructions before it is certain that they will actually be needed. This can help improve overall performance by reducing the amount of time that the CPU spends idle, waiting for instructions to be completed.

The problem with speculative execution is that it can also introduce security vulnerabilities. Specifically, Spectre allows an attacker to trick a processor into speculatively executing malicious code, even if that code would not normally be allowed to run. By doing so, an attacker can potentially gain access to sensitive data, including passwords, encryption keys, and other confidential information.

There are two main variants of the Spectre vulnerability: Spectre Variant 1 (CVE-2017-5753) and Spectre Variant 2 (CVE-2017-5715). Variant 1 is caused by a flaw in the way that processors handle branch predictions, while Variant 2 is caused by a flaw in the way that processors handle indirect branches.

Both variants of Spectre can be difficult to detect and mitigate, as they rely on subtle flaws in the design of modern CPUs. To address these vulnerabilities, software and firmware updates have been released by CPU manufacturers and operating system vendors. These updates include patches that modify the way that processors execute certain instructions and reduce the risk of speculative execution attacks.

However, it's important to note that these updates may come with a performance penalty, as they may require CPUs to execute more instructions in order to properly validate each instruction before executing it. This can result in a slowdown in overall system performance, especially on older or less powerful hardware. As a result, mitigating Spectre is an ongoing process that requires balancing security against performance considerations.

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
