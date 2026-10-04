# linux-native-wyse3040

Hands-on Linux system exploration using a **Dell Wyse 3040 Thin Client** running **Debian GNU/Linux 13 (trixie)**.

The purpose of this repository is to learn Linux from the system itself: inspect the kernel, CPU, memory, storage, filesystems, processes, services, and other native Linux components using standard command-line tools.

This is not intended to be a collection of command cheatsheets. Each report records what was actually observed on the machine and explains the related Linux concepts.

## Test Machine

- **Device:** Dell Wyse 3040 Thin Client
- **CPU:** Intel Atom x5-Z8350
- **Architecture:** x86_64
- **CPU topology:** 4 cores / 4 threads
- **RAM:** 2 GB
- **Storage:** 8 GB eMMC
- **OS:** Debian GNU/Linux 13 (trixie)
- **Kernel:** Linux 6.12.111+deb13-amd64

## Repository Structure

```text
linux-native-wyse3040/
├── README.md
└── reports/
    └── 01-system-overview.md
```

## Reports

### 01 — System Overview

Initial inspection of the Linux system using:

```bash
hostnamectl
hostname
uname
cat /etc/os-release
lscpu
free
lsblk
df
```

Topics covered:

- system identity and hostname
- operating system and kernel
- CPU architecture and topology
- CPU cache and virtualization
- CPU security mitigations
- RAM and swap
- eMMC layout
- Linux filesystems and mount points

Networking is intentionally outside the scope of the first report. Network interfaces, IP addressing, routing, DNS, and related tools will be explored when networking becomes the actual subject of a later lab.