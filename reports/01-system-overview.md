# 01 — System Overview

## 1. Objective

This report performs an initial inspection of Debian Linux running on a Dell Wyse 3040.

The goal is to understand the system using native Linux tools rather than immediately installing additional monitoring software.

The scope includes:

- system identity
- operating system
- Linux kernel
- CPU
- memory
- storage
- filesystems

Networking is excluded from this report because IP addresses, routes, gateways, and similar information depend partly on the external network environment rather than the Linux system itself.

---

# 2. System Identity

## `hostnamectl`

```bash
hostnamectl
```

Output:

```text
Static hostname: wyse3040
Icon name: computer-desktop
Chassis: desktop
Operating System: Debian GNU/Linux 13 (trixie)
Kernel: Linux 6.12.111+deb13-amd64
Architecture: x86-64
Hardware Vendor: Dell Inc.
Hardware Model: Wyse 3040 Thin Client
Firmware Version: 1.2.5
```

`hostnamectl` is a systemd utility used to query and change the hostname and related system metadata.

The system currently uses:

```text
Static hostname:    wyse3040
Transient hostname: wyse3040
Pretty hostname:    not configured
```

The three hostname types have different purposes:

- **Static hostname** — persistent system hostname.
- **Transient hostname** — temporary hostname that may be supplied or changed dynamically.
- **Pretty hostname** — human-readable descriptive name.

The machine also has two identifiers:

- **Machine ID** — identifies this Linux installation.
- **Boot ID** — identifies the current boot session and changes after reboot.

---

# 3. Operating System and Kernel

## `uname`

```bash
uname -a
```

Output:

```text
Linux wyse3040 6.12.111+deb13-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.12.111-1 (2026-09-28) x86_64 GNU/Linux
```

Important fields:

```text
Linux                       Kernel name
wyse3040                    Hostname
6.12.111+deb13-amd64        Kernel release
x86_64                      Machine architecture
GNU/Linux                   Operating environment
```

The command:

```bash
uname -v
```

returns build information for the currently running kernel.

---

## `/etc/os-release`

```bash
cat /etc/os-release
```

Relevant values:

```text
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
VERSION_ID="13"
VERSION_CODENAME=trixie
DEBIAN_VERSION_FULL=13.7
```

`/etc/os-release` identifies the Linux distribution installed on the system.

Therefore:

```text
Distribution: Debian GNU/Linux
Version:      13.7
Codename:     trixie
```

---

# 4. CPU

## `lscpu`

```bash
lscpu
```

The processor is:

```text
Intel(R) Atom(TM) x5-Z8350 CPU @ 1.44GHz
```

Main topology:

```text
Architecture:          x86_64
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
```

Therefore:

```text
1 socket
× 4 cores per socket
× 1 hardware thread per core
= 4 logical CPUs
```

The machine has **4 physical cores and 4 logical CPUs**.

There is no SMT/Hyper-Threading configuration where one core exposes multiple hardware threads.

---

# 5. CPU Architecture

```text
Architecture:     x86_64
CPU op-mode(s):   32-bit, 64-bit
```

`x86_64` is the 64-bit extension of the x86 instruction set architecture.

Other common names for the same architecture include:

```text
x86-64
AMD64
amd64
x64
```

The CPU can operate with both 32-bit and 64-bit x86 software.

This should not be confused with the CPU vendor.

For example:

```text
Vendor:       Intel
Architecture: x86_64
```

Intel is the manufacturer, while x86_64 is the instruction set architecture executed by the CPU.

---

# 6. Address Sizes

```text
Address sizes: 36 bits physical, 48 bits virtual
```

These values describe memory addressing capabilities.

## Physical address

A 36-bit physical address space can represent:

```text
2^36 bytes = 64 GiB
```

This is the address space available for physical memory addressing.

It does **not** mean the Wyse contains 64 GiB of RAM.

---

## Virtual address

A 48-bit virtual address space can represent:

```text
2^48 bytes = 256 TiB
```

Programs normally work with virtual addresses.

A simplified translation path is:

```text
Process
   ↓
Virtual Address
   ↓
MMU + Page Tables
   ↓
Physical Address
   ↓
RAM
```

A process identifier such as a PID or TID is unrelated to these memory addresses.

---

# 7. Byte Order

```text
Byte Order: Little Endian
```

Little Endian means that the least significant byte of a multi-byte value is stored at the lowest memory address.

For example:

```text
Value:

0x12345678
```

is stored in increasing memory addresses as:

```text
78 56 34 12
```

This matters when interpreting raw memory, binary file formats, network data, and low-level protocols.

---

# 8. CPU Identification

Relevant values:

```text
Vendor ID:  GenuineIntel
CPU family: 6
Model:      76
Stepping:   4
```

## Vendor ID

`GenuineIntel` is the CPU vendor identifier returned through the x86 CPUID mechanism.

It identifies the CPU vendor, not the exact processor model.

---

## Stepping

Stepping represents a hardware revision of a CPU design.

Two CPUs sold under the same model name may have different stepping revisions if the manufacturer modifies the silicon design.

A newer stepping may contain:

- hardware fixes
- errata fixes
- electrical changes
- manufacturing improvements

Stepping is different from microcode.

A stepping is a silicon revision, while CPU microcode may be updated later through firmware or the operating system.

---

# 9. CPU Frequency

The system reports:

```text
CPU min MHz: 480
CPU max MHz: 1920
```

The CPU can dynamically scale its frequency depending on factors such as:

- system load
- power management
- thermal limits
- CPU governor

The maximum frequency is approximately:

```text
1.92 GHz
```

The minimum reported scaling frequency is approximately:

```text
480 MHz
```

---

# 10. CPU Flags

`lscpu` reports a long list of CPU flags