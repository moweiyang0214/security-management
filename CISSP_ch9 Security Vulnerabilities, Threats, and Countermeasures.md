# Security Vulnerabilities, Threats, and Countermeasures

- Domain 3.0: Security Architecture and Engineering

The Security Architecture and Engineering domain addresses a wide range of concerns and issues, including secure design elements, security architecture, vulnerabilities, threats, and associated countermeasures.

## Shared Responsibility

Shared responsibility is the security design principle that indicates that organizations do not operate in isolation. Instead, they are intertwined with the world in numerous ways. We all use the same basic technology, we follow the same communication protocol specifications, we use the same internet, we use common foundations of operating systems and programming languages, and most of our IT/IS is implemented using off-the-shelf solutions (whether commercial or open source). Thus, we are automatically integrated with the rest of the world and we share in the responsibility to establish and maintain security.

It is our task to realize this shared responsibility and take our role in this situation seriously. Here are several aspects of this concept to ponder:

- Everyone in an organization has some level of security responsibility. It is the job of the CISO and security team to establish security and maintain it. It is the job of the regular employees to perform their tasks within the confines of security. It is the job of the auditor to monitor the environment for violations.
- Organizations are responsible to their stakeholders to make good security decisions in order to sustain the organization. Otherwise, the needs of the stakeholders may be violated.
- When working with third parties, especially with cloud providers, each entity needs to understand their portion of the shared responsibility of performing work operations and maintaining security. This is often referenced as the cloud shared responsibility model, which is discussed further in Chapter 16.
- As we become aware of new vulnerabilities and threats, we should consider it our responsibility (if not our duty) to responsibly disclose that information to the proper vendor or to an information sharing center (also known as a threat intelligence source or service).

It is because we participate in shared responsibility that we must research, implement, and manage engineering processes using secure design principles.

### AIS（Automated indicator sharing）

Automated indicator sharing (AIS) is an initiative by the Department of Homeland Security (DHS) to facilitate the open and free exchange of indicators of compromise (IoCs) and other cyberthreat information between the U.S. federal government and the private sector in an automated and timely manner (described as “machine speed”). An indicator is an observable along with a hypothesis about a threat. An observable is an identified fact of occurrence, such as the presence of a malicious file, usually accompanied by a hash.

AIS makes full use of Structured Threat Information eXpression (STIX) and Trusted Automated eXchange of Intelligence Information (TAXII) to share threat indicators. AIS is managed by the National Cybersecurity and Communications Integration Center (NCCIC).

## Assess and Mitigate the Vulnerabilities of Security Architectures, Designs, and Solution Elements

Computer architecture is an engineering discipline concerned with the design and construction of computing systems at a logical level. Technical mechanisms that can be implemented via computer architecture are the controls that system designers can build right into their systems. These include layering, abstraction, data hiding, trusted recovery, process isolation, and hardware segmentation.

**Note:** The more complex a system, the less assurance it provides. More complexity means that more areas for vulnerabilities exist and more areas must be secured against threats. More vulnerabilities and more threats mean that the subsequent security provided by the system is less trustworthy. See Chapter 8 for more on “keep it simple.”

### Hardware

The term hardware encompasses any tangible part of a computer that you can actually reach out and touch, from the keyboard and monitor to its CPU(s), storage media, and memory chips. Take careful note that although the physical portion of a storage device (such as a hard disk or flash memory) may be considered hardware, the contents of those devices—the collections of 0s and 1s that make up the software and data stored within them—may not.

#### Processor

The ***central processing unit (CPU)***, generally called the processor or the microprocessor, is the computer’s nerve center—it is the chip (or chips in a multiprocessor system) that governs all major operations and either directly performs or coordinates the complex symphony of calculations that allows a computer to perform its intended tasks. Surprisingly, the CPU is capable of performing only a limited set of computational and logical operations, despite the complexity of the tasks it allows the overall computer system to perform. It is the responsibility of the operating system and compilers or interpreters to translate high-level programming languages into simple instructions that a CPU understands. This limited range of functionality is intentional—it allows a CPU to perform computational and logical operations at blazing speeds.

##### Execution Types

