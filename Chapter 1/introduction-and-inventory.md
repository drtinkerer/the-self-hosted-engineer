# **Setting the Stage: Infrastructure and Intent**
## 1.0 Introduction: What is Homelab?
A **homelab** is a personal computing environment used for **learning, experimentation, and self-hosting services**. It allows individuals to explore **networking, system administration, containerization, cloud services, and automation** in a controlled environment.  
This book documents my **homelab journey**, covering the hardware I use, the open-source software powering it, and the lessons learned along the way.

## 1.1 Why Build a Homelab?
A homelab serves multiple purposes, from **learning DevOps and cloud technologies** to **self-hosting applications and improving security awareness**. Here are some of the main reasons for building one:

### 1.1.1 Learning and Experimentation
- Test new tools like Kubernetes, Docker, and automation frameworks.
- Experiment with cloud-native technologies without cloud costs.
- Build and break things without affecting production environments.

### 1.1.2 Self-Hosting and Privacy
- Host your own services like Nextcloud, VPNs, and media servers.
- Gain more control over your data and privacy.
- Reduce reliance on proprietary cloud services.

### 1.1.3 Cost-Efficiency
- Use old/spare hardware to create a functional infrastructure.
- Optimize for low-power consumption with Raspberry Pi and laptops.
- Leverage free-tier cloud services to expand capabilities.

## 1.2 Hardware Inventory
My homelab consists of a mix of **single-board computers, old laptops, and networking devices**. Each serves a specific role in the setup.

| Device       | Model                   | Units |
| ------------ | ----------------------- | ----- |
| Raspberry Pi | Raspberry Pi 4B         | 3     |
| Laptop       | Lenovo ThinkBook 14-IML | 1     |
| Laptop       | Dell Inspiron 3410      | 1     |
| Router       | TP-Link Archer A9       | 1     |

### Raspberry Pi 4 Model B
| Component    | Specification                                                       |
| -------------|---------------------------------------------------------------------|
| **CPU**      | Broadcom BCM2711, Quad-Core Cortex-A72 (ARM v8) 64-bit SoC @ 1.5GHz |
| **RAM**      | 8GB LPDDR4                                                          |
| **GPU**      | Broadcom VideoCore VI                                               |
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
| -------------|-----------------------------------------------|
| **CPU**      | 11th Gen Intel i3-1115G4 (4 cores) @ 4.100GHz |
| **RAM**      | 8GB                                           |
| **GPU**      | Intel Tiger Lake-LP GT2 [UHD Graphics G4]     |
| **Architecture** | x86                                       |

This is **not** a high-end setup. It is a **lightweight and budget-friendly** homelab built with hardware that I already had available. The laptops are repurposed for learning, experimenting, and running lightweight workloads. The goal is to **explore open-source tools, self-hosted services, and cloud integrations** using minimal resources. If you have different hardware, don’t worry—**the concepts in this book work on a variety of setups**, whether you're using virtual machines, cloud instances, or other single-board computers.

## 1.3 What Would You Need?
Building a homelab requires a combination of **hardware, cloud services, and essential accounts** for managing automation, security, and remote access.  
Here’s what you’ll need to get started:  
- A **bunch of servers at home** (laptops or Raspberry Pi)
- A **registered domain name** for hosting services
- An **Akeyless.io account** for secrets management
- A **GitHub account** for version control and infrastructure automation
- An **Oracle Cloud account (preferred)** for free-tier cloud resources
- A **Cloudflare account** for DNS and secure remote access

Each component plays a crucial role in ensuring **reliability, security, and scalability**. Let's break them down.

### **1.3.1 Home Servers: Using Laptops as Servers**
When I say **server**, I don’t mean expensive enterprise-grade hardware. Instead, I use **old laptops** that were lying around, turning them into **always-on, remotely accessible machines**.

#### **Why use laptops instead of dedicated servers?**
- **Cost-effective** – Reusing old hardware saves money.
- **Built-in UPS** – Laptop batteries keep them running during power cuts.
- **Silent operation** – Unlike traditional servers, laptops are **quiet and power-efficient**.
- **Sufficient performance** – Mid-range laptops can run **Docker, Kubernetes, and databases** efficiently.

