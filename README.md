# The Self-Hosted Engineer (WORK IN PROGRESS)

Welcome **The self hosted engineer**, a journey into the world of homelabs, self-hosting, and cloud computing using open-source tools and free-tier services.
This book is not just a technical guide—it’s a collection of my experiences, challenges, and insights as I build and manage my own infrastructure using Raspberry Pi clusters, dusty old Lenovo/Dell laptops from 2015, spare routers, and various cloud and SaaS solutions to support the softwares.

In today's world, cloud computing and DevOps practices are shaping the way we deploy and manage applications. But what if you could build and experiment with these technologies right from your home? 
That’s exactly what this book is about—creating a self-hosted, cost-effective homelab using a mix of open-source software and free-tier cloud services.

Whether you're an aspiring DevOps engineer, a tech enthusiast, or someone who just loves tinkering with servers, networking, and automation, this book will guide you through setting up your own infrastructure, experimenting with Kubernetes, automating workflows, and integrating cloud services—all while keeping costs minimal.

Through real-world examples and practical insights, I aim to share everything I’ve learned, making it easier for you to build, experiment, and scale your own homelab.

Let’s dive in!

Probable roadmap

### **Chapter 1: Introduction and Inventory**

- What is a homelab?
- Why build a homelab? (Learning, self-hosting, cost-efficiency)
- Hardware inventory (Raspberry Pi, laptops, router)
- Software philosophy (open-source, Linux-only, Docker/K8s-based)
- Network setup overview

### **Chapter 2: Setting Up the Base System**

- Installing Linux on servers (Debian setup, initial configuration)
- Configuring OpenWRT on the router (basic network setup)
- Setting up AdGuard Home for network-wide ad blocking
- Securing remote access with Cloudflare and NetBird

### **Chapter 3: Containerization with Docker**

- Why use Docker?
- Installing and configuring Docker
- Running and managing containers
- Using Docker Compose for multi-container applications
- Setting up Gluetun VPN for secure container networking

### **Chapter 4: Kubernetes on Raspberry Pi**

- What is Kubernetes? Why use it in a homelab?
- Setting up a Raspberry Pi Kubernetes cluster
- Installing and configuring K3s
- Managing workloads in Kubernetes

### **Chapter 5: Networking and Proxying Traffic**

- Reverse proxies: HAProxy and Traefik
- Configuring HAProxy on OpenWRT
- Setting up Traefik as the main entry point
- Using Cert Manager for automatic TLS certificates

### **Chapter 6: Deploying Applications with GitOps**

- What is GitOps?
- Setting up ArgoCD for declarative application deployment
- Managing Kubernetes workloads with ArgoCD

### **Chapter 7: Storage Solutions**

- Why storage is important in a homelab
- Setting up Longhorn for Kubernetes persistent volumes
- Configuring NFS for shared storage
- Self-hosted cloud storage with Nextcloud

### **Chapter 8: Database Management**

- MySQL and PostgreSQL in the homelab
- Hosting databases on local machines and cloud VMs
- Connecting applications securely to databases

### **Chapter 9: Secrets Management**

- Why secrets management is important
- Using Akeyless.io for managing secrets
- Configuring External Secrets Operator in Kubernetes

### **Chapter 10: Monitoring and Observability**

- Introduction to observability in homelabs
- Setting up Prometheus for metrics collection
- Visualizing data with Grafana
- Setting up alerting for system failures

### **Chapter 11: Self-Hosting Services**

- Running an ARR stack for media management
- Hosting a dashboard with Homarr
- Automating workflows with n8n

### **Chapter 12: Scaling and Future Improvements**

- Expanding the homelab with more nodes
- Hybrid cloud and local homelab integration
- Backup and disaster recovery strategies