# Type-1 Hypervisor – Proxmox VE

## Overview

Proxmox VE is an open-source bare-metal Type-1 hypervisor deployed directly on physical server hardware. In this experiment, an Ubuntu virtual machine is configured and deployed using the Proxmox VE web interface. System resources are verified and CPU performance is benchmarked using Sysbench.

## 1. Virtual Machine Specifications

| Parameter       | Configuration               |
| --------------- | --------------------------- |
| Hypervisor      | Proxmox VE                  |
| Hypervisor Type | Type-1                      |
| Node            | Selected Proxmox Node (pve) |
| VM Name         | CC-Experiment1-Type1        |
| Guest OS        | Linux (Ubuntu 64-bit)       |
| ISO Image       | ubuntu-22.04.iso            |
| CPU             | 2 vCPU (1 Socket, 2 Cores)  |
| Memory          | 2048 MiB (2 GB)             |
| Disk            | 20 GB (local-lvm)           |
| Network         | vmbr0 (VirtIO)              |

## 2. System Verification

| Verification      | Command       |
| ----------------- | ------------- |
| Hostname & OS     | `hostnamectl` |
| CPU               | `lscpu`       |
| Memory            | `free -h`     |
| Disk              | `df -h`       |
| System Monitoring | `top`         |

## 3. CPU Performance Benchmark

### Installation

```bash
sudo apt update
sudo apt install sysbench -y
sysbench --version
```

### Execution

```bash
sysbench cpu --cpu-max-prime=20000 run
```

## 4. Observation & Results

| Parameter            | Observation |
| -------------------- | ----------: |
| Hypervisor           |  Proxmox VE |
| Hypervisor Type      |      Type-1 |
| Guest OS             |      Ubuntu |
| CPU                  |      2 vCPU |
| Memory               |        2 GB |
| Disk                 |       20 GB |
| Total Execution Time |   10.0006 s |
| Total Events         |       16903 |
| Events per Second    |     1689.43 |
| Minimum Latency      |     0.57 ms |
| Average Latency      |     0.59 ms |
| Maximum Latency      |     1.09 ms |

## 5. Workflow

1. Open the Proxmox VE web interface.
2. Select the Proxmox node and create a new VM.
3. Configure Ubuntu ISO, CPU, memory, disk, and network.
4. Start the VM and install Ubuntu.
5. Verify the system using the listed Linux commands.
6. Install and run Sysbench.
7. Record the benchmark results.
8. Monitor the VM and power it off after completion.
