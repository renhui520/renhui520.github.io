---
layout: post
title: "关于我写的操作系统"
date:   2024-10-27
tags: [OS, C]
comments: true
author: renhui
---

# 目录:
  # 1. boot.S main.S
  # 2. hhk.c
  # 3. kernel_init.c
  

# OS
- **[我的github](https://github.com/renhui520 "github")**
- **[链接](https://github.com/renhui520/OS "OS")**: https://github.com/renhui520/OS
- 这个操作系统使用qemu进行模拟启动, 当然也可以使用到VMware和VirtualBox等虚拟机, 但是目前并没有实际尝试过
- 使用 make fast-run 运行
```bash
make fast-run
```
- 亦可使用 make kvm 来使用 kvm 虚拟化技术来运行, 达到更接近真机的效果
```bash
make kvm
```
> [!WARNING]
> 若要使用 kvm 来运行这个 OS 必须要先开启 CPU虚拟化 ！！


- 目前仅仅只实现到了虚拟内存管理的malloc, 接下来将会逐步完善外中断, 也就是apic
- 这份项目(OS)的开发时间大概是在2024-07-04开始的, 汇编也是在这个时候开始学习的

- 本项目涉及到GDT和IDT以及apic等知识

## boot.S main.S
  这两个文件主要涉及到操作系统最初的启动，和设置GDT和IDT等  
boot.S主要是引导和配置GRUB2，传递一些参数给GRUB2，例如：是否开始图形模式，初始化内核页大小，栈指针位置，初始化multiboot，为multiboot分配一块内存空间，用于保存multiboot信息，最后开启分页模式  
  main.S主要是配置和加载GDT，IDT，接着跳转到正式内核的初始化文件"init.c"  

# GDT