As computer processing power increased, users demanded more advanced features to enable these systems to process information at greater rates and to manage multiple functions simultaneously:

- **Multitasking** In computing, multitasking means handling two or more tasks simultaneously. In the past, most systems did not truly multitask because they relied on the OS to simulate multitasking by carefully structuring the sequence of commands sent to the CPU for execution (see multiprogramming). A single-core multitasking system is able to juggle more than one task or process at any given time. However, with that single-core CPU, it is still only actually executing a single process at any given moment. This is similar to juggling three balls, where your hands are usually only touching one ball at any given instant but the coordination of movements keeps all three balls moving.
- **Multicore** Today, most CPUs are multicore. This means that the CPU is now a chip containing two, four, eight, dozens, or more independent execution cores that can operate simultaneously and/or independently. There are even some specialty chips with over 10,000 cores.
- **Multiprocessing** In a multiprocessing environment, a multiprocessor system harnesses the power of more than one processor to complete the execution of a multithreaded application.
- **Multiprogramming** Multiprogramming is similar to multitasking. It involves the pseudo-simultaneous execution of two tasks on a single processor coordinated by the OS as a way to increase operational efficiency. For the most part, multiprogramming is a way to batch or serialize multiple processes so that when one process stops to wait on a peripheral, its state is saved and the next process in line begins to process. The first program does not return to processing until all other processes in the batch have had their chance to execute and they in turn stop for a peripheral. For any single program, this methodology causes significant delays in completing a task. However, across all processes in the batch, the total time to complete all tasks is reduced.
- **Multithreading** Multithreading permits multiple concurrent tasks to be performed within a single process. Unlike multitasking, where multiple tasks consist of multiple processes, multithreading permits multiple tasks to operate within a single process. A thread is a self-contained sequence of instructions that can execute in parallel with other threads that are part of the same parent process. Multithreading is often used in applications where frequent context switching between multiple active processes causes excessive overhead and reduces efficiency; switching between threads incurs far less overhead and is therefore more efficient.

Some multiprocessor systems may assign or dedicate a process or execution threat to a specific CPU (or core). This is called **affinity**.

#### Protection Mechanisms

When a computer is running, it operates a runtime environment that represents the combination of the OS and whatever applications may be active. Within that runtime environment, it’s necessary to integrate security controls to protect the integrity of the OS itself, to manage which users are allowed to access specific data items, to authorize or deny operations requested against such data, and so forth. The ways in which running computers implement and handle security at runtime may be broadly described as a collection of protection mechanisms, such as such as protection rings and operational states.

##### PROTECTION RINGS

- **Ring 0: OS Kernel/Memory (Resident Components)**  - 0 has the highest level of privilege and can basically access any resource, file, or memory location. The part of an OS that always remains resident in memory (so that it can run on demand at any time) is called the kernel. It occupies ring 0 and can preempt code running at any other ring.
- **Ring 1: Other OS Components** - The remaining parts of the OS—those that come and go as various tasks are requested, operations performed, processes switched, and so forth—occupy ring 1.
- **Ring 2: Drivers, Protocols, etc.** - Ring 2 is also somewhat privileged in that it’s where I/O drivers and system utilities reside; these are able to access peripheral devices, special files, and so forth that applications and other programs cannot themselves access directly.
- **Ring 3: User-Level Programs and Applications** - Those applications and programs occupy the outermost ring, ring 3.

The essence of the ring model lies in priority, privilege, and memory segmentation. Any process that wants to execute must get in line (a pending process queue). 

- Rings 0–2 run in **supervisory or privileged mode.** 

- Ring 3 runs in **user mode.**

**The process associated with the lowest ring number always runs before processes associated with highernumbered rings.** Processes in lower-numbered rings can access more resources and interact with the OS more directly than those in higher-numbered rings. 

Those processes that run in higher-numbered rings must generally ask a handler or a driver in a lower-numbered ring for services they need (aka **system call**); this is sometimes called a **mediated-access model.** 

In practice, many modern OSs use only two rings or divisions: one for system-level access (rings 0 through 2), often called **kernel mode** or **privileged mode**, and one for user-level programs and applications (ring 3), often called **user mode**.