#### **How to make laptops run 24x7 as servers?**
- **Disable sleep mode when the lid is closed** (Linux settings or BIOS).
- **Enable auto-boot after power failure** (BIOS setting).
- **Use Wake-on-LAN (WOL)** to turn them on remotely if needed.
- **Connect them via Ethernet** for stable networking.

These tweaks ensure laptops function as **reliable, low-power servers** for running containers and other services.

### **1.3.2 A Domain Name (Registered and Active)**
To access homelab services remotely, you need a **domain name**. This allows you to use user-friendly URLs instead of dealing with dynamic IP addresses.

#### **Where to get a domain?**
- I use **Cloudflare** to manage my domains.
- You can register one from **Namecheap, Google Domains, Porkbun, or any provider**.

#### **Why is a domain useful?**
- **Enables secure remote access** to self-hosted services.
- **Works with Cloudflare tunnels** to eliminate the need for port forwarding.
- **Simplifies service discovery** within your network.
- **Allows proper SSL/TLS encryption** with Let’s Encrypt.

If you plan on hosting **public-facing applications** or accessing services from outside your home, having a **domain name with Cloudflare DNS** is highly recommended.

### **1.3.3 Akeyless.io Account for Secrets Management**
Managing passwords, API keys, and sensitive configurations manually is **risky**. Instead, I use **Akeyless.io**, a cloud-based **secrets management solution**.

#### **Why use Akeyless?**
- **Stores credentials securely** instead of hardcoding them in config files.
- **Integrates with Kubernetes**, making it perfect for storing **K8s secrets**.
- **Supports Role-Based Access Control (RBAC)** to restrict access.

#### **How I use Akeyless in my homelab?**
- **Secrets are fetched dynamically** by applications instead of storing them in files.
- **External Secrets Operator (ESO)** automatically syncs secrets in Kubernetes.
- Ensures that **no sensitive data is exposed** in Git repositories.

If you’re running multiple services that require authentication, **secrets management is a must**.

### **1.3.4 GitHub Account for Version Control**
I use **GitHub** to store and manage all my homelab configurations, automation scripts, and infrastructure-as-code (IaC).

#### **Why GitHub?**
- **Version control** for configuration files (Docker, Kubernetes, Terraform).
- **GitOps automation** with **ArgoCD** for Kubernetes deployments.
- **CI/CD integration** to trigger automatic updates.

#### **How does GitHub help in my homelab?**
- All **Docker Compose, Kubernetes YAMLs, and automation scripts** are stored in a repository.
- **ArgoCD syncs my Kubernetes resources directly from GitHub**.
- GitHub Actions can **build and deploy** services automatically.

If you're running automated infrastructure, using **GitHub or another Git-based system** is essential.

### **1.3.5 Oracle Cloud Free Tier (Preferred Cloud Provider)**
Even though this is a **homelab**, I still use **cloud services** to offload certain workloads. Oracle Cloud is my **preferred choice** due to its **generous free tier**.

#### **Why Oracle Cloud?**
- **Free forever** VMs with up to **4 cores, 24GB RAM**.
- **Persistent block storage** up to **200GB for free**.
- **Load balancers, databases, and networking included**.

#### **What do I run in Oracle Cloud?**
- **PostgreSQL server** for remote database hosting.
- **NetBird VPN server** for secure remote access.
- **n8n automation server** for workflow automation.
- **Backup services** in case home servers go offline.

#### **Why not AWS, Google Cloud, or Azure?**
- AWS and Google Cloud free tiers are **too limited** for always-on workloads.
- Azure has **restrictive free-tier VM options**.
- Oracle provides the **most generous free compute resources**.

Using Oracle Cloud allows me to **extend my homelab with free cloud resources** while keeping **costs at zero**.

### **1.3.6 Cloudflare for Security and Remote Access**
I use **Cloudflare** to manage my **DNS, security, and remote access**.

