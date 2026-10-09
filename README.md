# Linux Native - Dell Wyse 3040

## Background

My previous experience with Linux mainly came from personal experimentation, everyday usage, and working with WSL (Windows Subsystem for Linux) when using Docker on Windows.

However, i now want to take a more systematic approach to learning Linux. My goal is to develop a comprehensive and solid foundation in Linux system adminstration, understand how Linux works under the hood, and eventually build my own Linux-based tools and ecosystem.

I started this project in October 2026, during my fourth year at university. I consider Linux proficiency an essential part of my technical skill set, both for upcoming internship applications and for more advanced engineering roles in the futures.

## Motivation - Why the Dell Wyse 3040?

I previously ran Ubuntu on my PC. At that time, i often installed monitoring tools such as htop or btop, along with various other utilities, without fully understanding how they worked.

My usual approach was simple: run a command, check whether it succeeded, and move on. I rarely investigated the underlying mechanisms or consider whether the installed tools were actually neccessary.

Over time, I realized that i had been installing unnecessary packages and consuming system resources for tasks that could often be accomplished using standard Linux utilities.

This led me to the Dell Wyse 3040, a low-powered thin client with limited CPU, memory, and storage resources. Its hardware constraints make it a suitable environment for learning how to manage packages, inspects storage, monitor resources usage, and understand the Linux system at a deeper level.

Rather than relying on additional software for everytask, i want to explore what Linux already provides.

I chose a minimal installation of Debian 13 (Trixie), although the specific Debian version was not a critical factor. Other Debian releases could have served the same purpose.

## Project Goals

Through this project, i aim to:
- Build a structured and comprehensive understanding of Linux system adminstration.
- Investigate Linux internals using standard command-line utilities and system interfaces.
- Understand how the kernel, processes, memory, storage, filesystems, and services interact.
- Learn to manage limited hardware resources efficiently.
- Develop my own tools to simplify system setup, adminstration, and monitoring.
- Document my experience, observations, and technical findings for future reference.

## Test Environment

| Component | Specification|
| --- | ---|
| Device | Dell Wyse 3040 Thin Client |
| CPU | Intel Atom x5-Z8350 |
| RAM | 2GB |
| Storage | 8 GB eMMC |
| OS | Debian GNU/Linux 13 (Trixie) |
| Architecture | x86_64 |

## Learing Roadmap

This is an initial roadmap based on my current understanding of Linux. Topics, priorities, and scope may change as i progress through the project.

### Phase 1 - System Fundamentals
- [x] System identification and hardware inspection
- [x] CPU architecture and topology
- [x] Memory management and swap
- [ ] Storage, partitions, and filesystems
- [ ] Processes, threads, and scheduling

### Phase 2 - System Adminstration
- [ ] Users, groups, and permissions
- [ ] Package management
- [ ] Systemd and service management
- [ ] Boot process and system initialization
- [ ] System logging and troubleshooting

## Phase 3 — Performance and Monitoring
- [ ] CPU utilization and load average
- [ ] Memory pressure and swap activity
- [ ] Disk I/O and filesystem performance
- [ ] Process monitoring and resource consumption
- [ ] Bottleneck identification and analysis

### Phase 4 — Linux Networking
- [ ] Network interfaces and configuration
- [ ] IP addressing and routing
- [ ] DNS and network troubleshooting
- [ ] Firewalls and network security
- [ ] Network monitoring and diagnostics

### Phase 5 — Linux Internals
- [ ] Kernel architecture and system calls
- [ ] Virtual memory and memory management
- [ ] Process scheduling and context switching
- [ ] Linux virtual filesystems (/proc, /sys, /dev)
- [ ] Device drivers and hardware interaction

### Phase 6 — Automation and Tool Development
- [ ] Shell scripting and automation
- [ ] Building custom monitoring tools
- [ ] Automating system configuration
- [ ] Developing Linux utilities
- [ ] Testing and documenting custom tools

## Repository Structure

```text
linux-native-wyse3040/
├── README.md
├── reports/
│   ├── 01-system-overview.md
│   └── ...
├── tools/
│   └── ...
└── scripts/
    └── ...
```

### How to Navigate

- **`README.md`** — Project introduction, objectives, environment, and learning roadmap.
- **`reports/`** — Technical reports documenting experiments, observations, explanations, and findings.
- **`tools/`** — Custom Linux utilities developed during the project.
- **`scripts/`** — Scripts for system administration and automation.

Start with [01 — System Overview](reports/01-system-overview.md) for the initial inspection of the Dell Wyse 3040.

> **Note:** The repository is a work in progress. Some directories are planned and may not exist yet. Its structure will evolve as the project develops.