From a security standpoint, the ring model enables an OS to protect and insulate itself from users and applications. It also permits the enforcement of strict boundaries between highly privileged OS components (such as the kernel) and less privileged parts of the OS (such as other parts of the OS, plus drivers and utilities).

The ring that a process occupies determines its access level to system resources. Processes may access objects directly only if they reside within their own ring or within some outside ring. Before any such request can be honored, however, the called ring must check to make sure that the calling process has the right credentials and authorization to access the data and to perform the operation(s) involved in satisfying the request.

##### PROCESS STATES

![image-20250611001428396](/Users/leiwang/Library/Application Support/typora-user-images/image-20250611001428396.png)

#### Operating Modes

Modern processors and OSs are designed to support multiuser environments in which individual users might not be granted access to all components of a system or all the information stored on it. For that reason, the processor itself supports two modes of operation:

##### **User Mode** （用户模式）

- **谁运行在这里？**
  用户应用程序（如 Word、Chrome、你自己写的 Python 脚本）
  ➜ 即使是系统管理员运行的工具，本身也运行在 User Mode。
- **能干什么？**
  - 只能访问**受限的指令集**
  - 无法直接访问硬件（比如磁盘、内存管理单元、I/O 设备）
  - 如果程序尝试访问受保护的资源，会引发异常（如 Segmentation Fault）
- **为什么存在这个模式？**
  - 防止程序**恶意或无意破坏**系统资源
  - 限制权限范围，提高系统的安全性和稳定性

User mode is the basic mode used by the CPU when executing user applications. In this mode, the CPU allows the execution of only a portion of its full instruction set. This is designed to protect users from accidentally damaging the system through the execution of poorly designed code or the unintentional misuse of that code. It also protects the system and its data from a malicious user and malicious code.

##### **Privileged Mode** （特权模式，也叫 Kernel Mode 或 Supervisor Mode）

- **谁运行在这里？**
  操作系统核心（Kernel）及其关键服务
  ➜ 包括驱动程序、文件系统管理、进程调度、内存分配、网络堆栈等
- **能干什么？**
  - 执行 CPU 所有指令（包括特权指令）
  - 直接访问内存、I/O、硬件中断控制器等
  - 控制所有资源分配、权限校验
- **为什么重要？**
  - 确保操作系统能够对系统进行**完整的控制**
  - 保持资源**统一管理和隔离**

CPUs also support privileged mode, which is designed to give the OS access to the full range of instructions supported by the CPU. Also known as supervisory, system, or kernel mode. Only processes that are components of the OS itself are allowed to execute in this mode, for both security and system integrity purposes.

| 类别     | User Mode（用户区） | Privileged Mode（管制区）            |
| -------- | ------------------- | ------------------------------------ |
| 类比     | 机场公共候机厅      | 飞机驾驶舱 & 控制塔                  |
| 谁能进入 | 所有乘客（程序）    | 只有飞行员和管控人员（操作系统核心） |
| 权限     | 看信息、等待、休息  | 操作飞机、调度航班                   |
| 安全控制 | 严格限制行为        | 拥有全面控制权限                     |

**Note:** Don’t confuse processor modes with any type of user access permissions. The fact that the high-level processor mode is sometimes called privileged or supervisory mode has no relationship to the role of a user. All user applications, including those of system administrators, run in user mode. When system administrators use system tools to make configuration changes to the system, those tools also run in user mode. When a user application needs to perform a privileged action, it passes that request to the OS using a system call, which evaluates it and either rejects the request or approves it and executes it using a privileged mode process outside the user’s control.

##### 关键机制：**系统调用（System Call）**

用户程序**不能直接切换**到特权模式。必须通过**系统调用接口（如 Linux 的 `syscall`）**向操作系统提出请求：

1. 用户程序运行时请求（如读取磁盘文件）
2. 通过“系统调用”请求操作系统执行
3. 操作系统内核检查请求合法性
4. 如果允许，操作系统在特权模式下执行
5. 返回结果，恢复用户模式继续运行

这就像：

> 乘客不能自己去驾驶舱开飞机，只能按服务铃请求乘务员去转达请求，由专业人员决定是否满足。

