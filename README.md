# Multi-Container Runtime Project

---

## 👩‍💻 Team Information

Name: Aditi Hubli — SRN: PES1UG24CS652
Name: Fathima Zahra — SRN: PES1UG24CS664

---

## 🎯 Objective

To implement a lightweight container runtime using OS concepts like process management, IPC, namespaces, and kernel modules.

---

## 🔗 Components

* engine.c (User-space runtime)
* monitor.c (Kernel module)
* monitor_ioctl.h
* Workloads: cpu_hog, memory_hog, io_pulse

---

## 🛠️ Build Instructions

```bash
make
```

![ss1](jackfruit_screenshots/ss1.png)

---

## 📦 Load Kernel Module

```bash
sudo insmod monitor.ko
ls -l /dev/container_monitor
```

![ss2](jackfruit_screenshots/ss2.png)

---

## 🚀 Run Supervisor

```bash
sudo ./engine supervisor ../rootfs-base
```

![ss3](jackfruit_screenshots/ss3.png)

---

## 🧪 Run Containers

```bash
sudo ./engine start alpha ./rootfs-alpha /bin/sh
sudo ./engine start beta ./rootfs-beta /bin/sh
```

![ss4](jackfruit_screenshots/ss4.png)

---

## 📋 List Containers

```bash
sudo ./engine ps
```

![ss5](jackfruit_screenshots/ss5.png)

---

## 📜 View Logs

```bash
sudo ./engine logs alpha
```

![ss6](jackfruit_screenshots/ss6.png)

---

## ⛔ Stop Containers

```bash
sudo ./engine stop alpha
```

![ss7](jackfruit_screenshots/ss7.png)

---

## 📊 Memory Monitoring

```bash
sudo dmesg | tail
```

![ss8](jackfruit_screenshots/ss8.png)

---

## ⚙️ Scheduling Demo

```bash
./boilerplate/cpu_hog
./boilerplate/io_pulse
```

![ss9](jackfruit_screenshots/ss9.png)
![ss10](jackfruit_screenshots/ss10.png)

---

## 🧹 Cleanup

```bash
sudo rmmod monitor
```
![ss11](jackfruit_screenshots/ss11.png)
---

## ✨ Features

* Supervisor process for managing multiple containers
* CLI commands: start, ps, logs, stop
* Kernel module for monitoring container behavior
* Scheduling experiments using workload programs

---
