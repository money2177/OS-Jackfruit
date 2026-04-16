# Multi-Container Runtime (OS Jackfruit)

A lightweight Linux container runtime implemented in C using Linux namespaces, process isolation, and a long-running supervisor process.

---

## 👩‍💻 Team Details

* **Aditi Hubli**
  SRN: PES1UG24CS652

* **Fathima Zahra**
  SRN: PES1UG24CS664

---

## 📌 Project Overview

This project implements a simplified container runtime similar to Docker using low-level Linux primitives. It supports multiple containers running concurrently with proper isolation and supervision.

---

## ⚙️ Features Implemented

### ✅ Task 1: Multi-Container Runtime

* Supervisor process runs continuously
* Multiple containers can run simultaneously
* Each container has:

  * Isolated PID namespace
  * UTS namespace (hostname isolation)
  * Mount namespace
* Separate root filesystem for each container
* `/proc` mounted correctly inside containers
* Zombie processes handled using `waitpid`

---

## 🧠 Design Approach

* Used `clone()` system call with namespace flags:

  * `CLONE_NEWPID`
  * `CLONE_NEWUTS`
  * `CLONE_NEWNS`
* Used `chroot()` for filesystem isolation
* Mounted `/proc` inside each container
* Implemented a parent supervisor loop to:

  * spawn containers
  * monitor child processes
  * clean up exited containers

---

## 📁 Project Structure

```
OS-Jackfruit/
├── boilerplate/
│   ├── engine.c
│   ├── monitor.c
│   ├── Makefile
│   ├── cpu_hog.c
│   ├── memory_hog.c
│   └── io_pulse.c
├── rootfs-base/
├── rootfs-1/
├── rootfs-2/
├── README.md
└── project-guide.md
```

---

## 🚀 How to Run

### 1. Compile

```bash
cd boilerplate
make
```

### 2. Run Supervisor

```bash
sudo ./engine
```

---

## 🧪 Demonstration

### Multiple Containers Running

* Supervisor launches multiple containers using `clone()`
* Each container runs independently

### Namespace Isolation

Inside container:

```bash
hostname
ps
```

### Filesystem Isolation

* Each container uses its own rootfs copy
* No shared writable filesystem

### /proc Functionality

* `ps` works correctly inside container

### Zombie Handling

```bash
ps aux | grep defunct
```

* No zombie processes observed

---

## 📸 Screenshots

![ss1](jackfruit_screenshots/ss1.png)
![ss2](jackfruit_screenshots/ss2.png)
![ss3](jackfruit_screenshots/ss3.png)
![ss4](jackfruit_screenshots/ss4.png)
![ss5](jackfruit_screenshots/ss5.png)
![ss6](jackfruit_screenshots/ss6.png)
![ss7](jackfruit_screenshots/ss7.png)
![ss8](jackfruit_screenshots/ss8.png)
![ss9](jackfruit_screenshots/ss9.png)
![ss10](jackfruit_screenshots/ss10.png)
![ss11](jackfruit_screenshots/ss11.png)
![ss12](jackfruit_screenshots/ss12.png)
![ss13](jackfruit_screenshots/ss13.png)
![ss14](jackfruit_screenshots/ss14.png)
![ss15](jackfruit_screenshots/ss15.png)
![ss16](jackfruit_screenshots/ss16.png)
![ss17](jackfruit_screenshots/ss17.png)

---

## 🧾 Conclusion

This project demonstrates how Linux namespaces and process management can be used to build a basic container runtime from scratch. It highlights key OS concepts such as isolation, process control, and system-level programming.

---

## 📚 References

* Linux `clone()` manual
* Linux namespaces documentation
* Course project guide

---