#### **How does Cloudflare help my homelab?**
- **DNS Management**: Handles all domains and subdomains.
- **Cloudflare Tunnel**: Securely exposes services without opening router ports.
- **DDoS Protection**: Shields against attacks.

#### **Why use Cloudflare instead of exposing my home IP?**
- Protects against **DDoS attacks**.
- **No need to open router ports**, reducing attack surface.
- **Automatically updates DNS records** if home IP changes dynamically.

Cloudflare is an **essential part of my homelab** for **security, remote access, and reliability**.

## Conclusion
To set up a homelab, you need:  
✅ **Home servers (laptops, Raspberry Pi)**  
✅ **A registered domain name**  
✅ **Akeyless for secure secrets management**  
✅ **GitHub for infrastructure version control**  
✅ **Oracle Cloud for free cloud VMs**  
✅ **Cloudflare for DNS, security, and remote access**

These components work together to create a **reliable, cost-effective homelab** that is fully automated and **securely accessible from anywhere**.

In the next section, we will **begin setting up the base system**, starting with **Linux installation, networking configurations, and security hardening**.

## 1.3 Software Philosophy
However, **you do not need to have the exact same hardware to follow along**. My homelab is built around **open-source software** and **Linux-first principles** to maintain flexibility and cost-efficiency. The focus of this book is on **software, configurations, and methodologies** rather than specific hardware choices. Even if you have just a single Linux machine, you can still explore and experiment with many of the concepts covered in this book.

Feel free to use this book as a guide, but always customize your setup based on your **own requirements, budget, and available resources**. Remember, the best homelab is the one that works for you!

## 1.2 Operating System Choices
My homelab runs entirely on **Linux**, with different distributions depending on the hardware. Most applications will run in **Docker containers**, so the underlying OS does not significantly impact functionality.

| Device                      | OS Name          | Version / Codename |
| --------------------------- | ---------------- | ------------------ |
| **Lenovo ThinkBook 14-IML** | Debian GNU/Linux | Trixie / Sid       |
| **Dell Inspiron 3410**      | Debian GNU/Linux | 12 (Bookworm)      |
| **Raspberry Pi 4B**         | Debian GNU/Linux | 12 (Bookworm)      |
| **TP Link Archer A9**       | OpenWRT          | 23.05              |

Regardless of your **hardware** or **distribution choice**, the majority of the setups in this book will work as long as you have **a Linux system with Docker**. If you prefer Ubuntu, Arch, Fedora, or any other Linux variant, you should still be able to follow along with minimal adjustments.

## 1.2.1 Why Linux?
- **Open-source & free** – No licensing costs, complete transparency, and community-driven development.
- **Lightweight & customizable** – Can be stripped down to essential components, making it ideal for homelabs.
- **Security & stability** – Linux is known for its strong security model and rock-solid stability.
- **Perfect for self-hosting** – Most open-source software runs natively on Linux.
- **Strong CLI & automation** – Shell scripting, package managers, and systemd services make automation seamless.

If you're new to Linux, don’t worry! This book will guide you through the essentials, and you’ll pick things up as you go.

### Hardware Independence
One of the core principles of this homelab is **hardware independence**. Even if you have just a **single Linux machine**, you can still experiment with many of the concepts covered in this book. The majority of services and applications will run inside **Docker containers**, meaning the underlying OS and hardware don't matter as much.

This makes it easy to:
- Deploy services on any Linux system, whether it's a laptop, desktop, or cloud instance.
- Recreate the same setup on different hardware with minimal modifications.
- Upgrade or switch distributions without breaking existing services.

If you're running a different Linux distribution, you might need to tweak **package installation commands**, but everything else should work the same.

### 1.3.1 Linux-Only Approach
My homelab operates **entirely on Linux**, avoiding proprietary operating systems like Windows. The choice of Linux provides **stability, customization, security, and better automation support**.

- **Debian**: Used for its stability and extensive package support.
- **Alpine Linux**: A lightweight and security-focused distribution, ideal for containers.
- **Arch Linux**: Used for workstations and experimental setups due to its rolling-release model.

