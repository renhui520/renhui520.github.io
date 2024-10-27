---
layout: post
title: "关于我写的操作系统"
date:   2024-10-27
tags: [OS, C]
comments: true
author: xxx
---

# OS
- 链接: https://github.com/renhui520/OS
- 这个操作系统使用qemu进行模拟启动, 当然也可以使用到VMware和VirtualBox等虚拟机, 但是目前并没有实际尝试过
- 使用 make run 运行
- 亦可使用 make kvm 来使用 kvm 虚拟化技术来运行, 达到更接近真机的效果
- 目前仅仅只实现到了虚拟内存管理的malloc, 接下来将会逐步完善外中断, 也就是apic