**“管理员不就是有最高权限了吗？是不是也能运行在 Privileged Mode？”**
❌ **错。管理员是高权限用户**，但运行的程序仍在 **User Mode**。只有操作系统核心的代码才能运行在 **Privileged Mode**。

##### CISSP考点总结

| 考点         | 内容                                                         |
| :----------- | ------------------------------------------------------------ |
| **保护机制** | 用户模式限制权限，避免系统被破坏                             |
| **安全边界** | 内核与用户之间的模式切换是关键安全边界                       |
| **原则体现** | 最小权限原则、强制访问控制                                   |
| **考试陷阱** | 不要混淆“用户权限”和“处理器模式”！系统管理员也运行在用户模式下 |

#### Memory

The second major hardware component of a system is memory, the storage bank for information that the computer needs to keep readily available. There are many different kinds of memory, each suitable for different purposes, and we’ll take a look at each in the sections that follow.

##### Read-Only Memory

**Read-only memory (ROM)** works like the name implies—it’s memory the system can read but can’t change (no writing allowed). The contents of a standard ROM chip are burned in at the factory, and the end user simply cannot alter it. ROM chips often contain “bootstrap” information that computers use to start up prior to loading an OS from disk. This includes the **power-on self-test (POST)** series of diagnostics that run each time you boot a PC.

ROM’s primary advantage is that it can’t be modified. This attribute makes ROM extremely desirable for orchestrating a computer’s innermost workings.

There is a type of ROM that may be altered to some extent. It is known as programmable read-only memory (PROM), and its several subtypes:

- **Programmable Read-Only Memory (PROM)** A basic programmable read-only memory (PROM) chip is similar to a ROM chip in functionality, but with one exception. During the manufacturing process, a PROM chip’s contents aren’t “burned in” at the factory as with standard ROM chips. Instead, a PROM incorporates special functionality that allows an end user to burn in the chip’s contents later. Once data is written to a PROM chip, no further changes are possible.
- **Erasable Programmable Read-Only Memory (EPROM)** Combine the relatively high cost of PROM chips and software developers’ inevitable desires to tinker with their code once it’s written and you have the rationale that led to the development of erasable PROM (EPROM). There are two main subcategories of EPROM: UVEPROM and EEPROM (see the next item). Ultraviolet EPROMs (UVEPROMs) can be erased with a light. These chips have a small window that, when illuminated with a special ultraviolet light, causes the contents of the chip to be erased. After this process is complete, end users can burn new information into the UVEPROM as if it had never been programmed before.
- **Electronically Erasable Programmable Read-Only Memory (EEPROM)** A more flexible, friendly alternative to UVEPROM is electronically erasable PROM (EEPROM), which uses electric voltages delivered to the pins of the chip to force erasure.
- **Flash Memory** Flash memory is a derivative concept from EEPROM. It is a nonvolatile form of storage media that can be electronically erased and rewritten. The primary difference between EEPROM and flash memory is that EEPROM must be fully erased to be rewritten, whereas flash memory can be erased and written in blocks or pages. The most common type of flash memory is NAND flash. It is widely used in memory cards, thumb drives, mobile devices, and SSDs (solid-state drives).

##### Random Access Memory

Random access memory (RAM) is readable and writable memory that contains information a computer uses during processing. RAM retains its contents only when power is continuously supplied to it. Unlike with ROM, when a computer is powered off, all data stored in RAM disappears. For this reason, RAM is useful only for temporary storage. Critical data should never be stored solely in RAM; a backup copy should always be kept on another storage device to prevent its disappearance in the event of a sudden loss of electrical power. The following are types of RAM:

- **Real Memory** Real memory (also known as main memory or primary memory) is typically the largest RAM storage resource available to a computer. It is normally composed of a number of dynamic RAM chips and, therefore, must be refreshed by the CPU on a periodic basis (see the sidebar “Dynamic vs. Static RAM” for more information on this subject).
- **Cache RAM** Computer systems contain a number of caches that improve performance by taking data from slower devices and temporarily storing it in faster devices when repeated use is likely; this is cache RAM. The processor normally contains an onboard cache of extremely fast memory used to hold data on which it will operate. This can be referred to as L1, L2, L3, and even L4 cache (with the L being short for level). Many modern CPUs include up to three levels of on-chip cache, with some caches (usually L1 and/or L2) dedicated to a single processor core, whereas L3 may be a shared cache between cores. Some CPUs can involve L4 cache, which may be located on the mainboard/ motherboard or on the GPU (graphics processing unit). Likewise, real memory often contains a cache of information pulled or read from a storage device.

