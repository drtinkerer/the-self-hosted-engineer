## Disclaimer

This book is a documentation of my personal homelab setup and the experiences I've had while building and managing it.

This homelab is all about **using open-source software that is free to use**. As part of this philosophy, I will be **completely avoiding Microsoft Windows**. Every operating system I use will be a **Linux variant**, whether it's **Debian, Arch, or Alpine Linux**.

The goal is to create an environment that is **fully open-source, lightweight, and efficient**, without relying on proprietary systems. This ensures maximum flexibility, better security, and full control over the software stack. If you're used to Windows, don't worry—Linux offers powerful alternatives for almost every use case, and this book will guide you through them.

---

## Hardware I Have in My Homelab

| Device       | Model                   | Units |
| ------------ | ----------------------- | ----- |
| Raspberry Pi | Raspberry Pi 4B         | 3     |
| Laptop       | Lenovo ThinkBook 14-IML | 1     |
| Laptop       | Dell Inspiron 3410      | 1     |
| Router       | TP-Link Archer A9       | 1     |

This is **not** a high-end, shiny setup by any means. In fact, it is a **lightweight and budget-friendly** homelab built with hardware that I already had available. The Lenovo and Dell laptops are not powerful workstations—as of 2025, they are like almost 10 year **old machines, so I **repurposed them** for learning, experimenting, and running lightweight workloads.

The goal of this homelab is not to create a high-performance data center but to **explore open-source tools, self-hosted services, and cloud integrations** using minimal resources. If you have different hardware, don’t worry—**the concepts in this book will work on a variety of setups**, whether you're using virtual machines, cloud instances, or other single-board computers.

---

## Hardware Specifications

### Raspberry Pi 4 Model B

| Component    | Specification                                                       |
|-------------|---------------------------------------------------------------------|
| **CPU**     | Broadcom BCM2711, Quad-Core Cortex-A72 (ARM v8) 64-bit SoC @ 1.5GHz |
| **RAM**     | 8GB LPDDR4                                                          |
| **GPU**     | Broadcom VideoCore VI                                               |
| **Architecture** | aarch64 / ARM-based                                            |

### Lenovo ThinkBook 14-IML

| Component        | Specification                        |
| ---------------- | ------------------------------------ |
| **CPU**          | Intel i3-10110U (4 cores) @ 4.100GHz |
| **RAM**          | 8GB                                  |
| **GPU**          | Intel CometLake-U GT2 [UHD Graphics] |
| **Architecture** | x86                                  |

### Dell Inspiron 3410

| Component    | Specification                                 |
|-------------|---------------------------------------------|
| **CPU**     | 11th Gen Intel i3-1115G4 (4 cores) @ 4.100GHz |
| **RAM**     | 8GB                                           |
| **GPU**     | Intel Tiger Lake-LP GT2 [UHD Graphics G4]     |
| **Architecture** | x86 |

---

### Flexibility of Hardware

However, **you do not need to have the exact same hardware to follow along**.

The focus of this book is on **software, configurations, and methodologies** rather than specific hardware choices. Even if you have just a single Linux machine, you can still explore and experiment with many of the concepts covered in this book.

Many of the concepts and tools discussed here can be adapted to different setups, whether you're using **cloud instances, virtual machines, or other single-board computers**.

Feel free to use this book as a guide, but always customize your setup based on your **own requirements, budget, and available resources**. The best homelab is the one that works for you!


---

## Operating System Choices

My homelab runs entirely on **Linux**, with different distributions depending on the hardware. However, **you are free to use any Linux distribution of your choice**. 
Since most of the applications will be running in **Docker containers**, the underlying OS does not significantly impact functionality.

| Device                      | OS Name          | Version / Codename |
| --------------------------- | ---------------- | ------------------ |
| **Lenovo ThinkBook 14-IML** | Debian GNU/Linux | Trixie / Sid       |
| **Dell Inspiron 3410**      | Debian GNU/Linux | 12 (Bookworm)      |
| **Raspberry Pi 4B**         | Debian GNU/Linux | 12 (Bookworm)      |
| **TP Link Archer A9**       | OpenWRT          | 23.05              |

Regardless of your **hardware** or **distribution choice**, the majority of the setups in this book will work as long as you have **a Linux system with Docker**. If you prefer Ubuntu, Arch, Fedora, or any other Linux variant, you should still be able to follow along with minimal adjustments.
To anchor that, I am using Trixie on Lenovo which is unstable. It is currently part of **Debian Testing**, which means it is a **rolling development branch** that eventually becomes the next stable Debian version.

### Why Linux?

- **Open-source & free** – No licensing costs, complete transparency, and community-driven development.  
- **Lightweight & customizable** – Can be stripped down to essential components, making it ideal for homelabs.  
- **Security & stability** – Linux is known for its strong security model and rock-solid stability.  
- **Perfect for self-hosting** – Most open-source software runs natively on Linux.  
- **Strong CLI & automation** – Shell scripting, package managers, and systemd services make automation seamless.  

If you're new to Linux, don’t worry! This book will guide you through the essentials, and you’ll pick things up as you go.

---

### Hardware Independence

One of the core principles of this homelab is **hardware independence**. Even if you have just a **single Linux machine**, you can still experiment with many of the concepts covered in this book. The majority of services and applications will run inside **Docker containers**, meaning the underlying OS and hardware don't matter as much. 

This makes it easy to:
- Deploy services on any Linux system, whether it's a laptop, desktop, or cloud instance.  
- Recreate the same setup on different hardware with minimal modifications.  
- Upgrade or switch distributions without breaking existing services.  

If you're running a different Linux distribution, you might need to tweak **package installation commands**, but everything else should work the same.

---

