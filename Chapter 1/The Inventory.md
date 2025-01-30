## Disclaimer

This book is a documentation of my personal homelab setup and the experiences I've had while building and managing it.

This homelab is all about **using open-source software that is free to use**. As part of this philosophy, I will be **completely avoiding Microsoft Windows**. Every operating system I use will be a **Linux variant**, whether it's **Debian, Arch, or Alpine Linux**.  

The goal is to create an environment that is **fully open-source, lightweight, and efficient**, without relying on proprietary systems. This ensures maximum flexibility, better security, and full control over the software stack. If you're used to Windows, don't worry—Linux offers powerful alternatives for almost every use case, and this book will guide you through them.

### Hardware I have at my place

| Device       | Model                   | Units |
| ------------ | ----------------------- | ----- |
| Raspberry Pi | Raspberry Pi 4B         | 3     |
| Laptop       | Lenovo ThinkBook 14-IML | 1     |
| Laptop       | Dell Inspiron 3410      | 1     |
| Router       | TP-Link Archer A9       | 1     |
|              |                         |       |

Now, this is not a high-end shiny setup by any means. In fact, it is a **lightweight and budget-friendly** homelab built with hardware that I already had available. The Lenovo and Dell laptops are not powerful workstations—they are just **old machines which were lying around with crappy performance on latest Microsoft Windows that I repurposed** for learning, experimenting, and running lightweight workloads.  

The goal of this homelab is not to create a high-performance data center but to **explore open-source tools, self-hosted services, and cloud integrations** using minimal resources. If you have different hardware, don’t worry—**the concepts in this book will work on a variety of setups**, whether you're using virtual machines, cloud instances, or other single-board computers.

## Hardware Specifications

### Raspberry Pi 4 Model B

| Component    | Specification                                                       |
| ------------ | ------------------------------------------------------------------- |
| CPU          | Broadcom BCM2711, Quad-Core Cortex-A72 (ARM v8) 64-bit SoC @ 1.5GHz |
| RAM          | 8GB LPDDR4                                                          |
| GPU          | Broadcom VideoCore VI                                               |
| ARCHITECTURE | aarch64/arm based                                                   |

### Lenovo ThinkPad
| Component    | Specification                        |
| ------------ | ------------------------------------ |
| CPU          | Intel i3-10110U (4 cores) @ 4.100GHz |
| RAM          | 8GB                                  |
| GPU          | Intel CometLake-U GT2 [UHD Graphics] |
| ARCHITECTURE | x86                                  |

### Dell Inspiron 3410
| Component    | Specification                                 |
| ------------ | --------------------------------------------- |
| CPU          | 11th Gen Intel i3-1115G4 (4 cores) @ 4.100GHz |
| RAM          | 8GB                                           |
| GPU          | Intel Tiger Lake-LP GT2 [UHD Graphics G4]     |
| ARCHITECTURE | x86                                           |


However, you do not need to have the exact same hardware to follow along.

The focus of this book is on the **software, configurations, and methodologies** rather than specific hardware choices. Many of the concepts and tools discussed here can be adapted to different se\tups, whether you're using cloud instances, virtual machines, or other single-board computers.

Feel free to use this book as a guide, but always customize your setup based on your own requirements, budget, and available resources. The best homelab is the one that works for you!