Many peripherals also include onboard caches to reduce the storage burden they place on the CPU and OS. Many storage devices, such as hard disk drives (HDDs), solid-state drives (SSDs), and some thumb drives, contain caches to assist with improving read and write speed. However, these caches must be flushed to the permanent or secondary storage area before disconnection or power loss in order to avoid data loss of cache resident data.

##### Registers (寄存器)

The CPU also includes a limited amount of onboard memory, known as registers, that provide it with directly accessible memory locations that the brain of the CPU, the arithmeticlogical unit (ALU), uses when performing calculations or processing instructions. The size and number of registers varies, but typical CPUs have 8 to 32 registers and are often either 32 or 64 bits in size. In fact, any data that the ALU is to manipulate must be loaded into a register unless it is directly supplied as part of the instruction. The main advantage of this type of memory is that it is part of the ALU itself and, therefore, operates in lockstep with the CPU at typical CPU speeds.

##### Memory Addressing

When using memory resources, the processor must have some means of referring to various locations in memory. The solution to this problem is known as memory addressing, and there are several different addressing schemes used in various circumstances. The following are five of the most common addressing schemes:

- **Register Addressing** As you learned in the previous section, registers are small memory locations directly in the CPU. When the CPU needs information from one of its registers to complete an operation, it uses a register address (for example, “register 1”) to access its contents.
- **Immediate Addressing** Immediate addressing is not a memory addressing scheme per se but rather a way of referring to data that is supplied to the CPU as part of an instruction. For example, the CPU might process the command “Add 2 to the value in register 1.” This command uses two addressing schemes. The first is immediate addressing—the CPU is being told to add the value 2 and does not need to retrieve that value from a memory location—it’s supplied as part of the command. The second is register addressing; it’s instructed to retrieve the value from register 1.
- **Direct Addressing** In direct addressing, the CPU is provided with an actual address of the memory location to access. The address must be located on the same memory page as the instruction being executed. Direct addressing is more flexible than immediate addressing since the contents of the memory location can be changed more readily than reprogramming the immediate addressing’s hard-coded data.
- **Indirect Addressing** Indirect addressing uses a scheme similar to direct addressing. However, the memory address supplied to the CPU as part of the instruction doesn’t contain the actual value that the CPU is to use as an operand. Instead, the memory address contains another memory address. The CPU reads the indirect address to learn the address where the desired data resides and then retrieves the actual operand from that address.
- **Base+Offset Addressing** Base+offset addressing uses a value stored in one of the CPU’s registers or pointers as the base location from which to begin counting. The CPU then adds the offset supplied with the instruction to that base address and retrieves the operand from that computed memory location.

##### Secondary Memory

**Secondary memory** is a term commonly used to refer to magnetic, optical, or flash-based media or other storage devices that contain data not immediately available to the CPU. For the CPU to access data in secondary memory, the data must first be read by the OS and stored in real memory.

**Virtual memory** is a special type of secondary memory that is used to expand the addressable space of real memory. The most common type of virtual memory is the pagefile or swapfile that most OSs manage as part of their memory management functions. This specially formatted file contains data previously stored in real memory but not recently used. When the OS needs to access addresses stored in the pagefile, it checks to see whether the page is memory-resident (in which case it can access it immediately) or whether it has been swapped to disk, in which case it reads the data from disk back into real memory (this process is called paging).

Virtual memory’s primary drawback is that the paging operations that occur when data is exchanged between primary and secondary memory are relatively slow. The need for virtual memory is reduced with larger banks of actual physical RAM, and the performance hit of virtual memory can be reduced by using a flashcard or an SSD to host the virtual memory paging file.

