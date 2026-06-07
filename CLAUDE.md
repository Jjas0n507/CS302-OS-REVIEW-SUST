# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 仓库用途

这是《操作系统》课程的期末考试复习文件夹，包含课件 PDF（Spring 2026，Prof. Yinqian Zhang）。资料不完整，后续可能添加更多文件。

## 课程课件清单（按教学顺序）

| 编号 | 文件 | 主题 |
|------|------|------|
| L02 | `L02 OS Basics.pdf` | 计算机系统组织、冯诺依曼架构、OS 结构、虚拟化 |
| L03 | `L03 Processes(1).pdf` | 进程抽象、系统调用、fork/exec/wait、线程 |
| L04 | `L04 Address Translation(1).pdf` | 地址转换、多道程序、内存分区、分段、基址/界限寄存器 |
| L05 | `L05 Paging.pdf` | 分页机制、多级页表、TLB、实际分页方案 |
| L06 | `L06 Demand Paging(2).pdf` | 请求分页、虚拟内存、交换空间、页面置换算法 |
| L07 | `L07 Linux Memory Management(1).pdf` | Linux 内存管理、用户/内核地址空间划分 |
| L08 | `L08 CPU Scheduling.pdf` | CPU 调度、抢占/非抢占调度、调度算法与优化指标 |
| L09 | `L09 Synchronization.pdf` | 线程/进程同步、竞态条件、锁、信号量等同步原语 |
| L10 | `L10 Deadlock.pdf` | 死锁的条件、预防、避免、检测与恢复 |
| L11 | `L11 IO and Storage.pdf` | I/O 设备接口、轮询、中断、DMA、存储层次 |
| L12 | `L12 File System.pdf` | 文件系统：命名、磁盘管理、保护、可靠性 |
| L13 | `L13 Operating System Security.pdf` | OS 安全：隔离、访问控制、ASLR、Stack Canary、CFI、Fuzzing |

缺失的课件：L01（可能是课程介绍/大纲）。复习时注意结合课件之间的逻辑递进关系。

## 常用操作

- **搜索课件内容**：`pdftotext "文件名.pdf" - | grep -i "关键词"` — 提取 PDF 文本并搜索
- **提取课件前 N 页文本**：`pdftotext -l N "文件名.pdf" -` — 快速浏览内容
- **批量搜索所有课件**：`for f in *.pdf; do echo "=== $f ==="; pdftotext "$f" - 2>/dev/null | grep -i "关键词"; done`

## 课程知识体系架构

整个课程围绕操作系统的四大核心抽象展开：

1. **进程（CPU 虚拟化）** — L03 → L08 → L09 → L10
   - 进程是 CPU 的虚拟化抽象，从进程创建（fork/exec）到 CPU 调度（调度算法），再到进程间同步（锁、信号量）和死锁问题，形成一条完整链路。

2. **内存（内存虚拟化）** — L04 → L05 → L06 → L07
   - 从早期的分段和基址/界限方案，到现代分页机制（多级页表 + TLB），再到请求分页和虚拟内存，最后以 Linux 的具体实现收尾。核心理念：让每个进程以为自己独占内存。

3. **存储与 I/O（持久化）** — L11 → L12
   - 从底层设备接口（轮询、中断、DMA）到上层文件系统抽象（inode、目录、块管理），实现数据的持久化存储。

4. **安全与保护** — L13
   - 隔离、访问控制、漏洞发现与利用防护（ASLR、Stack Canary、CFI）、入侵检测。

此外，L02 提供了计算机系统组织和 OS 基础概念的总览，是以上所有内容的背景知识。

## 复习建议

- 按模块（进程/内存/存储/安全）横向复习，而非按课件顺序纵向推进
- 重点关注 L09（同步）和 L05+L06（分页+请求分页），这两个是传统考试重点
- L07（Linux 内存管理）内容较少，可能与 L05/L06 合并考察
- L10（死锁）虽然页数少，但死锁四个必要条件、银行家算法是经典考点
- 如需深入某个主题，可以让我直接提取对应 PDF 的完整文本进行讲解或问答