#### Why No Windows?
- Windows requires more **resources** and is **less flexible** for server workloads.
- Linux provides **better CLI tooling** for automation and scripting.
- Most cloud-native tools are **designed for Linux environments**.

All my **servers, containers, and orchestration tools** are based on **Linux-native software**, ensuring **high compatibility** and **resource efficiency**.

### 1.3.2 Containerization and Kubernetes
My homelab heavily relies on **containerization** to manage applications efficiently.

#### **Docker for Containers**
- Each application runs in an **isolated container**, ensuring dependencies do not interfere.
- Containers allow **quick deployment, updates, and rollback** without affecting the host system.
- **Docker Compose** is used to manage multi-container applications with ease.

#### **Kubernetes for Orchestration**
I use **K3s**, a lightweight Kubernetes distribution, to manage my **Raspberry Pi cluster**.
- K3s enables **automatic scaling, self-healing, and service discovery**.
- **ArgoCD** is used for **GitOps-based deployment automation**.
- **Cert Manager** manages SSL certificates for Kubernetes workloads.

The combination of **Docker and Kubernetes** allows my homelab to **scale dynamically**, deploy applications reliably, and manage workloads efficiently.

### 1.3.3 Remote Access and Security
Since my homelab contains **sensitive data and self-hosted services**, securing access is a priority.

#### **Cloudflare Tunnel**
- Acts as a **secure gateway** for accessing services remotely.
- Eliminates the need to expose ports directly to the internet.
- Provides **DDoS protection and encrypted connections**.

#### **NetBird for Zero-Trust Networking**
- Connects **homelab devices securely over the internet**.
- Enables **VPN-like connectivity** without traditional VPN complexity.
- Used to access **remote servers hosted on free-tier cloud providers**.

#### **AdGuard Home for DNS-Level Ad Blocking**
- Blocks ads and trackers **network-wide**. 
- Filters out **malicious domains** to enhance security.
- Ensures **faster browsing and privacy** for all devices.

With **Cloudflare Tunnel, NetBird, and AdGuard Home**, my homelab remains **secure, accessible, and private**, even when accessed remotely.

## 1.4 Network Setup Overview
My network is designed for **high availability, security, and efficient traffic routing**.

### 1.4.1 Core Network Layout
#### **Traefik as the Main Entry Point**
- Handles **reverse proxying and load balancing**.
- Provides **automatic SSL certificates with Let’s Encrypt**.
- Routes traffic **intelligently based on hostname or path rules**.

#### **HAProxy on OpenWRT**
- Acts as an **additional layer of security** and **traffic routing**.
- Helps in **load balancing traffic between multiple services**.
- Ensures **high availability of critical services**.

#### **Cloudflare DNS and Tunnels**
- All domain names use **Cloudflare’s DNS**, improving security and speed.
- Cloudflare Tunnel provides **remote access without exposing ports**.

By combining **Traefik, HAProxy, and Cloudflare**, my homelab ensures **secure, efficient, and remote-friendly traffic management**.

### 1.4.2 Internal Services
My homelab hosts several **critical internal services** for data storage, monitoring, and security.

#### **Database Systems**
- **MySQL**: Used for applications requiring **structured relational data**.
- **PostgreSQL**: Preferred for workloads needing **advanced query capabilities**.
- **Cloud-hosted databases (Oracle Free-Tier)** for off-site storage redundancy.

#### **Secrets Management**
- **Akeyless.io** for **managing API keys, credentials, and environment variables**.
- **External Secrets Operator** in Kubernetes to **synchronize secrets securely**.

#### **Monitoring Stack**
- **Prometheus** collects system metrics for monitoring CPU, RAM, and network usage.
- **Grafana** visualizes metrics in **dashboards with alerts and analytics**.

This monitoring stack ensures **real-time insights, alerting, and proactive issue detection** in my homelab.

## Conclusion
This chapter provided a **detailed overview** of the **hardware, software, network layout, and security considerations** of my homelab. In the next chapter, we will begin with the **base system setup**, including Linux installation, network configuration, and preparing the environment for containerized workloads.