| 类型                  | 是否可写   | 挥发性       | 用途                          | 备注                    |
| --------------------- | ---------- | ------------ | ----------------------------- | ----------------------- |
| **ROM**               | ❌ 不可写   | ❌ 非易失性   | 存放固化启动信息，如 BIOS     | 出厂烧录，无法更改      |
| **PROM**              | ✅ 一次写入 | ❌            | 用户可写一次                  | 开发中常用              |
| **EPROM**             | ✅ 可擦写   | ❌            | 可用 UV 光擦除                | 有透明窗口              |
| **EEPROM**            | ✅ 可电擦写 | ❌            | 用电信号擦除再重写            | 更灵活，闪存前身        |
| **Flash**             | ✅ 分块擦写 | ❌            | 常见于 SSD、U盘、移动设备     | EEPROM 的高级演化       |
| **RAM**               | ✅ 可写     | ✅ 易失性     | 程序运行时主存                | 无电即失，需持续供电    |
| **Registers**         | ✅ 可写     | ✅ 极快速易失 | CPU运算中临时操作数存储       | 最靠近 ALU，数量极少    |
| **Cache RAM (L1~L4)** | ✅ 可写     | ✅            | 加速内存/磁盘等数据访问       | 越靠近CPU越快、越小     |
| **Secondary Memory**  | ✅ 可写     | ❌            | 持久数据存储，如硬盘          | CPU需通过OS间接访问     |
| **Virtual Memory**    | ✅ 可写     | ❌            | 临时补充主内存空间（如 swap） | 慢、但可以扩展 RAM 功能 |

##### Memory Addressing（内存寻址方式）

理解**5种主流内存寻址方式**对安全工程师理解程序执行和漏洞原理（如缓冲区溢出）非常关键：

| 模式                     | 简介                     | 示例                                 | 应用场景                       |
| ------------------------ | ------------------------ | ------------------------------------ | ------------------------------ |
| **Register Addressing**  | 从寄存器读取操作数       | ADD R1, R2                           | 极快，CPU 内部数据交换         |
| **Immediate Addressing** | 直接提供数据             | ADD R1, #5                           | 编译器嵌入常量操作数           |
| **Direct Addressing**    | 指定实际内存地址         | LOAD A, 0x1000                       | 指令可访问物理内存             |
| **Indirect Addressing**  | 提供一个“指向地址的地址” | MOV A, (0x2000) → 去 0x2000 处取地址 | 指针式访问结构                 |
| **Base + Offset**        | 基址+偏移计算实际地址    | MOV A, [R1 + 4]                      | 访问数组、结构体等复杂数据结构 |

🔐 **安全启示**：

- 不正确管理指针或偏移很容易造成**内存泄漏或越界访问漏洞**
- 熟悉寻址模式有助于理解汇编分析与逆向工程

##### Register, Cache, RAM, Secondary Memory 的层级关系（速度 & 作用）

这部分可以用一个金字塔图表示，越顶端越快越小：

```
  ┌────────────┐
  │ Registers  │ ⏩ 极小、超快（CPU内部）
  └────┬───────┘
       ↓
  ┌────────────┐
  │ Cache RAM  │ ⏩ 快速临时缓存（L1~L4）
  └────┬───────┘
       ↓
  ┌────────────┐
  │ Real RAM   │ ⏩ 程序运行时主内存
  └────┬───────┘
       ↓
  ┌──────────────┐
  │ Virtual Mem  │ ⏩ 页交换，慢
  └────┬─────────┘
       ↓
  ┌──────────────┐
  │ Secondary Mem│ ⏩ 持久磁盘存储，如 SSD/HDD
  └──────────────┘

```

##### CISSP 考试重点提示

| 考点类别                 | 可能问题或陷阱                              |
| ------------------------ | ------------------------------------------- |
| **ROM 类型比较**         | 哪种可以紫外线擦除？（答：UVEPROM）         |
| **缓存原理**             | 多级缓存 L1~L4 的作用及层级？               |
| **虚拟内存**             | 说明 pagefile/swapfile 的工作机制及性能瓶颈 |
| **寄存器作用**           | ALU 操作数必须来自哪里？（答：Registers）   |
| **数据持久性**           | 哪些内存类型属于非易失性？                  |
| **间接寻址 vs 基址偏移** | 哪种更常用于数组访问？                      |

#### Data Storage Devices

