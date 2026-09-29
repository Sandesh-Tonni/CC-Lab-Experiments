# Type-2 Hypervisor – VMware Workstation

## Overview

VMware Workstation is a Type-2 hypervisor that runs on top of a host operating system. In this experiment, an Ubuntu virtual machine is created using VMware Workstation and its CPU performance is analyzed using Sysbench.

## 1. Virtual Machine Specifications

| Parameter       | Configuration                 |
| --------------- | ----------------------------- |
| Hypervisor      | VMware Workstation            |
| Hypervisor Type | Type-2                        |
| VM Name         | CC-Experiment1-Type2          |
| Guest OS        | Ubuntu 64-bit                 |
| CPU             | 2 vCPU (1 Processor, 2 Cores) |
| Memory          | 8 GB (8192 MB)                |
| Disk            | 20 GB                         |
| Network         | NAT                           |

## 2. System Verification

The following commands are used to verify the Ubuntu VM:

```bash
hostnamectl
lscpu
free -h
df -h
top
```

## 3. CPU Performance Benchmark

Install Sysbench:

```bash
sudo apt update
sudo apt install sysbench -y
sysbench --version
```

Run the CPU benchmark:

```bash
sysbench cpu --cpu-max-prime=20000 run
```

## 4. Observation & Results

| Metric               |    Result |
| -------------------- | --------: |
| Total Execution Time | 10.0003 s |
| Total Events         |     17588 |
| Events per Second    |   1758.60 |
| Minimum Latency      |   0.55 ms |
| Average Latency      |   0.57 ms |
| Maximum Latency      |   1.11 ms |

## 5. Workflow

1. Launch VMware Workstation.
2. Create a new virtual machine and select the Ubuntu ISO.
3. Configure the VM with 2 vCPU and 8 GB RAM.
4. Allocate a 20 GB virtual disk and select NAT networking.
5. Install Ubuntu and complete the VM setup.
6. Verify system resources using Linux commands.
7. Install and run Sysbench CPU benchmark.
8. Record the performance results and power off the VM.