Data storage devices are used to store information that may be used by a computer any time after it’s written.

##### Primary vs. Secondary

Primary memory, also known as primary storage, is the RAM that a computer uses to keep necessary information readily available to the CPU while the computer is running. Secondary memory (or secondary storage) includes all the familiar long-term storage devices that you use every day. Secondary storage consists of magnetic and optical media such as HDDs, SSDs, flash drives, magnetic tapes, CDs, DVDs, and flash memory cards.

##### Volatile vs. Nonvolatile

The volatility of a storage device is simply a measure of how likely it is to lose its data when power is turned off or cycled. Devices designed to retain their data (such as magnetic media, ROMs, and optical media) are classified as nonvolatile, whereas devices such as static or dynamic RAM modules, which lose their data when power is removed, are classified as volatile.

##### Random vs. Sequential

Storage devices may be accessed in one of two fashions. Random access storage devices allow an OS to read (and sometimes write) immediately from any point within the device by using some type of addressing system. Almost all primary storage devices are random access devices. You can use a memory address to access information stored at any point within a RAM chip without reading the data that is physically stored before it. Most secondary storage devices are also random access.

Sequential storage devices, on the other hand, do not provide this flexibility. They require that you read (or speed past) all the data physically stored prior to the desired location. A common example of a sequential storage device is a magnetic tape drive.

##### Memory Security Issues

Memory stores and processes your data—some of which may be extremely sensitive. Any memory devices that may retain sensitive data should be purged before they are allowed to leave your organization for any reason. This is especially true for secondary memory and ROM/PROM/EPROM/EEPROM devices designed to retain data even after the power is turned off.

However, memory data retention issues are not limited to secondary memory (i.e., storage devices). It is technically possible that the electrical components used in volatile primary memory could retain some of their charge for a limited period of time after power is turned off. A technically sophisticated individual could theoretically retrieve portions of the data stored on such devices.

There is a memory compromise, called the cold boot attack, that freezes memory chips to delay the decay of resident data when the system is turned off or the RAM is pulled out of the motherboard. See en.wikipedia.org/wiki/Cold_boot_attack. There are even attacks and tools that focus on memory image dumps or system crash dumps to extract encryption keys.

##### Storage Media Security

There are several concerns when it comes to the security of secondary storage devices:

1. Data may remain on secondary storage devices even after it has been erased. This condition is known as data remanence. Utilities are available that can retrieve files from a disk even after they have been deleted or reformatted. If you truly want to remove data from a secondary storage device, you must use a specialized utility designed to overwrite all traces of data on the device (commonly called sanitizing) or damage or destroy it beyond possible repair.
2. A traditional zeroization wipe is less effective for SSDs because bad blocks are likely not overwritten.
3. Secondary storage devices are also prone to theft. Economic loss is not the major factor (after all, how much does a backup tape or a hard drive cost?), but the loss of confidential information poses great risks. For this reason, it is important to use full-disk encryption to reduce the risk of an unauthorized entity gaining access to your data. Many HDDs, SSDs, and flash devices offer on-device native encryption.
4. Removable media pose a significant information disclosure risk, so securing them often requires encryption technologies.

#### Emanation Security

Many electrical devices emanate electrical signals or radiation that can be intercepted and may contain confidential, sensitive, or private data. Obvious examples of emanation devices are wireless networking equipment and mobile phones, but many other devices are vulnerable to emanation interception that you might not expect, including monitors, network cables, modems, and internal or external media drives (hard drives, USB thumb drives, CDs, and so on). With the right equipment, adversaries can intercept electromagnetic or radio frequency signals (collectively known as emanations) from these devices and interpret them to extract confidential data.

#### Input and Output Devices

##### Monitors

##### Printers

##### Keyboards/Mice

##### Modems

#### Firmware

## Client-Based Systems

### 1. Mobile Code

### 2. Local Caches

## Server-Based Systems

### 1. Large-Scale Parallel Data Systems

### 2. Grid Computing

### 3. Peer to Peer

## Industrial Control Systems

## Distributed Systems

## High-Performance Computing (HPC) Systems

## Internet of Things

## Edge and Fog Computing

## Embedded Devices and Cyber-Physical Systems

