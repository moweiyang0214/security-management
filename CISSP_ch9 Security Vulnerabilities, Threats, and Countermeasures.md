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

| 分类                  | 说明                          | 示例                     | 关键点                   |
| --------------------- | ----------------------------- | ------------------------ | ------------------------ |
| **Primary Memory**    | 临时数据处理，直接由 CPU 使用 | RAM、Cache、Registers    | 易失性，断电丢失         |
| **Secondary Storage** | 长期数据保存                  | HDD、SSD、USB、DVD、磁带 | 非易失性，需 OS 协调访问 |

🔐 **安全性区别**：二级存储因其持久性，**数据残留风险大**，需格外注意清除/加密措施。

##### Volatile vs. Nonvolatile

The volatility of a storage device is simply a measure of how likely it is to lose its data when power is turned off or cycled. Devices designed to retain their data (such as magnetic media, ROMs, and optical media) are classified as nonvolatile, whereas devices such as static or dynamic RAM modules, which lose their data when power is removed, are classified as volatile.

| 分类            | 电源断开是否保留数据 | 示例                       |
| --------------- | -------------------- | -------------------------- |
| **Volatile**    | ❌ 不保留             | RAM、Cache、Registers      |
| **Nonvolatile** | ✅ 保留               | ROM、SSD、HDD、光盘、Flash |

⚠️ 虽然 RAM 是易失性，但冷启动攻击等高级手段可**延缓电荷衰减**，读取部分内存残留数据。

##### Random vs. Sequential

Storage devices may be accessed in one of two fashions. Random access storage devices allow an OS to read (and sometimes write) immediately from any point within the device by using some type of addressing system. Almost all primary storage devices are random access devices. You can use a memory address to access information stored at any point within a RAM chip without reading the data that is physically stored before it. Most secondary storage devices are also random access.

Sequential storage devices, on the other hand, do not provide this flexibility. They require that you read (or speed past) all the data physically stored prior to the desired location. A common example of a sequential storage device is a magnetic tape drive.

| 访问方式              | 描述             | 示例               | CISSP 场景             |
| --------------------- | ---------------- | ------------------ | ---------------------- |
| **Random Access**     | 任意位置快速访问 | RAM、SSD、HDD      | 大多数操作系统设计基础 |
| **Sequential Access** | 顺序读取，速度慢 | 磁带、部分日志系统 | 适用于归档、批处理场景 |

📌 **考点提示**：备份磁带 = **顺序访问**设备；SSD = **随机访问**设备（且有数据擦除挑战）。

##### Memory Security Issues (Memory 安全风险与对策总结)

1. **数据残留（Data Remanence）**

- **定义**：数据在看似“删除”后依然残存于介质上的现象。
- **解决方案**：
  - 使用专业工具彻底**擦除（sanitization）**数据
  - 采用 **DoD 5220.22-M** 标准的多次覆写
  - 对 SSD：注意不能完全控制哪些块被擦除，传统 wipe 无法保证

2. **冷启动攻击（Cold Boot Attack）**

- **原理**：RAM 芯片在极低温状态下掉电后依然保持数据数秒到数分钟
- **风险数据**：密码、加密密钥
- **对策**：
  - 禁用睡眠/休眠时保留内存
  - 开启全盘加密并存储密钥在 TPM 中，而非内存中
  - 设定 BIOS 密码、禁用 USB 启动

3. **Crash Dump / Memory Dump 攻击**

- **描述**：黑客提取系统崩溃转储文件或内存镜像，提取敏感信息
- **对策**：
  - 限制系统产生 dump 的权限
  - 禁用调试工具访问生产环境
  - 加密内存中的敏感数据（如密码）

Memory stores and processes your data—some of which may be extremely sensitive. Any memory devices that may retain sensitive data should be purged before they are allowed to leave your organization for any reason. This is especially true for secondary memory and ROM/PROM/EPROM/EEPROM devices designed to retain data even after the power is turned off.

However, memory data retention issues are not limited to secondary memory (i.e., storage devices). It is technically possible that the electrical components used in volatile primary memory could retain some of their charge for a limited period of time after power is turned off. A technically sophisticated individual could theoretically retrieve portions of the data stored on such devices.

There is a memory compromise, called the cold boot attack, that freezes memory chips to delay the decay of resident data when the system is turned off or the RAM is pulled out of the motherboard. See en.wikipedia.org/wiki/Cold_boot_attack. There are even attacks and tools that focus on memory image dumps or system crash dumps to extract encryption keys.

##### Storage Media Security (**物理存储设备的安全问题**)

There are several concerns when it comes to the security of secondary storage devices:

1. Data may remain on secondary storage devices even after it has been erased. This condition is known as data remanence. Utilities are available that can retrieve files from a disk even after they have been deleted or reformatted. If you truly want to remove data from a secondary storage device, you must use a specialized utility designed to overwrite all traces of data on the device (commonly called sanitizing) or damage or destroy it beyond possible repair.
2. A traditional zeroization wipe is less effective for SSDs because bad blocks are likely not overwritten.
3. Secondary storage devices are also prone to theft. Economic loss is not the major factor (after all, how much does a backup tape or a hard drive cost?), but the loss of confidential information poses great risks. For this reason, it is important to use full-disk encryption to reduce the risk of an unauthorized entity gaining access to your data. Many HDDs, SSDs, and flash devices offer on-device native encryption.
4. Removable media pose a significant information disclosure risk, so securing them often requires encryption technologies.

| 风险             | 描述                  | 推荐对策                                  |
| ---------------- | --------------------- | ----------------------------------------- |
| **数据残留**     | 擦除不彻底            | 数据擦除/销毁                             |
| **数据泄漏**     | 设备丢失被盗          | 全盘加密                                  |
| **移动介质攻击** | U盘/SD 卡植入恶意代码 | 限制插入端口 + 加密                       |
| **SSD 擦除困难** | 特殊逻辑块无法清除    | 用 SSD-aware 工具进行 sanitize 或销毁设备 |

##### CISSP 典型考点 & 提示

| 考题方向         | 常见问法                                     | 正确选项提示                   |
| ---------------- | -------------------------------------------- | ------------------------------ |
| **存储设备分类** | 哪种是易失性存储？                           | RAM                            |
| **介质处理**     | 磁带被擦除后如何确保数据不被恢复？           | Sanitization（多次擦除或销毁） |
| **存储设备攻击** | 哪种攻击会冷冻内存芯片以读取密钥？           | Cold boot attack               |
| **SSD 擦除问题** | 为什么对 SSD 使用零化方法不安全？            | 无法保证所有块被擦除           |
| **数据泄露防御** | 确保移动硬盘被盗后数据无法读取，哪项最有效？ | 全盘加密                       |

快速记忆口诀：**“残冷转移，全盘加密！”**

代表：

- 数据**残留**风险
- **冷启动**攻击威胁
- **崩溃转储**的内存镜像可被滥用
- 媒体**转移过程泄密**
- 推荐统一措施：**Full-Disk Encryption**

#### Emanation Security

**Emanation Security** 是信息安全中的一个子领域，专注于防止机密信息通过**非预期的电子信号、无线电波或电磁EM（Electromagnetic）辐射泄漏**。

| 术语                  | 含义                                                   |
| --------------------- | ------------------------------------------------------ |
| **Emanation（辐射）** | 设备在运行中产生的电磁信号，可能包含敏感数据           |
| **Van Eck Radiation** | 由显示设备或线路泄露的 EM 辐射，可被监听               |
| **Van Eck Phreaking** | 攻击者利用接收器远程还原原始显示内容或数据的攻击       |
| **TEMPEST**           | 一套美国政府标准和对策体系，用于防止电磁泄露和监听攻击 |

Many electrical devices emanate electrical signals or radiation that can be intercepted and may contain confidential, sensitive, or private data. Obvious examples of emanation devices are wireless networking equipment and mobile phones, but many other devices are vulnerable to emanation interception that you might not expect, including monitors, network cables, modems, and internal or external media drives (hard drives, USB thumb drives, CDs, and so on). With the right equipment, adversaries can intercept electromagnetic or radio frequency signals (collectively known as emanations) from these devices and interpret them to extract confidential data.

The types of countermeasures and safeguards used to protect against emanation attacks are known as TEMPEST countermeasures. **TEMPEST** was originally a government research study aimed at protecting electronic equipment from the electromagnetic pulse (EMP) emitted during nuclear explosions. It has since expanded to a general study of monitoring emanations and preventing their interception.

Simply because of the kinds of electronic components from which they’re built, many computer hardware devices **emit electromagnetic (EM) radiation** during normal operation. The process of communicating with other machines or peripheral equipment creates emanations that can be intercepted. These emanation leaks can cause serious security issues but are generally easy to address.

TEMPEST-derived technology allows the electronic emanations that devices produce (known as **Van Eck radiation**) to be read from a distance (this process is known as **Van Eck phreaking**). TEMPEST eavesdropping or Van Eck phreaking countermeasures include the following:

1. **Faraday Cage** A Faraday cage is a box, mobile room, or entire building designed with an external metal skin, often a wire mesh that fully surrounds an area on all sides. This metal skin acts as an EM absorbing capacitor that prevents electromagnetic signals (emanations) from exiting or entering the area that the cage encloses. Faraday cages can be designed to block specific frequencies while allowing others—for example, blocking Wi-Fi while allowing walkie talkies and mobile phones.

2. **White Noise** White noise simply means broadcasting false traffic to mask and hide the presence of real emanations. White noise can consist of a real signal from another source that is not confidential, a constant signal at a specific frequency, a randomly variable signal, or even a jam signal that causes interception equipment to fail. Although this is similar to jamming devices, the purpose is to convolute the signal only for the eavesdropper, not the authorized user, rather than stopping even valid uses of emanations.
3. **Control Zone** A third type of TEMPEST countermeasure, a control zone, is simply the implementation of both a Faraday cage and white noise generation to protect a specific area in an environment; the rest of the environment is not affected. A control zone can be a room, a floor, or an entire building.

##### TEMPEST 对策详解

| 对策类型                  | 描述                                       | 示例或关键点                     |
| ------------------------- | ------------------------------------------ | -------------------------------- |
| **Faraday Cage**          | 金属屏蔽结构，阻隔或吸收 EM 信号           | 数据中心、SCIF 安全通信房常用    |
| **White Noise（白噪声）** | 引入虚假信号扰乱监听                       | 类似干扰器，但不影响正常用户使用 |
| **Control Zone**          | 综合 Faraday Cage + 白噪声，用于高安全区域 | 例：军事通信室、政府安全机房     |

**注意**：TEMPEST 通常是**物理性、工程性对策**，并非依赖软件配置或防火墙。

In addition to the official TEMPEST countermeasure concepts, shielding, access control, and antenna management can be helpful against emanation eavesdropping. Shielding of cables (networking and otherwise) may be sufficient to reduce or block emanation access. This may be an element included in the manufacture of equipment, such as shielded twisted pair (STP), or may be accomplished by using shielding conduits or just replacing copper network cables with fiber-optic cables.

##### UTP vs STP

| 缩写    | 全称                    | 中文             |
| ------- | ----------------------- | ---------------- |
| **UTP** | Unshielded Twisted Pair | **非屏蔽双绞线** |
| **STP** | Shielded Twisted Pair   | **屏蔽双绞线**   |

| 特性                   | **UTP（非屏蔽）** | **STP（屏蔽）**               |
| ---------------------- | ----------------- | ----------------------------- |
| 是否有电磁屏蔽层       | ❌ 无              | ✅ 有屏蔽层（金属箔或编织网）  |
| 抗 EMI（电磁干扰）能力 | 较弱              | 强                            |
| 成本与安装难度         | 更便宜、安装简单  | 更贵，接地要求更严格          |
| 典型应用场景           | 普通企业/家庭网络 | 高干扰环境（如工厂、机房）    |
| 是否用于电磁安全防护   | 否                | 是，可作为**TEMPEST对策**之一 |

**为什么 STP 与 CISSP 安全有关？**

因为**电磁泄露（EMI、RFI）不仅会干扰通信质量，还可能导致数据泄漏**。攻击者可以通过监听电磁信号来重建网络传输数据，形成 **旁路攻击（Side-Channel Attack）**。

因此，CISSP 在物理与网络安全章节中，会特别提到：

- **UTP 安装方便，但不适用于高安全等级场景**
- **STP 可用于防止**：
  - 电磁干扰（EMI）
  - 射频干扰（RFI）
  - 电磁窃听（如 Van Eck 攻击）

##### 光纤 vs STP

虽然 STP 能防止泄露，但**光纤（Fiber Optic）**是最佳安全选择，因为：

- 它通过 **光信号** 传输，不产生电磁信号
- 无法被传统 EM 监听设备截获
- 属于完全物理隔离的传输方式

##### 其他有效的电磁防护措施

| 方法                    | 描述                              | 特点                           |
| ----------------------- | --------------------------------- | ------------------------------ |
| **Shielded Cabling**    | 使用**屏蔽双绞线（STP）**或光纤   | 减少或阻断 EMI（电磁干扰）泄露 |
| **Access Control**      | 防止未经授权者接近关键设备        | 属于物理访问控制的一部分       |
| **Antenna Management**  | 控制无线设备天线功率与方向性      | 减少不必要的信号外泄范围       |
| **Physical Separation** | 将高敏设备置于远离窗户/外墙的地方 | 低成本但有效的辅助策略         |

##### CISSP 考试重点 & 易混陷阱提示

| 考点                           | 说明                                | 易错点提示                         |
| ------------------------------ | ----------------------------------- | ---------------------------------- |
| **TEMPEST 是什么？**           | 一组用于防止电磁泄露的标准          | 并非加密协议！是物理性安全框架     |
| **Van Eck 攻击属于哪类攻击？** | **旁路攻击（Side Channel Attack）** | 常和缓存侧信道攻击等混淆           |
| **Faraday Cage 是什么？**      | 电磁信号屏蔽工具                    | 不影响内部设备工作，但屏蔽外部监听 |
| **STP vs UTP**                 | STP 提供 EMI 屏蔽                   | UTP 无 EMI 防护，易受干扰          |
| **光纤替代铜线的优势？**       | 几乎不泄露电磁信号，抗监听强        | 属于物理安全增强手段               |

##### 快速记忆口诀：「**范艾克噪场盾，电磁泄露沉**」

- **范**：Van Eck Radiation
- **艾克**：Phreaking（监听还原技术）
- **噪**：白噪声扰乱监听
- **场**：控制区（Control Zone）
- **盾**：Faraday Cage（EM 防护盾）
- **电磁泄露沉**：EM 信号沉没，数据更安全！

#### Input and Output Devices 输入/输出设备安全风险总结

Input and output devices can present security risks to a system. Security professionals should be aware of these risks and ensure that appropriate controls are in place to mitigate them.

##### Monitors（显示器）

| 安全风险                         | 说明                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| **电磁泄露**                     | 尤其是旧式 CRT 显示器，可被 TEMPEST/Van Eck 技术远程还原显示内容 |
| **肩窥攻击（Shoulder Surfing）** | 通过肉眼或摄像头偷窥屏幕内容，适用于所有屏幕（包括移动设备） |

📝 **考试易混点**：

- Shoulder surfing ≠ TEMPEST。前者是**视觉偷窥**，后者是**EM监听**。

TEMPEST technology can compromise the security of data displayed on a monitor. Generally, legacy cathode ray tube (CRT) monitors are more prone to radiate significantly, whereas most modern monitors leak much less (some claim not enough to reveal critical data); this includes liquid crystal display (LCD), light-emitting diode (LED), organic light-emitting diode (OLED), and quantum dot OLED (QLED).

It is arguable that the biggest risk with any monitor is still shoulder surfing or telephoto lenses on cameras. The concept that someone can see what is on your screen with their eyes or a video camera is known as shoulder surfing. Don’t forget shoulder surfing is a concern for desktop displays, laptop displays, tablets, and mobile phones.

##### Printers**（打印机）**

| 风险类别         | 描述                                               |
| ---------------- | -------------------------------------------------- |
| **物理打印泄露** | 打印后未及时取走，或物理防护不足，易被窃取         |
| **打印缓存风险** | 多功能打印机可能将文档缓存在硬盘中                 |
| **网络攻击**     | 打印机常暴露在网络中，缺乏系统加固，易被远程利用   |
| **旧式传真漏洞** | 有线传真接口可被利用恢复远程命令访问（AT命令漏洞） |

✅ **对策建议**：

- 安全打印（需身份验证）
- 清除打印缓存
- 禁用不必要的传真功能

Printers also represent a security risk that is easy to overlook. Depending on the physical security controls used at your organization, it may be much easier to walk out with sensitive information in printed form than to walk out with a flash drive or magnetic media. If printers are shared, users may forget to retrieve their sensitive printouts, leaving them vulnerable to prying eyes. Many modern printers also store data locally, often on a hard drive, and some retain copies of printouts indefinitely. Printers are usually exposed on the network for convenient access and are often not designed to be secure systems.

Concerns should also apply to multifunction printers (MFPs), especially those that include fax capabilities and that are network attached (whether wired or wireless). In 2018, researchers discovered that it is still possible to take over control of a computer system over a public switched telephone network (PSTN) line using ancient AT commands supported by modems and fax modems/machines. If you don’t always need fax capabilities, don’t leave the telephone line plugged in. If you do need always available fax capabilities, use a standalone fax machine.

##### Keyboards/Mice**（输入设备）**

| 风险类型           | 描述                                           |
| ------------------ | ---------------------------------------------- |
| **TEMPEST**        | 无线/有线键盘均可能泄露电磁信号                |
| **硬件键盘记录器** | 小型物理装置可植入键盘线路，实现**键盘记录**   |
| **无线窃听**       | 蓝牙或无线键鼠信号可被拦截，若未加密则风险极高 |

📌 **考试角度理解**：这是**旁路攻击（side-channel attack）**的一种。

Keyboards, mice, and similar input devices are not immune to security vulnerabilities either. All of these devices are vulnerable to TEMPEST monitoring. Also, keyboards are vulnerable to less sophisticated bugging. A simple device can be placed inside a keyboard or along its connection cable to intercept all the keystrokes that take place and transmit them to a remote receiver using a radio signal. This has the same effect as TEMPEST monitoring but can be done with much less expensive gear. Additionally, if your keyboard and mouse are wireless, including Bluetooth, their radio signals can be intercepted.

##### Modems**（调制解调器）**

| 风险类别         | 描述                                                     |
| ---------------- | -------------------------------------------------------- |
| **绕过边界防御** | 老式拨号调制解调器提供“外部直接连接”入口，绕过防火墙/VPN |
| **隐蔽泄密通道** | 内部人员可利用调制解调器创建“隐秘数据外传通道”           |
| **复古攻击**     | 使用 AT 命令等可重新激活隐藏通信端口                     |

🔒 **应对建议**：

- 禁用或淘汰所有未授权调制解调器
- 管理端口（如 RJ-11）与设备物理接口的使用
- 启用网络行为监测系统识别“非预期流量模式”

With the advent of ubiquitous broadband and wireless connectivity, modems are becoming a scarce legacy computer component. If your organization is still using older equipment, there is a chance that a modem is part of the hardware configuration. Modems allow users to create uncontrolled access points into your network. In the worst case, if improperly configured, they can create extremely serious security vulnerabilities that allow an outsider to bypass all your perimeter protection mechanisms and directly access your network resources. At best, they create an alternate egress channel that insiders can use to funnel data outside your organization. But keep in mind that these vulnerabilities can be exploited only if the modem is connected to an operational telephone landline.

You should seriously consider an outright ban on modems in your organization’s security policy unless you truly need them for business reasons. In those cases, security officials should know the physical and logical locations of all modems on the network, ensure that they are correctly configured, and make certain that appropriate protective measures are in place to prevent their illegitimate use.

#### Firmware (固件安全)

##### **Firmware 基础**

| 项目         | 说明                                            |
| ------------ | ----------------------------------------------- |
| **Firmware** | ROM/EEPROM/Flash 上的低层嵌入式软件             |
| **用途**     | 控制硬件基本运行逻辑，如 BIOS/打印机/IoT        |
| **更新方式** | Flashing，可能被滥用为攻击载体（见：phlashing） |

Firmware (also known as microcode) is a term used to describe software that is stored in a ROM or an EEPROM chip. This type of software is changed infrequently (actually, never, if it’s stored on a true ROM chip as opposed to an EEPROM or flash chip) and often drives the basic operation of a computing device.

Many hardware devices, such as printers and modems, need some limited set of instructions and processing power to complete their tasks while minimizing the burden placed on the OS itself. In many cases, these “mini” OSs are entirely contained in firmware chips onboard the devices they serve. Firmware is commonly used by mobile devices, Internet of Things (IoT) equipment, edge computing devices, fog computing devices, and industrial control systems.

##### BIOS vs UEFI（启动固件演进）

| 项目           | BIOS （Basic input/output system） | UEFI（Unified Extensible Firmware Interface） |
| -------------- | ---------------------------------- | --------------------------------------------- |
| **架构**       | 传统 x86，16位                     | CPU 独立、支持 GUI 与网络                     |
| **驱动支持**   | 固定驱动                           | 动态驱动加载                                  |
| **启动盘支持** | 2.2TB 限制                         | 支持大容量盘（>2TB）                          |
| **安全机制**   | 基本启动验证                       | Secure Boot / Measured Boot / 网络启动支持    |

1. **Basic input/output system (BIOS)** is the legacy basic low-end firmware or software embedded in a motherboard’s EEPROM or flash chip. The BIOS contains the OS-independent primitive instructions that a computer needs to start up and load the OS from disk. The BIOS identifies and initiates the basic system hardware components, such as the hard drive, optical drive, and video card, so that the bootstrapping process of loading an OS can begin. In most modern systems, the BIOS has been replaced by UEFI.

2. **Unified Extensible Firmware Interface (UEFI)** provides support for all of the same functions as BIOS with many improvements, such as support for larger hard drives (especially for booting), faster boot times, enhanced security features, and even the ability to use a mouse when making system changes (BIOS was limited to keyboard control only). UEFI also includes a CPU-independent architecture, a flexible pre-OS environment with networking support, measured boot, boot attestation (aka secure boot), and backward and forward compatibility. It also runs CPU-independent drivers (for system components, drive controllers, and hard drives).

The process of updating the UEFI, BIOS, or firmware is known as flashing. If hackers or malware can alter the UEFI, BIOS, or firmware of a system, they may be able to bypass security features or initiate otherwise prohibited activities. There have been a few examples of malicious code embedding itself into UEFI, BIOS, or firmware. There is also an attack known as phlashing, in which a malicious variation of official BIOS or firmware is installed that introduces remote control or other malicious features into a device.

Boot attestation or secure boot is a feature of UEFI that aims to protect the local OS by preventing the loading or installing of device drivers or an OS that is not signed by a preapproved digital certificate. Secure boot thus protects systems against a range of low-level or boot-level malware, such as certain rootkits and backdoors. Secure boot ensures that only drivers and OSs that pass attestation (the verification and approval process accomplished through the validation of a digital signature) are allowed to be installed and loaded on the local system.

Measured boot is an optional feature of UEFI that takes a hash calculation of every element involved in the booting process. The hashes are performed by and stored in the Trusted Platform Module (TPM). If foul play is detected in regard to booting, the hashes of the most recent boot can be accessed and compared against known-good values to determine which (if any) of the boot components have been compromised. Measured boot does not interrupt or stop the process of booting; it just records the hash IDs of the elements used in the boot. Thus, it is like a security camera. It does not prevent a malicious action; it just records whatever occurs in its area of view.

##### UEFI 安全机制详解

| 安全功能                      | 描述                               | 类比                         |
| ----------------------------- | ---------------------------------- | ---------------------------- |
| **Secure Boot（安全启动）**   | 只加载通过签名验证的 OS / 驱动     | 门卫验证身份才能进入         |
| **Measured Boot（度量启动）** | TPM 记录启动元素哈希，用于事后审计 | 监控摄像头录像，供事后分析   |
| **Phlashing 攻击**            | 恶意固件“合法刷入”                 | 持久性后门（在 OS 级别以下） |

📌 **攻击者若控制 UEFI，可绕过 OS 层全部防御**

##### 快速记忆技巧 & 考点口诀

> **“屏肩波泄键盘录，印留网连传真复；闪刷固件藏后门，启动双盾保主机。”**

解释：

- **屏**：Monitor（可电磁泄露）
- **肩**：Shoulder Surfing
- **波泄**：EM 辐射泄露（Van Eck）
- **键盘录**：硬件键盘记录器
- **印留**：打印文件被遗忘
- **网连传真复**：打印/传真设备连接网络，复古攻击如 AT 指令利用
- **闪刷**：Firmware flashing
- **后门**：恶意固件构造持久后门
- **双盾**：Secure Boot + Measured Boot
- **主机**：系统完整性保障核心

## Client-Based Systems

**Client-based vulnerabilities** = 发生在客户端（如浏览器、操作系统、缓存、前端代码）的安全问题，而非服务器。

典型攻击包括：

- **移动代码攻击**（JavaScript、Java applets、ActiveX 等）
- **本地缓存投毒**
- **浏览器漏洞利用**
- **恶意脚本注入（XSS、CSRF）**

这些攻击通常借助合法渠道（网页、插件、邮件、下载等）在客户端执行恶意代码，**即便服务器完全安全也可能中招**。

Client-based vulnerabilities place the user, their data, and their system at risk of compromise and destruction. A client-side attack is any attack that is able to harm a client. Generally, when attacks are discussed, it’s assumed that the primary target is a server or a server-side component. A client-side or client-focused attack is one where the client itself, or a process on the client, is the target. A common example of a client-side attack is a malicious website that transfers malicious mobile code (such as an applet) to a vulnerable browser running on the client. Client-side attacks can occur over any communications protocol, not just Hypertext Transfer Protocol (HTTP). Another potential vulnerability that is client based is the risk of poisoning of local caches.

### 1. Mobile Code

**Applet**：早期常见的嵌入式代码块（如 Java Applet），运行在客户端，执行计算或显示交互。

**JavaScript**：现代网页中最常用的客户端代码，具备逻辑、访问 DOM、网络请求能力。

| 角色   | 好处                     |
| ------ | ------------------------ |
| 客户端 | 响应快、减少对服务器依赖 |
| 服务器 | 降低负载、保护业务逻辑   |

##### 安全风险

| 攻击                        | 描述                                   |
| --------------------------- | -------------------------------------- |
| **恶意 Applet**             | 被篡改执行恶意操作                     |
| **XSS（跨站脚本攻击）**     | 攻击者注入 JS 获取敏感数据             |
| **CSRF（跨站请求伪造）**    | 攻击者诱导用户浏览器执行未授权操作     |
| **Same-Origin Policy 绕过** | 理论上 JS 不应访问其他域，但可以被绕过 |
| **Sandbox 逃逸**            | JS 越权访问系统资源                    |

##### 防护措施

| 层级         | 对策                                                         |
| ------------ | ------------------------------------------------------------ |
| **浏览器端** | 自动更新、禁用高危插件、安装脚本控制扩展（如 NoScript、uBlock） |
| **服务器端** | 实施 CSP（内容安全策略）、使用 JS 安全子集（SES, ADsafe）    |
| **网络层**   | 部署 Web Application Firewall（WAF）过滤异常请求             |

Applets are code objects sent from a server to a client to perform some action. In fact, applets are actually self-contained miniature programs that execute independently of the server that sent them—that is, mobile code. The arena of the web is undergoing constant flux. The use of applets is not as common today as it was in the early 2010s. However, applets are not absent from the web, and most browsers still support them (or still have add-ons present that support them). Thus, even when your organization does not use applets in your internal or public web design, your web browsers could encounter them while surfing the public web.

Imagine a web server that offers a variety of financial tools to web users. One of these tools might be a mortgage calculator that processes a user’s financial information and provides a monthly mortgage payment based on the loan’s principal and term and the borrower’s credit information. Instead of processing this data and returning the results to the client system, the remote web server might send to the local system an applet that enables it to perform those calculations itself. This provides a number of benefits to both the remote server and the end user:

- The processing burden is shifted to the client, freeing up resources on the web server to process requests from more users.
- The client is able to produce data using local resources rather than waiting for a response from the remote server. In many cases, this results in a quicker response to changes in the input data.
- In a properly programmed applet, the web server does not receive any data provided to the applet as input, therefore maintaining the security and privacy of the user’s financial data.

JavaScript is supported by most browsers via a dedicated JavaScript engine. Most of the implementations use sandbox isolation to restrict JavaScript to web-related activities while minimizing its ability to perform general-purpose programming tasks. Also, most browsers default to enforcing the same-origin policy. The same-origin policy prohibits JavaScript code from accessing content from another origin. The origin is typically defined by a combination of protocol (i.e., HTTP vs. HTTPS), domain/IP address, and port number. If other content has any one of these origin elements different from the origin of the JavaScript code, the code will be blocked from accessing that content.

However, there are ways of abusing JavaScript. Hackers can create believable fake websites that look and act like a valid site, including duplicating the JavaScript dynamic elements. But since the JavaScript code is in the HTML document sent to the browser, a malicious hacker could alter that code to perform harmful actions, such as copying or cloning credentials and distributing them to the attacker. Malicious hackers have also found means to breach the sandbox isolation and even violate same-original policies from time to time, so JavaScript should be considered a threat. Whenever you allow code from an unknown and thus untrusted source to execute on your system, you are putting your system at risk of compromise. XSS and XSRF/CSRF can be used to exploit JavaScript support in browsers.

Here are some responses to these risks:

1. Keep browsers updated (client side).
2. Implement JavaScript subsets (such as ADsafe, Secure ECMAScript [SES], or Caja) (server side).
3. Use a content security policy (CSP) that attempts to rigidly enforce same-origin restrictions for most browser-side active technologies (integrated into browsers and referenced by HTML header values).

As with most web applications, insertion attacks are common, so watch out for injection of odd or abusive JavaScript code in the input being received by a web server.

As a client, you may gain some benefit by being behind a web application firewall (WAF) or next-generation firewall (NGFW). We do not recommended disabling JavaScript outright—that would cause most of the web to stop functioning in your browser. Instead, the use of add-ons, browser helper objects (BHOs), and extensions may reduce the risk of JavaScript. Two examples include NoScript for Mozilla Firefox and UBlock Origin for Chrome and Edge (based on Chromium).

### 2. Local Caches - 本地缓存

There are many types of local caches, including DNS cache, ARP cache, and temporary internet files. See Chapter 11 for details about DNS cache and ARP cache abuses.

##### 缓存种类

| 类型               | 说明                         |
| ------------------ | ---------------------------- |
| **DNS 缓存**       | 将域名解析结果保存在本地     |
| **ARP 缓存**       | 保存 IP ⇄ MAC 映射表         |
| **浏览器临时文件** | 保留网页、脚本、图片、视频等 |

##### 缓存安全风险

| 攻击方式                  | 描述                                             |
| ------------------------- | ------------------------------------------------ |
| **Cache Poisoning**       | 在缓存中植入伪造数据或恶意文件                   |
| **Split-Response Attack** | 分裂 HTTP 响应，插入恶意文件至缓存               |
| **DOM-based XSS**         | 使用缓存中的脚本或 HTML 元素触发攻击             |
| **持久化攻击**            | 即便后续访问合法网站，也可能调用被污染的缓存内容 |

##### 防护建议

| 对策                    | 说明                                                     |
| ----------------------- | -------------------------------------------------------- |
| **缩短缓存寿命**        | 缓存内容存储时间越短，被利用的窗口越小                   |
| **禁用预载功能**        | 防止未请求的内容被缓存（preloading）                     |
| **退出清除缓存/Cookie** | 浏览器关闭时自动清空敏感信息                             |
| **自动清理工具**        | 使用脚本或工具定期清除临时文件（如 CCleaner、BleachBit） |

Temporary internet files or the internet files cache is the temporary storage of files downloaded from internet sites that are being held by the client’s utility (typically a browser) for current and possibly future use. Mostly this cache contains website content, but other internet services can use a file cache as well. A variety of exploitations, such as the split-response attack, can cause the client to download content and store it in the cache that was not an intended element of a requested web page. DOM XSS may be able to access and use locally cached files to execute malicious code or exfiltrate data (see Chapter 21). Mobile code scripting attacks could also be used to plant false content in the cache. Once files have been poisoned in the cache, then even when a legitimate web document calls on a cached item, the malicious item will be activated.

Client utilities should be managing the local files cache, but those utilities might not always be doing the best job. Often the defaults are for efficiency and performance, not for security. Consider reconfiguring the cache to only retain files for a short period of time, minimize the cache size, and disable preloading of content. Keep in mind that these changes can reduce browsing performance when on slower or high-latency connections. You may want to configure the browser to delete all cookies and cache upon exit. Although you can typically perform a manual cache wipe, you would have to remember to do that. Another option is to use an automated that can be configured to wipe temporary internet files on a schedule or upon targeted program close.

##### CISSP 考试重点提示

| 考点类别                | 关键问法                        | 正确思维                            |
| ----------------------- | ------------------------------- | ----------------------------------- |
| **客户端攻击面**        | 哪些攻击是面向客户端？          | 移动代码、缓存投毒、XSS             |
| **JavaScript 安全模型** | Same-Origin Policy 起什么作用？ | 限制跨域访问资源                    |
| **CSP 策略**            | 什么能减缓 XSS 风险？           | CSP 头部控制资源加载范围            |
| **缓存中毒风险**        | Split-Response 攻击影响？       | 注入恶意内容进缓存中                |
| **防护措施**            | 防移动代码攻击首选？            | 浏览器更新、脚本隔离、CSP、插件辅助 |

##### 快速记忆口诀： “动码潜藏毒，缓存藏后门；同源是护栏，清理是扫雷。”

解读：

- 动码（Mobile Code）易被篡改，藏有“毒”
- 本地缓存被投毒后，合法内容也变成“后门”
- Same-Origin Policy 是核心“护栏”
- 清理缓存是扫除潜在残留“炸弹”

## Server-Based Systems

在 CISSP 中，**服务器端安全不仅关心服务器本身**，还涉及如下关键目标：

1. **保障数据流的完整性与可用性**
2. **防止过载、阻断和服务中断**
3. **支持多线程/并发计算任务的安全执行**
4. **识别并控制分布式和对等式计算架构中的隐性风险**

### 0. Data Flow Control（数据流控制）

✅ 目标

- 确保数据稳定传输
- 控制节奏、防止拥塞
- 避免数据丢失/重复
- 抵御恶意/非恶意导致的 DoS

⚠️ 风险与应对

| 风险                | 描述                     | 对策                           |
| ------------------- | ------------------------ | ------------------------------ |
| **数据过载**        | 接收端无法处理高速数据流 | 使用缓冲、速率限制、QoS        |
| **拥塞攻击**        | 大量连接压垮服务器       | 防火墙、DoS 检测、负载均衡     |
| **延迟/丢包**       | 高并发或网络瓶颈导致     | 负载均衡 + 冗余架构            |
| **服务拒绝（DoS）** | 资源耗尽型攻击           | 网络/应用层 DoS 防御（如 WAF） |

#### **负载均衡器（Load Balancer）**

> 将请求“智能地”分配到多台服务器

**负载均衡算法示例**：

- Round-robin（轮询）
- Least connections（最少连接）
- Weighted response time（响应时间权重）
- Resource-based（基于 CPU/内存使用率）

📌 **安全重点**：确保负载均衡设备本身安全，防止它成为单点故障或攻击目标。

An important area of server-based concern, which may include clients as well, is the issue of data flow control. Data flow is the movement of data between processes, between devices, across a network, or over communication channels. Management of data flow ensures not only efficient transmission with minimal delays or latency, but also reliable throughput using hashing and confidentiality protection with encryption. Data flow control also ensures that receiving systems are not overloaded with traffic, especially to the point of dropping connections or being subject to a malicious or even self-inflicted denial of service. When data overflow occurs, data may be lost or corrupted or may trigger a need for retransmission. These results are undesirable, and data flow control is often implemented to prevent these issues from occurring. Data flow control may be provided by networking devices, including routers and switches, as well as network applications and services.

A load balancer is used to spread or distribute network traffic load across several network links or network devices. A load balancer may be able to provide more control over data flow. The purpose of load balancing is to obtain more optimal infrastructure utilization, minimize response time, maximize throughput, reduce overloading, and eliminate bottlenecks. Although load balancing can be used in a variety of situations, a common implementation is spreading a load across multiple members of a server farm or cluster. A load balancer might use a variety of techniques to perform load distribution, including random choice, round robin, load/utilization monitoring, and preferencing. See Chapter 12, “Secure Communications and Network Attacks,” for more on load balancing.

A denial-of-service (DoS) attack can be a severe detriment to data flow control. It is important to monitor for DoS attacks and implement mitigations. See Chapter 17, “Preventing and Responding to Incidents,” for a discussion of these attacks and potential defenses.

### 1. Large-Scale Parallel Data Systems - 并行系统

#### 分类与特性

| 类型                      | 描述                                  | 安全/稳定性                          |
| ------------------------- | ------------------------------------- | ------------------------------------ |
| **SMP（对称多处理）**     | 多 CPU/核，**共享 OS 和内存总线**     | 易于集中管理，适用于高 IOPS 场景     |
| **AMP（非对称多处理）**   | 每个处理器**独立运行 OS**、有专属内存 | 灵活性强，适合任务隔离，但管理复杂   |
| **MPP（大规模并行处理）** | 上千台节点共同处理一个任务            | 易于横向扩展，但对协调器依赖大、昂贵 |

🧠 联想记忆：

- **SMP**：多个厨师在同一个厨房同时工作（共享资源）
- **AMP**：多个厨房各自做各自的菜（隔离、可定制）
- **MPP**：一个主厨调度上千个小厨房完成超级复杂大餐（高并发、高成本）

Parallel data systems or parallel computing is a computation system designed to perform numerous calculations simultaneously. But parallel data systems often go far beyond basic multiprocessing capabilities. They often include the concept of dividing up a large task into smaller elements, and then distributing each subelement to a different processing subsystem for parallel computation. This implementation is based on the idea that some problems can be solved efficiently if broken into smaller tasks that can be worked on concurrently. Parallel data processing can be accomplished by using distinct CPUs or multicore CPUs, virtual systems, or any combination of these. Large-scale parallel data systems must also be concerned with performance, power consumption, and reliability/stability issues.

Within the arena of multiprocessing or parallel processing there are several divisions. The first division is between symmetric multiprocessing (SMP) and asymmetric multiprocessing (AMP).

The scenario where a single computer contains multiple processors that are treated equally and controlled by a single OS is called symmetric multiprocessing (SMP). In SMP, processors share not only a common OS but also a common data bus and memory resources. In this type of arrangement, systems may use a large number of processors. The collection of processors works collectively on a single or primary task, code, or project.

In asymmetric multiprocessing (AMP), the processors are often operating independently of one another. Usually, each processor has its own OS and/or task instruction set, as well as a dedicated data bus and memory resources. Under AMP, processors can be configured to execute only specific code or operate on specific tasks (or specific code or tasks are allowed to run only on specific processors; this might be called affinity in some circumstances).

A variation of AMP is massive parallel processing (MPP), where numerous AMP systems are linked together in order to work on a single primary task across multiple processes in multiple linked systems. Some computationally intensive operations, such as those that support the research of scientists and mathematicians, require more processing power than a single OS can deliver. Such operations may be best served by MPP. MPP systems house hundreds or even thousands of processors, each of which has its own OS and memory/bus resources. Some MPPs have over 10 million execution cores. When the software that coordinates the entire system’s activities and schedules them for processing encounters a computationally intensive task, it assigns responsibility for the task to a single processor (not so different from the Master Control Program [MCP] in the popular movie “Tron”). This processor in turn breaks the task up into manageable parts and distributes them to other processors for execution. Those processors return their results to the coordinating processor, where they are assembled and returned to the requesting application. MPP systems are extremely powerful (not to mention extremely expensive!) and are used in a great deal of computing or computational-based research.

Both types of multiprocessing provide unique advantages and are suitable for different types of situations. SMP systems are adept at processing simple operations at extremely high rates, whereas MPP systems are uniquely suited for processing very large, complex, computationally intensive tasks that lend themselves to decomposition and distribution into a number of subordinate parts.

The arena of large-scale parallel data systems is still evolving. It is likely that many management issues are yet to be discovered and solutions to known issues are still being sought. Large-scale parallel data management is likely a key tool in managing big data and will often involve cloud computing (see Chapter 16), grid computing, or peer-to-peer computing solutions.

### 2. Grid Computing（网格计算）

loosely-coupled 分布式计算网络，用“志愿节点”聚合空闲资源完成大任务。

特点

- 参与者可以随时加入/退出
- 节点来源随机、异构
- 处理科学任务：如 SETI@Home、蛋白质折叠模拟等

安全问题

| 风险               | 描述                                                       |
| ------------------ | ---------------------------------------------------------- |
| **数据外泄**       | 工作包内容对所有节点开放，**不适合处理私密/商业数据**      |
| **结果不可控**     | 节点可能掉线、延迟、结果出错，影响结果完整性               |
| **中心化控制风险** | 中央服务器故障或被攻陷，可能导致**任务错配或恶意指令下发** |

📌 考点：**Grid 不适合处理保密性要求高的数据！**

Grid computing is a form of parallel distributed processing that loosely groups a significant number of processing nodes to work toward a specific processing goal. Members of the grid can enter and leave the grid at random intervals. Often, grid members join the grid only when their processing capacities are not being taxed for local workloads. When a system is otherwise in an idle state, it could join a grid group, download a small portion of work, and begin calculations. When a system leaves the grid, it saves its work and may upload completed or partial work elements back to the grid. Many interesting uses of grid computing have developed, including projects seeking out intelligent aliens, performing protein folding, predicting weather, modeling earthquakes, planning financial decisions, and solving for primes.

The biggest security concern with grid computing is that the content of each work packet is potentially exposed to the world. Many grid computing projects are open to the world, so there is no restriction on who can run the local processing application and participate in the grid’s project. This also means that grid members could keep copies of each work packet and examine the contents. Thus, grid projects will not likely be able to maintain secrecy and are not appropriate for private, confidential, or proprietary data.

Grid computing can also vary greatly in computational capacity from moment to moment. Work packets are sometimes not returned, returned late, or returned corrupted. This requires significant reworking and causes instability in the speed, progress, responsiveness, and latency of the project as a whole and with individual grid members. Time-sensitive projects might not be given sufficient computational time to finish by a specific chronological deadline.

Grid computing often uses a central primary core of servers to manage the project, track work packets, and integrate returned work segments. If the central servers are overloaded or go offline, complete failure or crashing of the grid can occur. However, usually when central grid systems are inaccessible, grid members complete their current local tasks and then regularly poll to discover when the central servers come back online. There is also a potential risk that a compromise of the central grid servers could be leveraged to attack grid members or trick grid members into performing malicious actions instead of the intended purpose of the grid community.

### 3. Peer to Peer （P2P网络）

类似 Grid，但没有中央管理；以节点对节点实时互联为基础。

应用场景

- BitTorrent（文件分发）
- Skype/Zoom（VoIP 通信）
- 区块链（分布式账本）

⚠️ 安全问题

| 问题         | 描述                         |
| ------------ | ---------------------------- |
| **版权风险** | 容易成为非法分发渠道         |
| **数据泄露** | 缺乏统一加密或身份验证机制   |
| **难以监管** | 无中央控管，恶意节点难以隔离 |
| **带宽耗尽** | 无限制的数据交换可压垮网络   |

📌 对比记忆：

- **Grid = 有“指挥部”的志愿军队**
- **P2P = 每个节点都自己决定怎么连接谁，不受控制**

Peer-to-peer (P2P) technologies are networking and distributed application solutions that share tasks and workloads among peers. This is similar to grid computing; the primary differences are that there is no central management system and the services are usually provided in real time rather than as a collection of computational power. Common examples of P2P include many VoIP services, BitTorrent (for data/file distribution), and tools for streaming audio/music distribution.

Security concerns with P2P solutions include a perceived inducement to pirate copyrighted materials, the ability to eavesdrop on distributed content, a lack of central control/ oversight/management/filtering, and the potential for services to consume all available bandwidth.

#### CISSP 考试重点提示

| 考点               | 常考点类型                 | 正确理解                       |
| ------------------ | -------------------------- | ------------------------------ |
| **DoS 与流控关系** | 哪种机制可防止系统过载？   | 流控 + 负载均衡器              |
| **Grid vs MPP**    | 哪种更适合高保密计算？     | MPP，因为 Grid 数据外泄风险高  |
| **SMP vs AMP**     | SMP 是共享 OS 和内存的吗？ | ✅ 是，共享一切                 |
| **P2P 安全隐患**   | 为什么 P2P 被认为不安全？  | 缺乏管理/加密，版权争议        |
| **负载均衡目标**   | 负载均衡的核心目的？       | 降低延迟，避免瓶颈，提高稳定性 |

快速记忆口诀

**“SMP 同心干，AMP 分头算；MPP 万众一心搞科研。”**
**“Grid 多人拼图，P2P 没头群舞；负载均衡稳如虎！”**

## Industrial Control Systems 工业控制系统安全

**PLC**（Programmable Logic Controller）
→ 单一设备控制（如装配线上的机械臂）

**DCS**（Distributed Control System）
→ 控制**多个 PLC 设备**，用于工业生产流程自动化
→ 更适合**本地部署、实时控制**

**SCADA**（Supervisory Control and Data Acquisition）
→ 用于**远程监控和控制**广域分布的工业系统
→ 主要做**数据采集与可视化控制**，可连接 DCS 和 PLC

```
单点控制      局域控制            广域管理
   PLC   →   DCS         →      SCADA
 控制一个     控制多个设备         控制整个系统/地理区域
  设备       通信内部PLC等        管理多个DCS与PLC
```

#### 三者功能对比总结表

| 特性                 | **PLC**                          | **DCS**          | **SCADA**                |
| -------------------- | -------------------------------- | ---------------- | ------------------------ |
| 控制范围             | 单一设备                         | 多设备（区域）   | 跨区域、分布式           |
| 是否具备高级流程控制 | ❌                                | ✅                | ❌                        |
| 是否支持远程监控     | ❌                                | 限于局域         | ✅                        |
| 通信对象             | 设备                             | PLC网络          | DCS + PLC网络            |
| 常见场景             | 自动装配线                       | 精细制造/炼油厂  | 电网/输水管网/交通       |
| 安全隐患             | 一旦被植入恶意代码可导致系统瘫痪 | 依赖本地网络保护 | 网络攻击面大，需重点保护 |

#### ICS 安全挑战与历史教训

| 问题                 | 描述                             | 代表事件                    |
| -------------------- | -------------------------------- | --------------------------- |
| **默认不含安全设计** | 老系统无认证、无加密、开放协议   | 老版 SCADA、Modbus          |
| **老旧设备广泛部署** | 无法更新补丁，存在零日漏洞       | 化工/能源站常见             |
| **隔离不彻底**       | 传统认为 OT 与 IT 网络是物理隔离 | 实际常通过 VPN/远程桌面暴露 |
| **Stuxnet 攻击**     | 第一例针对 SCADA 系统的 Rootkit  | 2010 年伊朗核设施事件       |

📌 **Stuxnet** 是一个经典案例，考试中经常用它来考 ICS 与 SCADA 安全问题。

#### ICS 安全加固建议（CISSP角度）

| 分类           | 控制措施                                                     |
| -------------- | ------------------------------------------------------------ |
| **网络层面**   | ICS 网络与企业网络物理/逻辑隔离，使用防火墙、DMZ、空中断开“air gap”策略 |
| **访问控制**   | 强化物理访问控制，逻辑访问使用 MFA、RBAC                     |
| **系统硬化**   | 禁用不必要服务，仅运行必要代码                               |
| **日志与监控** | 所有指令、修改操作需进行完整日志记录与分析                   |
| **补丁与更新** | 尽可能测试更新补丁后部署，或部署前进行网络层加固防护         |
| **终端保护**   | 所有远程访问口应有端点检测（如 EDR）、跳板机管控等机制       |

An industrial control system (ICS) is a form of computer-management device that controls industrial processes and machines, also known as operational technology (OT). ICSs are used across a wide range of industries, including manufacturing, fabrication, electricity generation and distribution, water distribution, sewage processing, and oil refining. There are several forms of ICS, including distributed control systems (DCSs), programmable logic controllers (PLCs), and supervisory control and data acquisition (SCADA).

DCS units are typically found in industrial process plants where the need to gather data and implement control over a large-scale environment from a single location is essential. An important aspect of DCS is that the controlling elements are distributed across the monitored environment, such as a manufacturing floor or a production line, and the centralized monitoring location sends commands out of those localized controllers while gathering status and performance data. A DCS might be analog or digital in nature, depending on the task being performed or the device being controlled. For example, a liquid flow value DCS would be an analog system, whereas an electric voltage regulator DCS would likely be a digital system.

A DCS focuses on processes and is state driven, whereas SCADA focuses on datagathering and is event driven. A DCS is used to control processes using a network of sensors, controllers, actuators, and operator terminals and is able to carry out advanced process control techniques. DCS is more suited to operating on a limited scale, whereas SCADA is suitable for managing systems over large geographic areas.

PLC units are effectively single-purpose or focused-purpose digital computers. They are typically deployed for the management and automation of various industrial electromechanical operations, such as controlling systems on an assembly line or a large-scale digital light display (such as a giant display system in a stadium or on a Las Vegas Strip marquee).

A SCADA system can operate as a standalone device, be networked together with other SCADA systems, or be networked with traditional IT systems. SCADA is often referred to as a human-machine interface (HMI) since it enables people to better understand, oversee, manage, and control complex machine and technology systems. SCADA is used to monitor and control a wide range of industrial processes, but it is not able to carry out advanced process control techniques. SCADA can communicate with PLCs and DCS solutions.

Legacy SCADA systems were designed with minimal human interfaces. Often, they used mechanical buttons and knobs or simple LCD screen interfaces (similar to what you might have on a business printer or a GPS navigation device). However, modern networked SCADA devices may have more complex remote-control software interfaces.

A PLC is used to control a single device in a standalone manner. DCS was used to interconnect several PLCs, but within a limited physical range, in order to gain centralized control, management, and oversight through networking. SCADA expanded this to large-scale physical areas to interconnect multiple DCSs and individual PLCs. For example, a PLC can control a single transformer, a DCS can manage a power station, and SCADA can oversee a power grid.

In theory, the static design of SCADA, PLC, and DCS units and their minimal human interfaces should make the system fairly resistant to compromise or modification. Thus, little security was built into these industrial control devices, especially in the past. But there have been several well-known compromises of industrial control systems in recent years; for example, Stuxnet delivered the first-ever-known rootkit to a SCADA system located in a nuclear facility. Many SCADA vendors have started implementing security improvements into their solutions in order to prevent or at least reduce future compromises. However, in practice, SCADA and ICS systems are still often poorly secured, vulnerable, and infrequently updated, and older versions not designed for security are still in widespread use.

Generally, typical security management and hardening processes can be applied to ICS, DCS, PLC, and SCADA systems to improve on whatever security is or isn’t present in the device from the manufacturer. Common important security controls include isolating networks, limiting access physically and logically, restricting code to only essential application, and logging all activity.

The ISA99 standards development committee has established and is maintaining guidelines for securing ICS, DCS, PLC, and SCADA systems. Much of their work is integrated into the International Electrotechnical Commission’s (IEC) 62443 series of standards. To learn more about these standards, visit www.isa.org and iecee.org. NIST maintains ICS security standards in SP 800-82 (csrc.nist.gov/publications/detail/sp/800-82/ rev-2/final). North American Electric Reliability Corporation (NERC) maintains its own security guides for ICS as part of the Critical Infrastructure Protection (CIP) standards (www.nerc.com/pa/Stand/Pages/CIPStandards.aspx), which are similar to those of European Reference Network for Critical Infrastructure Protection (ERNCIP) (erncipproject.jrc.ec.europa.eu).

#### 标准与规范指南（考试考点）

| 标准组织           | 内容                      | 网址提示                                                    |
| ------------------ | ------------------------- | ----------------------------------------------------------- |
| **ISA/IEC 62443**  | 国际通用 ICS 安全架构标准 | [isa.org](https://www.isa.org/)                             |
| **NIST SP 800-82** | ICS 网络安全指南（美）    | [csrc.nist.gov](https://csrc.nist.gov/)                     |
| **NERC CIP**       | 北美电网安全标准          | [nerc.com](https://www.nerc.com/)                           |
| **ERNCIP**         | 欧洲关键基础设施保护      | [erncip.jrc.ec.europa.eu](https://erncip.jrc.ec.europa.eu/) |

#### CISSP 考试重点提示

| 题型   | 考点                             | 重点                                     |
| ------ | -------------------------------- | ---------------------------------------- |
| 单选题 | 哪种系统适合大规模地理区域控制？ | ✅ SCADA                                  |
| 单选题 | SCADA 最大的安全挑战是什么？     | ✅ 网络暴露/无安全设计                    |
| 多选题 | 加固 ICS 系统的最佳做法？        | ✅ 网络隔离、访问限制、最小权限、日志收集 |
| 场景题 | ICS 被恶意代码控制怎么办？       | ✅ 断网隔离、切换手动控制、调用应急预案   |
| 记忆题 | ISA/IEC 62443 是什么？           | ✅ 工控安全标准                           |

##### 快速记忆口诀

> **“控一机是 PLC，控一厂是 DCS，控全网才是 SCADA。”**
> **“SCADA 最怕连公网，安全要靠隔与控。**

## Distributed Systems

**Distributed Computing Environment (DCE)**：多个互联的计算组件协作完成单一任务的架构。

特性

- 由多个组件组成，但**对用户呈现为统一整体**
- 可能是**同构（homogeneous）\**或\**异构（heterogeneous）**
- 支持并发/异步/容错（fail-soft）
- 通过 **IDL**（接口定义语言）实现跨语言、跨平台通信

应用场景示例

- DNS、SSO、LDAP
- MMORPG（大型多人在线游戏）
- Cloud / SaaS / Blockchain
- Microservices / SOA / Serverless

分布式系统架构举例

| 架构类型                | 描述                       | 示例               |
| ----------------------- | -------------------------- | ------------------ |
| **Client-Server**       | 最基础的一种分布式结构     | Web App、邮件系统  |
| **Three-Tier**          | 表现层、业务层、数据层分离 | 现代网站结构       |
| **Multitier**           | 更复杂的模块化架构         | 微服务、微前端     |
| **P2P**                 | 各节点平等交换资源         | 区块链、BitTorrent |
| **SOA / Microservices** | 独立服务协同执行任务       | 电商后端、金融服务 |

分布式系统的主要安全挑战

| 风险类别              | 具体内容                       | 影响               |
| --------------------- | ------------------------------ | ------------------ |
| **横向移动攻击**      | 一节点被攻陷后可跨组件传播     | 全局失控、数据泄露 |
| **身份伪装 / 冒充**   | 攻击者伪装合法用户或服务       | Bypass、权限提升   |
| **通信监听与篡改**    | 中间人攻击（MITM）或未加密传输 | 机密泄露           |
| **权限管理不统一**    | 不同组件使用不同权限模型       | 零权限越权风险高   |
| **缺乏集中监控/审计** | 分布式架构导致日志难以统一     | 难以溯源、响应延迟 |

A distributed system or a distributed computing environment (DCE) is a collection of individual systems that work together to support a resource or provide a service. Often a DCE is perceived by users as a single entity rather than numerous individual servers or components. DCEs are designed to support communication and coordination among their members in order to achieve a common function, goal, or operation.

Some DCE systems are composed of homogenous members; others are composed of heterogeneous systems. Distributed systems can be implemented to provide resiliency, reliability, performance, and scalability benefits. Most DCEs exhibit numerous duplicate or concurrent components, are asynchronous, and allow for fail-soft or independent failure of components. A DCE is also known as (or at least described as) concurrent computing, parallel computing, and distributed computing. DCE solutions are implemented as client-server architectures (see the previous client and server sections as well as endpoint coverage in Chapter 11), as a three-tier architecture (such as basic web applications), as multitiered architectures (such as advanced web applications), and as peer-to-peer architectures (such as BitTorrent and most cryptocurrency blockchain ledgers (see Chapter 7). DCE solutions are often employed for scientific and medical research projects, in education projects, and in industrial applications requiring extensive computational resources.

DCE forms the backbone of a wide range of modern internet, business, and communication technologies that you might use regularly, including DNS, single-sign on, directory services, massively multiplayer online role-playing games (MMORPGs), mobile networks, and most websites. DCE also makes possible a plethora of advanced technologies such as serviceoriented architecture (SOA), software-defined networking (SDN), microservices, infrastructure as code, serverless computing, virtualization, and cloud services. A DCE typically includes an Interface Definition Language (IDL). An IDL is a language used to define the interface between client and server processes or objects in a distributed system. IDL enables the creation of interfaces between objects when those objects are in varying locations or are using different programming languages; thus, IDL interfaces are language independent and location independent. There are numerous examples of DCE IDLs or frameworks, such as remote procedure calls (RPCs), the Common Object Request Broker Architecture (CORBA), and the Distributed Component Object Model (DCOM).

There are some security issues inherent with DCE. The primary security concern is the interconnectedness of the components. This configuration could allow for error or malware propagation, and if an adversary compromises one component, it may grant them the ability to compromise other components in the collective through pivoting and lateral movement. Other common issues to consider and address include the following:

- Access by unauthorized users
- Masquerading, impersonation, and spoofing attacks of users and/or devices
- Security control bypass or disablement
- Communication eavesdropping and manipulation
- Insufficient authentication and authorization
- A lack of monitoring, auditing, and logging
- Failing to enforce accountability

The issues in this list are not unique to DCE, but they are especially problematic in a distributed system.

Since distributed systems include members that may be distributed geographically, they have a larger potential attack surface than that of a single system. Thus, it is important to consider the collective threats and risks of the individual member components of a DCE as well as the communications interconnections between them. To secure DCE, encryption is needed for storage, transmission, and processing (such as homomorphic encryption). Also, strong multifactor authentication should be implemented. If a strict homogeneous component set is not maintained, heterogenous systems introduce their own risks, whether different OSs are in use or just different versions or patch levels of the same OS. The more varied the DCE components, the more challenging it is to maintain consistent security configuration, enforcement, monitoring, and oversight. If the DCE is so large or broadly distributed as to cross international boundaries, then data sovereignty issues need to be addressed.

### Blockchain

区块链（Blockchain）在分布式系统中的位置

| 特性             | 描述                               |
| ---------------- | ---------------------------------- |
| **不可篡改账本** | 利用哈希链和时间戳保持事务完整性   |
| **共识机制**     | 回滚操作需超过半数节点同意         |
| **应用场景**     | 加密货币、供应链管理、合同管理等   |
| **安全价值**     | 提供数据完整性保障，但不等于保密性 |

**考点提醒**：区块链**防改但不防看**，不能替代加密。

A blockchain is a collection or ledger of records, transactions, operations, or other events that are verified using hashing, timestamps, and transaction data. Each time a new element is added to the record, the whole ledger is hashed again. This system prevents abusive modification of the history of events by providing proof of whether the ledger has retained its integrity.

The concept of blockchain was originally designed as part of the Bitcoin cryptocurrency in 2008. It has since been used because it’s a reliable transactional technology independent of cryptocurrencies.

A distributed ledger or public ledger is hosted by numerous systems across the internet. This provides for redundancy and further supports the integrity of the blockchain as a whole. However, it is possible to reverse, undo, or discard events from the blockchain, but only by reverting to a previous edition of the ledger prior to when the “offending” event was added. But this means all other events since then must be discarded as well. With a public or distributed ledger, this can be accomplished only if a majority (over 50 percent) of the systems supporting/hosting the ledger agree to make the rollback change.

### Data Sovereignty 数据主权

It is the concept that, once information has been converted into a binary form and stored as digital files, it is subject to the laws of the country within which the storage device resides. In light of the growing use of cloud computing and other DCEs, data sovereignty is an important consideration if there are regulations in your industry that require data to remain in your country of origin or if the country of storage has vastly different laws as compared to your country of origin. Data sovereignty can have an impact on privacy, confidentiality, and accessibility of your data.

**一旦数据落地某国，其受该国法律管辖**。

常见影响场景：

- 云服务部署在境外
- GDPR 要求欧盟用户数据不可跨境
- 美国 PATRIOT Act 可要求美国公司提交存储在全球的数据

安全考量

| 领域       | 风险                                       |
| ---------- | ------------------------------------------ |
| **隐私**   | 非母国法律可能允许访问个人数据             |
| **可用性** | 地缘政治因素可能导致数据被强制隔离         |
| **合规性** | 企业可能违反跨境监管政策（如 GDPR, HIPAA） |

CISSP视角：分布式系统的安全措施

| 安全类别           | 对策示例                               |
| ------------------ | -------------------------------------- |
| **认证与授权**     | 强制多因素认证、统一 IAM               |
| **通信安全**       | 使用 TLS / VPN 加密内部通信            |
| **微分段**         | 控制系统间最小连接路径（如使用 SDN）   |
| **集中日志审计**   | 使用 SIEM 收集所有节点的日志           |
| **配置一致性管理** | 自动化配置管理（如 Ansible, Puppet）   |
| **数据加密**       | 存储+传输+处理（如同态加密）一体化保护 |
| **主权合规管理**   | 数据地理标签 + 云服务提供商 SLA 审查   |

CISSP 考试重点提示

| 题型   | 考法                           | 正确理解                         |
| ------ | ------------------------------ | -------------------------------- |
| 场景题 | 某组件被攻陷，哪类风险最严重？ | 横向移动 / 权限绕过              |
| 单选题 | 区块链最核心的安全属性是？     | ✅ 数据完整性                     |
| 多选题 | 分布式系统安全重点措施有哪些？ | ✅ 加密、统一认证、配置管理、审计 |
| 概念题 | 什么是数据主权？               | 数据受存储地法律控制             |
| 对比题 | DCE vs 传统系统的安全挑战？    | ✅ 攻击面更广，管理更难，组件更杂 |

快速记忆口诀

> **“分布式虽强，控制不能忘；链中不可改，传输需加码；数据落哪国，法律别犯错。”**

- 分布式 = 多节点，管理更难
- 区块链 = 不可篡改，但不等于保密
- 主权合规 = 你在哪里存数据，你就受哪里的法律约束

## High-Performance Computing (HPC) Systems 高性能计算系统

HPC = 针对**大规模复杂计算或实时数据处理**需求设计的超高速计算平台。

### 应用场景

| 领域     | 示例                            |
| -------- | ------------------------------- |
| 科学研究 | 气候模拟、宇宙模拟、药物设计    |
| 工业工程 | CAD/CAE、模拟仿真、制造流程优化 |
| 商业分析 | 高频交易、大数据分析、3D建模    |
| 人工智能 | 神经网络训练、自然语言处理      |
| 医疗健康 | 基因序列分析、癌症检测          |

### 架构三要素

| 组件                       | 描述                             | 安全风险                   |
| -------------------------- | -------------------------------- | -------------------------- |
| **计算资源（Compute）**    | 多核心 CPU/GPU、大规模分布式系统 | 单点漏洞、越权计算滥用     |
| **网络能力（Networking）** | 低延迟高带宽互连                 | 拒绝服务攻击、数据窃听     |
| **存储容量（Storage）**    | 快速读取大数据集                 | 数据泄露、残留、合规性问题 |

⚠️ **性能瓶颈 → 安全瓶颈**：慢速 I/O 或网络不仅影响效率，也会拖慢防护检测响应。

High-performance computing (HPC) systems are computing platforms designed to perform complex calculations or data manipulations at extremely high speeds. Super computers and MPP solutions are common examples of HPC systems. HPC systems are used when real-time or near-real-time processing of massive data is necessary for a particular task or application. These applications can include scientific studies, industrial research, medical analysis, societal solutions, and commercial endeavors.

Many of the products and services we use today, including mobile devices and their apps, IoT devices, ICS solutions, streaming media, voice assistants, 3D modeling and rendering, and AI/ML calculations, all depend on HPC to exist. As the population of internet and computing devices increase, as the datasets being collected continue to increase exponentially, and as new uses of that data and those devices are conceived, HPC will be in even greater demand in the future.

An HPC solution is composed of three main elements: compute resources, network capabilities, and storage capacity. Each element must be able to provide equivalent capabilities in order to optimize overall performance. If storage is too slow, then data cannot be fed to the application processing on the compute resources. If networking capacity is not sufficient, then users of a resource will experience latency or even a benign denial of service (DoS).

### RTOS（Real-Time Operating System）

RTOS = 针对“实时响应”需求设计的操作系统，**以确定性响应速度为核心目标**。

#### 两种实时性

| 类型                         | 描述                               | 示例                        |
| ---------------------------- | ---------------------------------- | --------------------------- |
| **硬实时（Hard Real-Time）** | 必须在确定时间内响应，否则后果严重 | 飞控系统、自动驾驶          |
| **软实时（Soft Real-Time）** | 一定延迟可容忍，尽量减少延迟即可   | 数位笔、音频播放、AR/VR渲染 |

#### 两种调度机制

| 类型           | 描述                                   |
| -------------- | -------------------------------------- |
| **事件驱动型** | 根据任务优先级动态切换（高优先级抢占） |
| **时间共享型** | 根据时钟中断、时间片轮转调度           |

A concept related to HPC is that of the real-time OS (RTOS). Often HPCs implement RTOS compute capability or otherwise attempt to achieve real-time processing and operations.

A real-time operating system (RTOS) is designed to process or handle data as it arrives on the system with minimal latency or delay. An RTOS is usually stored on read-only memory (ROM) and is designed to operate in a hard real-time or soft real-time condition. A hard real-time solution is for mission-critical operations where delay must be eliminated or minimized for safety, such as autonomous cars. A soft real-time solution is used when some level of modest delay is acceptable under typical or normal conditions, as it is for most consumer electronics, such as the delay between a digitizing pen and a graphics program on a computer.

RTOSs can be event-driven or time-sharing. An event-driven RTOS will switch between operations or tasks based on preassigned priorities. A time-sharing RTOS will switch between operations or tasks based on clock interrupts or specific time intervals. An RTOS is often implemented when scheduling or timing is the most critical part of the task to be performed.

A security concern using RTOSs is that these systems are often focused and singlepurpose, leaving little room for security. They often use custom or proprietary code, which may include unknown bugs or flaws that could be discovered by attackers. An RTOS might be overloaded or distracted with bogus datasets or process requests by malware. When deploying or using RTOSs, use isolation and communication monitoring to minimize abuses.

#### HPC / RTOS 的安全挑战

| 问题                     | 描述                                         | 举措                    |
| ------------------------ | -------------------------------------------- | ----------------------- |
| **系统精简不含安全模块** | RTOS 常常仅包含最基本运行逻辑，无防火墙/认证 | 外部加固、最小可用网络  |
| **专用代码或固件风险**   | 专用硬件使用私有代码，难以检测漏洞           | 代码审计、通信控制      |
| **资源诱骗（数据泛洪）** | 虚假数据或攻击可占满实时处理通道             | 限速机制、隔离系统      |
| **恶意中断干扰**         | 定时攻击扰乱任务调度（软实时风险高）         | 时钟保护、完整性监测    |
| **难以更新补丁**         | 固件/ROM系统更新困难，长期暴露风险           | 网络隔离 + 静态加固设计 |

📌 **考试关注**：RTOS = **确定性 > 功能性**，因此安全模块通常不内建，要额外部署。

#### 与其他系统的对比关系

| 类型                            | 描述               | 调度重点           | 是否实时             |
| ------------------------------- | ------------------ | ------------------ | -------------------- |
| **通用 OS（如 Linux/Windows）** | 多功能、多任务     | 响应尽量快         | ❌                    |
| **RTOS（嵌入式控制系统）**      | 高速实时、任务唯一 | **响应时间恒定**   | ✅                    |
| **HPC 平台（超级计算）**        | 并发大任务处理     | 计算吞吐、数据并行 | 可近实时，但非主目标 |

#### 安全实践建议（CISSP 实战思路）

| 分类             | 控制措施                                         |
| ---------------- | ------------------------------------------------ |
| **网络保护**     | 强隔离、防护 RTOS 控制接口、内网流量加密         |
| **系统加固**     | 移除未使用模块，防止代码注入，固化配置           |
| **输入验证**     | 对 RTOS 输入源进行完整性校验、白名单机制         |
| **资源调度控制** | 使用任务优先级保护关键线程，拒绝低优先级泛滥请求 |
| **异常监测**     | 利用外部监控系统侦测执行偏差、资源异常           |

#### CISSP 考试重点提示

| 考题类型 | 考点                       | 正确理解                           |
| -------- | -------------------------- | ---------------------------------- |
| 场景题   | 自动驾驶系统使用何种 OS？  | ✅ 硬实时 RTOS                      |
| 单选题   | 哪类系统最注重确定性响应？ | ✅ RTOS                             |
| 多选题   | HPC 系统设计三大元素？     | ✅ 计算、网络、存储                 |
| 安全考点 | RTOS 系统的最大风险？      | ✅ 缺乏内建安全性、攻击面小但危险大 |
| 对比题   | RTOS 与一般 OS 最大区别？  | ✅ 响应确定性 vs 功能多样性         |

**“HPC 重吞吐，RTOS 抓时度；超算靠联动，实时靠速度。”**

- HPC = 高吞吐大数据并发
- RTOS = 秒级响应、控制核心设备
- 安全靠加固，不靠原生功能！

## Internet of Things

| 项目     | **IoT（Internet of Things）**        | **Embedded Systems（嵌入式系统）** |
| -------- | ------------------------------------ | ---------------------------------- |
| 概念     | 具有联网能力的智能设备               | 内嵌在设备中的专用控制系统         |
| 独立性   | 可以是独立硬件                       | 通常是集成于设备内部               |
| 联网能力 | ✅（几乎默认接入网络）                | ❌ 可选，常常无网络                 |
| 示例     | 智能摄像头、智能门铃、手环、语音助手 | 微波炉控制板、汽车电控系统         |

📌 **考点提示**：IoT 是“独立、联网、可远程控制”的智能硬件，而嵌入式系统是“内嵌控制”的。

#### IoT 面临的主要安全挑战

| 风险类型            | 描述                        | 案例                 |
| ------------------- | --------------------------- | -------------------- |
| **弱配置/默认密码** | 出厂默认账号常未更改        | Mirai 僵尸网络       |
| **缺乏加密**        | 数据传输无加密              | 语音助手被监听       |
| **无补丁更新机制**  | 固件无法升级                | 漏洞长期暴露         |
| **隐私泄露**        | 传感器/摄像头泄露信息       | 儿童玩具监听隐私     |
| **横向入侵跳板**    | 攻击者控制 IoT 设备进入内网 | 通过打印机攻击企业网 |
| **未隔离的网络**    | 所有设备在同一子网中        | IoT 成为攻击入口     |
| **供应链问题**      | 不受信任厂商，硬件后门      | 便宜摄像头含间谍模块 |

#### 安全部署建议：企业与家庭适用

| 安全措施                        | 描述                                                 |
| ------------------------------- | ---------------------------------------------------- |
| **网络隔离（VLAN/路由器划分）** | 与主业务网断开，三层路由隔离                         |
| **设备硬化**                    | 改默认密码、关闭不必要功能                           |
| **补丁与更新机制**              | 定期检查固件更新、启用自动更新                       |
| **物理访问控制**                | 防止设备被盗用或物理篡改                             |
| **最小权限配置**                | 只开放必要服务端口与 API                             |
| **日志监控**                    | 使用 SIEM 或日志分析系统记录设备行为                 |
| **选择可信厂商**                | 评估安全声明、安全更新历史、安全认证（如 ISO 27001） |

📌 **CISSP 提示**：IoT 安全首要原则就是 **“不信任出厂默认配置”**！

#### 特殊场景：IIoT（工业物联网）

工业物联网（**IIoT**）是 IoT 在工业与基础设施中的进阶版本，常结合 **ICS、DCS、SCADA** 系统。

| 应用领域     | 示例                               |
| ------------ | ---------------------------------- |
| 制造业       | 自动流水线、焊接机械臂、预测性维护 |
| 公共基础设施 | 电网、排水、交通信号控制           |
| 环境感知     | 城市空气/噪声监测、水位传感器      |
| 工业自动化   | 边缘计算 + 云计算优化控制流程      |

#### 安全风险升级

- 与 OT 系统耦合（ICS）
- 连入云服务（云暴露）
- 使用边缘/雾计算（边界模糊）
- 可能跨国部署（数据主权问题）

#### 企业 IoT 典型部署案例：三路由器模型（Three Dumb Routers）

一种家庭或小型组织 IoT 隔离策略，适用于不懂 VLAN 的场景

```
        ┌──────────────┐
        │  Internet    │
        └────┬─────────┘
             ↓
        ┌──────────────┐
        │ Router A (主)│ ← 管理主业务网（办公网络）
        └────┬─────────┘
             ↓
        ┌──────────────┐
        │ Router B     │ ← 客户访客 Wi-Fi
        └────┬─────────┘
             ↓
        ┌──────────────┐
        │ Router C     │ ← IoT 网络（电视、音箱、传感器）
        └──────────────┘
```

📌 **层层隔离，控制信任边界；简单粗暴，却很有效。**

#### IoT 相关CISSP标准

| 组织      | 文档                                                         | 链接               |
| --------- | ------------------------------------------------------------ | ------------------ |
| **NIST**  | [SP 800-213](https://csrc.nist.gov/publications/detail/sp/800-213/final) IoT 安全框架 | IoT Risk Framework |
| **OWASP** | [IoT Top 10](https://owasp.org/www-project-internet-of-things/) | 漏洞清单与缓解建议 |
| **ISO**   | ISO/IEC 30141:2018 IoT 架构参考模型                          | IoT 建模与治理基础 |

#### CISSP 考试重点提示

| 题型   | 考法                         | 正确理解                                 |
| ------ | ---------------------------- | ---------------------------------------- |
| 场景题 | 公司摄像头被入侵，如何防御？ | 网络隔离 + 默认配置检查                  |
| 多选题 | IoT 安全加固方法             | ✅ 网络隔离、最小权限、补丁更新、物理安全 |
| 单选题 | IoT 与嵌入式系统最大区别？   | ✅ 独立联网 vs 嵌入整机结构中             |
| 术语题 | IIoT 属于哪个系统演进？      | ICS / OT 系统结合云计算                  |
| 原则题 | IoT 安全最关键意识？         | ✅ 不信任默认设置，必须手动硬化           |

快速记忆口诀

> **“万物皆可联，默认最危险；连网不隔离，漏洞遍地起。”**
> **“物联网重配置，隔离分网强防御。”**

Smart devices are a range of devices that offer the user a plethora of customization options, typically through installing apps, and may take advantage of on-device or in-the-cloud machine learning (ML) processing. The products that can be labeled “smart devices” are constantly expanding and already include smartphones, tablets, music players, home assistants, extreme sport cameras, virtual reality/augmented reality (VR/AR) systems, and fitness trackers.

The Internet of Things (IoT) is a class of smart devices that are internet-connected in order to provide automation, remote control, or AI processing to appliances or devices. IoT may often perform functions and operate similar to an embedded system, but they are different. An IoT device is almost always a separate and distinct hardware device that is used on its own or in conjunction with an existing system (such as a smart IoT thermostat for a heating, ventilation, and air-conditioning [HVAC] system). An embedded system is one where the computer control component has been integrated into the structure, design, and operation of the larger mechanism, often even built into the same chassis or case.

The security issues related to IoT are often about access and encryption. All too often an IoT device was not designed with security as a core concept or even an afterthought. This has resulted in numerous home and office network security breaches. Additionally, once an attacker has remote access to or through an IoT device, they may be able to access other devices on the compromised network. When electing to install IoT equipment, evaluate the security of the device as well as the security reputation of the vendor. If the device does not have the ability to meet or accept your existing security baseline, then don’t compromise your security just for a flashy gadget.

One possible secure implementation is to deploy a distinct network for the IoT equipment, which is kept separate and isolated from the primary network. This configuration is often known as three dumb routers. Other standard security practices are beneficial to IoT, including keeping systems patched, limiting physical and logical access, monitoring all activity, and implementing firewalls and filtering.

Although we often associate smart devices and IoT with home or personal use, they are also a concern to every organization. This is partly because of the use of mobile devices by employees within the company’s facilities and even on the organizational network.

Another concern is that many IoT or networked automation devices are often used in the business environment. This includes environmental controls, such as HVAC management, air quality control, debris and smoke detection, lighting controls, door automation, personnel and asset tracking, and consumable inventory management and auto-reordering (such as coffee, snacks, printer toner, paper, and other office supplies). Thus, both smart devices and IoT devices are potential elements of a modern business network that need appropriate security management and oversight. For some additional reading on the importance of proper security management of smart devices and IoT equipment, see “NIST Initiatives in IoT”

A common IoT device deployed in a business environment is sensors. Sensors can measure just about anything, including temperature, humidity, light levels, dust particles, movement, acceleration, and air/liquid flow. Sensors can be linked with cyber-physical systems to automatically adjust or alter operations based on the sensor’s measurements, such as turning on the air conditioning when the temperature rises above a threshold. Sensors can also be linked to ICS, DCS, and SCADA solutions.

The precautions related to facility automation devices are the same as for smart devices, IoT, and wearables. Always consider the security implications, evaluate the included or lacking security features, consider implementing the devices in an isolated network away from your other computer equipment, and only use solutions that provide robust authentication and encryption.

Often IoT devices—in fact, almost all hardware and software—will have insecure or weak defaults. Never assume defaults are good enough. Always evaluate the setting and configuration options of acquired IoT products and make changes that optimize security and support business functions. This is especially relevant to default passwords, which must always be changed and verified.

**Industrial Internet of Things (IIoT)** is a derivative of IoT that focuses more on industrial, engineering, manufacturing, or infrastructure level oversight, automation, management, and sensing. IIoT is an evolution of ICS and DCS that integrates cloud services to perform data collection, analysis, optimization, and automation. Examples of IIoT include edge computing and fog computing (see the section “Edge and Fog Computing,” earlier in this chapter).

## Edge and Fog Computing（边缘计算，雾计算）

#### 核心概念对比：Edge vs Fog Computing

| 特征           | **Edge Computing**（边缘计算） | **Fog Computing**（雾计算）    |
| -------------- | ------------------------------ | ------------------------------ |
| **计算位置**   | 在设备本地（网络边缘）         | 在本地网络节点（LAN 层）       |
| **处理模式**   | 分布式、自主处理               | 局部集中式处理                 |
| **延迟性**     | 极低，适合实时响应             | 较低，仍依赖局部中心           |
| **示例设备**   | 智能摄像头、自动驾驶汽车       | 本地服务器、网关、控制器       |
| **适用场景**   | 快速、分布式响应需求场景       | 本地聚合计算与协调场景         |
| **数据流向**   | 处理数据**不出本地设备**       | 数据汇总至**局域中心设备**处理 |
| **与云的关系** | 补充云计算，实现“近端处理”     | 云前缓冲与本地调度层           |

**一句话总结**：

- **Edge = 就地决策，就地处理**
- **Fog = 局域中心智能调度**

#### 架构演进流程图（从中心到边缘）

```
Mainframe → Client/Server → Cloud → Fog → Edge
   |            |            |       |     |
中心计算      分布处理        虚拟集中 本地调度 本地处理
```

**Mainframe**：集中大机房计算

**Client/Server**：服务器分担任务

**Cloud**：虚拟化中心远程计算

**Fog**：LAN 层的协调与决策中心

**Edge**：数据来源处直接完成计算处理

**Edge computing** is a philosophy of network design where data and the compute resources are located as close as possible in order to optimize bandwidth use while minimizing latency. In edge computing, the intelligence and processing are contained within each device. Thus, rather than having to send data off to a master processing entity, each device can process its own data locally. The architecture of edge computing performs computations closer to the data source, which is at or near the edge of the network. This is distinct from performing processing in the cloud on data transmitted from remote locations. Edge computing is often implemented as an element of IIoT (Industrial Internet of Things) solutions, but edge computing is not limited to this type of implementation.

**Edge computing** can be viewed as the next evolution of computing concepts. Originally, computing was accomplished on core mainframe computers where applications were executed on the central system but where controlled or manipulated via thin clients. Then the distributed concept of client/server moved computing out to endpoint devices. This allowed for the execution of decentralized applications (i.e., not centrally controlled) that ran locally on the endpoint system. From there, virtualization led to cloud computing. Cloud computing is a type of centralized application execution on remote data center systems, controlled remotely by endpoints. Finally, edge computing is the use of devices that are close to or at the endpoint where applications are centrally controlled but the actual execution is as close to the user or network edge as possible.

One potential use for edge devices is the deployment of mini-web servers by ISPs to host static or simple pages for popular sites that are located nearer to the bulk of common visitors than the main web servers. This speeds up the initial access to the front page of a popular organization’s web presence, but then subsequent page visits are directed to and served by core or primary web servers that may be located elsewhere. Other examples of edge computing solution include security systems, motion detecting cameras, image recognition systems, IoT and IIoT devices, self-driving cars, optimized content delivery network (CDN) caching, medical monitoring devices, and video conferencing solutions.

**Fog computing** is another example of advanced computation architectures, which is also often used as an element in an IIoT deployment. Fog computing relies on sensors, IoT devices, or even edge computing devices to collect data, and then transfer it back to a central location for processing. The fog computing processing location is positioned in the LAN. Thus, with fog computing, intelligence and processing are centralized in the LAN. The centralized compute power processes information gathered from the fog of disparate devices and sensors.

In short, edge computing performs processing on the distributed edge systems, whereas fog computing performs centralized processing of the data collected by the distributed sensors. Both edge and fog computing can often take advantage of or integrate the use of microcontrollers, embedded devices, static devices, cyber-physical systems, and IoT equipment.

#### 应用场景对比

| 场景            | 推荐架构   | 原因                       |
| --------------- | ---------- | -------------------------- |
| 自动驾驶汽车    | Edge       | 毫秒级响应，不能依赖网络   |
| 工厂设备协调    | Fog        | 多传感器集中控制，统一逻辑 |
| 内容分发（CDN） | Edge       | 靠近用户，提高加载速度     |
| 医疗监测设备    | Edge + Fog | 数据初处理后本地中转分析   |
| 智慧城市摄像头  | Fog        | 管控摄像头、聚合分析       |

#### 安全挑战与策略

##### Edge/Fog 特有风险

| 风险                       | 描述                          |
| -------------------------- | ----------------------------- |
| **分布式攻击面广**         | 每个节点都是潜在攻击入口      |
| **设备安全难统一**         | 使用微控制器/IoT 硬件种类繁多 |
| **缺乏统一认证/更新机制**  | 易被利用为僵尸网络节点        |
| **数据本地处理隐私暴露**   | 本地存储敏感数据容易泄露      |
| **边缘设备不含加密或日志** | 无检测、响应能力              |

#### 安全建议（CISSP导向）

| 控制项                 | 描述                             |
| ---------------------- | -------------------------------- |
| **身份验证统一化**     | 使用集中身份管理（如 IAM + PKI） |
| **零信任架构**         | 每个节点都需独立认证、细粒度授权 |
| **微分段策略**         | 网络与物理隔离，最小连接路径     |
| **日志回传与集中监控** | 所有边缘行为必须上报             |
| **自动更新机制**       | 建立统一 OTA 更新平台            |
| **数据加密**           | 存储+传输+处理三位一体加密机制   |

#### 考试关联知识体系

| 概念                       | 所属模块                  | 示例考点                            |
| -------------------------- | ------------------------- | ----------------------------------- |
| **Edge Computing**         | 物联网、分布式架构        | 哪种架构适合本地快速响应？          |
| **Fog Computing**          | ICS / IIoT / LAN 集中控制 | 什么用于本地传感器聚合处理？        |
| **Cyber-Physical Systems** | 嵌入式、RTOS、智能控制    | RTOS 安装于何处？与 Edge 结合如何？ |
| **Data Locality**          | 数据主权与延迟优化        | 为什么采用边缘处理而非云端？        |

## Embedded Devices(嵌入式设备) and Cyber-Physical Systems (CPS) 

| 概念                             | 定义                                                 | 示例                              |
| -------------------------------- | ---------------------------------------------------- | --------------------------------- |
| **Embedded System**              | 集成在设备中的专用计算组件，用于控制/自动化/远程监控 | 智能打印机、工业焊接臂、医疗设备  |
| **Microcontroller**              | 小型片上计算单元（CPU+存储+I/O）                     | Arduino、Raspberry Pi             |
| **Static System**                | 非持久化、不允许用户修改状态的系统                   | 机场自助值机机、宾馆公共电脑、ATM |
| **Network-Enabled Device**       | 自带联网功能的设备                                   | 智能电视、路由器、机顶盒          |
| **Cyber-Physical System（CPS）** | 控制物理世界的计算系统                               | 自动驾驶、智能家居控制、智能电网  |
| **IIoT**                         | 工业级物联网，用于监测、分析与自动化                 | 工厂传感器与边缘计算网关          |

注意：

- **嵌入式系统 ≠ CPS ≠ IoT**，但三者往往重叠。
- 大多数嵌入式设备是**静态系统（Static）**，不支持动态变更、补丁更新困难。

#### 架构层次图：从通用计算到嵌入式控制

```
┌────────────────────────┐
│ General Purpose Systems│  ⟶  云服务器、台式机、笔记本
└────────────────────────┘
            ↓
┌────────────────────────┐
│ Embedded Systems       │  ⟶  打印机、电视、摄像头
└────────────────────────┘
            ↓
┌────────────────────────┐
│ Cyber-Physical Systems │  ⟶  空调系统、焊接臂、遥控探测车
└────────────────────────┘
            ↓
┌────────────────────────┐
│ IIoT / IoT             │  ⟶  控制系统、智能传感器、远程控制平台
└────────────────────────┘
```

#### 安全风险总览与分层管控

##### 核心风险

| 类型                         | 描述                                    |
| ---------------------------- | --------------------------------------- |
| **无法升级/打补丁**          | 固件更新机制缺失或依赖厂商响应          |
| **默认/硬编码凭据**          | 用户无法更改，攻击者轻易利用            |
| **弱加密或预共享密钥**       | 加密算法落后，秘钥管理差                |
| **资源限制无法部署传统安全** | CPU、内存、电力不足，无法运行防护机制   |
| **攻击入口**                 | 设备可能作为“跳板”进入主网络或用于 DDoS |
| **供应链风险**               | 设备厂商或后端云平台可信度低            |

#### 安全控制措施与建议（CISSP视角）

##### 网络分段 & 隔离

- 使用 **VLAN、空中断网（Air Gap）、隔离子网** 管理嵌入式与静态设备
- 应用 **ISFW（内部分段防火墙）** 控制横向移动风险

##### 身份认证控制

- 拒绝使用默认凭据，强制更换
- 尽可能使用 **设备认证（如 mutual certificate authentication）**

##### 固件与软件管理

- 使用**受控更新流程（manual update）**而非自动推送
- 检查数字签名、来源验证（可使用“wrapper”机制）

##### 日志与监控

- 使用**外部 SIEM** 或日志服务器收集活动信息
- 针对 CPS 设置传感器行为阈值报警

##### 物理 & 逻辑安全

- 避免设备暴露于不可信环境（如公共接入区）
- 施加物理锁定与远程访问限制

#### 设备示例安全分析（考试可能出现）

| 设备                  | 类型              | 风险提示                           |
| --------------------- | ----------------- | ---------------------------------- |
| **智能打印机（MFD）** | 嵌入式 + 网络设备 | 打印任务泄露，远程控制面板存在漏洞 |
| **ATM/值机终端**      | 静态系统          | 用户信息未清除，系统恢复未完全     |
| **Raspberry Pi**      | 微控制器/嵌入式   | 使用公共镜像，系统默认口令易被滥用 |
| **自助医疗设备**      | CPS + IoT         | 数据存储未加密，蓝牙数据广播暴露   |
| **智能摄像头**        | IoT/嵌入式        | 云服务弱认证，后门或监听漏洞       |

#### 考试重点提示

| 考点类型 | 问题样式                       | 正确理解                          |
| -------- | ------------------------------ | --------------------------------- |
| 概念类   | Cyber-Physical System 是什么？ | 控制物理环境的计算系统            |
| 应用类   | 哪些是静态环境示例？           | ✅ ATM、宾馆公共电脑、固定的 kiosk |
| 风险类   | 为什么嵌入式设备难以防护？     | ✅ 资源限制、不可升级、默认口令    |
| 控制类   | 如何保护 IoT/嵌入式设备？      | ✅ 网络隔离、更新审查、最小权限    |
| 拓展类   | 什么是 wrapper？               | ✅ 限制更新渠道的验证封装          |

##### 快速记忆口诀

> **“嵌入物理控，更新难、口令同；不信默认网，隔离是王道。”**

解释：

- 嵌入式设备控制现实世界
- 固件难更新、默认密码泛滥
- 网络不能混用主业务网
- 最安全做法是网络分段和“零信任”

------

##### 总结建议

嵌入式与静态设备的安全管理不同于通用服务器与终端，需要：

- **更细粒度的网络管理**
- **更严格的更新策略**
- **更主动的风险评估**

An embedded system is any form of computing component added to an existing mechanical or electrical system for the purpose of providing automation, remote control, and/or monitoring. The embedded system is typically designed around a limited set of specific functions in relation to the larger product to which it is attached. It may consist of the same components found in a typical computer system, or it may be a microcontroller (an integrated chip with onboard memory and peripheral ports).

Embedded systems can be a security risk because they are generally static systems, meaning that even the administrators who deploy them have no real means to alter the device’s operations in order to address security vulnerabilities. Some embedded systems can be updated with patches from the vendor, but often patches are released months after a known exploit is found in the wild. It is essential that embedded systems be isolated from the internet and from a private production network to minimize exposure to remote exploitation, remote control, or malware compromise.

Security concerns for embedded systems include the fact that most are designed with a focus on minimizing cost and extraneous features. This often leads to a lack of security and difficulty with upgrades or patches. Because an embedded system may be in control of a mechanism in the physical world, a security breach could cause harm to people and property.

#### Microcontrollers

A microcontroller is similar to, but less complex than a system on a chip, or SoC (see Chapter 11). A microcontroller may be a component of an SoC. A microcontroller is a small computer consisting of a CPU (with one or more cores), memory, various input/ output capabilities, RAM, and often nonvolatile storage in the form of flash or ROM/ PROM/EEPROM. Examples include Raspberry Pi, Arduino, and a field-programmable gate array (FPGA).

1. **Raspberry Pi** is a popular example of a 64-bit microcontroller or a single-board computer. These types of microcontrollers provide a small form-factor computer that can be used to add computer control and monitoring almost anything. A Raspberry Pi includes a CPU, RAM, video, and peripheral support (via USB), and some include onboard networking. The Raspberry Pi includes its own custom OS, but dozens of alternative OSs can be installed as a replacement. There is a broad and diverse development community around the Raspberry Pi that is using it as part of science experiments to control coffeemakers.
2. **Arduino** is an open source hardware and software organization that creates singleboard 8-bit microcontrollers for building digital devices. An Arduino has limited RAM, a single USB port, and I/O pins for controlling additional electronics (such as servo motors or LED lights), and does not include an OS. Instead, Arduino can execute C++ programs specifically written to its limited instruction set. Whereas Raspberry Pi is a miniature computer, Arduino is a much simpler device.
3. **A field-programmable gate array (FPGA)** is a flexible computing device intended to be programmed by the end user or customer. FPGAs are often used as embedded devices in a wide range of products, including industrial control systems (ICSs).

### 1. Static Systems

Static systems (aka static environments) is a set of conditions, events, and surroundings that don’t change. In theory, once understood, a static environment doesn’t offer new or surprising elements. A static IT environment is any system that is intended to remain unchanged by users and administrators. The goal is to prevent, or at least reduce, the possibility of a user implementing change that could result in reduced security or functional operation. This is also known as a nonpersistent environment or a stateless system, as opposed to a persistent environment or stateful system, which allows changes and retains them between access events and reboots.

Examples of static systems include the check-in kiosk at the airport, an ATM, and often the complimentary guest computer at a hotel or library. Those guest computers are configured to provide the user with a temporary desktop environment to perform a restricted range of tasks. However, when the user terminates their session due to timeout or logging out, the system discards all the previous sessions information and changes and restores a pristine version of the environment for the next user. Static systems can be implemented in a variety of ways, including using local VMs or remotely accessed VDI (Virtual Desktop Infrastructure).

In technology, static environments are applications, OSs, hardware sets, or networks that are configured for a specific need, capability, or function, and then set to remain unaltered. However, although the term static is used, there are no truly static systems. There is always the chance that a hardware failure, a hardware configuration change, a software bug, a software-setting change, or an exploit may alter the environment, resulting in undesired operating parameters or actual security intrusions.

Sometimes the phrase static OS is used to refer to the concept of a static system/environment or to indicate a slight variation. That variation is that the OS itself is beyond the ability of the user to change but the user can install or use applications. Often, those applications may be limited, restricted, or controlled in order to avoid allowing an application to alter the otherwise static OS. Some potential examples of static OSs would be smart TVs, gaming systems/consoles, or mobile devices where only applications from a vendor-controlled app store can be installed.

### 2. Network-Enabled Devices

Network-enabled devices are any type of device (whether mobile or stationary) that has native network capabilities. This generally assumes the network in question is a wireless type of network, primarily that provided by a mobile telecommunications company. However, it can also refer to devices that connect to Wi-Fi (especially when they can connect automatically), devices that share data connectivity from a wireless telco service (such as a mobile hot spot), and devices with RJ-45 jacks to receive a standard Ethernet cable for a wired connection. Network-enabled devices include smartphones, mobile phones, tablets, smart TVs, settop boxes, or an HDMI-stick streaming-media player (such as a Roku Player, Amazon Fire TV, or Google TV [previously known as Android TV and Chromecast]), network-attached printers, game systems, and much more. Examples of embedded systems include networkattached printers, smart TVs, HVAC controls, smart appliances, smart thermostats, vehicle entertainment/driver assist/self-driving systems, and medical devices. Network-enabled devices may be embedded systems or used to create embedded systems. Network-enabled devices are also often static systems.

### 3. Cyber-Physical Systems

Cyber-physical systems refer to devices that offer a computational means to control something in the physical world. In the past, these might have been referred to as embedded systems, but the category of cyber-physical seems to focus more on the physical world results rather than the computational aspects. Cyber-physical devices and systems are essentially key elements in robotics and sensor networks. Basically, any computational device that can cause a movement to occur in the real world is considered a robotic element, whereas any such device that can detect physical conditions (such as temperature, light, movement, and humidity) is a sensor. Examples of cyber-physical systems include prosthetics to provide human augmentation or assistance, collision avoidance in vehicles, air traffic control coordination, precision in robot surgery, remote operation in hazardous conditions, and energy conservation in vehicles, equipment, mobile devices, and buildings.

Another extension of cyber-physical systems, embedded systems, and network-enabled devices is that of the Internet of Things (IoT). As discussed earlier, IoT is the collection of devices that can communicate over the internet with one another or with a control console in order to affect and monitor the real world. IoT devices might be labeled as smart devices or smart-home equipment. Many of the ideas of industrial environmental control found in office buildings are finding their way into more consumer-available solutions for small offices or personal homes. IoT is not limited to static location equipment but can also be used in association with land, air, or water vehicles or on mobile devices. IoT devices are usually static systems, since they may only run the firmware provided by the manufacturer.

### 4. Elements Related to Embedded and Static Systems

Mainframes are high-end computer systems used to perform highly complex calculations and provide bulk data processing. Older mainframes may be considered static environments because they were often designed around a single task or supported a single mission-critical application. These configurations didn’t offer significant flexibility, but they did provide for high stability and long-term operation.

Modern mainframes are much more flexible and are often used to provide high-speed computation power in support of numerous virtual machines. Each virtual machine can be used to host a unique OS and in turn support a wide range of applications. If a modern mainframe is implemented to provide fixed or static support of one OS or application, it may be considered a static environment.

Game consoles, whether home systems or portable systems, are potentially examples of static systems. The OS of a game console is generally fixed and is changed only when the vendor releases a system upgrade. Such upgrades are often a mixture of OS, application, and firmware improvements. Although game console capabilities are generally focused on playing games and media, modern consoles may offer support for a range of cultivated and third-party applications. The more flexible and open-ended the app support, the less of a static system it becomes.

HVAC can be controlled by an embedded solution (which might be also known as a smart device or an IoT device). Physical security controls protect against physical attacks, whereas logical and technical controls only protect against logical and technical attacks. HVAC is discussed further in Chapter 10.

Many printers are network-attached printers, meaning they can be directly connected to the network without being directly attached to a computer. A network-attached printer serves as its own print server. It may connect to the network via cable or through wireless. Some devices are more than just printers and may include fax, scanning, and other functions. These are known as multifunction devices (MFDs) or MFPs. Any device connected to a network can be a potential breach point. This may be due to flaws in the firmware of the device as well as whether the device uses communication encryption.

An MFD/MFP can be considered an embedded device if it has integrated network capabilities that allow it to operate as an independent network node rather than a direct-attached dependent device. Thus, network-attached printers and other similar devices pose an increased security risk because they often house full-fledged computers within their chassis. Network security managers need to include all such devices in their security management strategy in order to prevent these devices from being the targets of attack, used to house malware or attack tools, or grant outsiders remote-control access. Many MFDs/MFPs have embedded web servers for remote management, which can be a vector of compromise. Also, most MFPs/MFDs (as well as fax machines and copiers) have storage devices where print jobs are stored, which may allow for access or recovery by unauthorized entities.

Surveillance systems include any device that is intended to monitor and track assets and/ or subjects. These can be embedded systems, or they can be dedicated sensors. Examples include security cameras, door open/close sensors, movement sensors, scales in access control vestibules, and smartcard readers.

In-vehicle computing systems, medical systems/devices, aircraft/UAV/drones, and smart meters are all potential examples of embedded, static, network-attached, and cyber-physical systems. These were discussed previously in this chapter.

### 5. Security Concerns of Embedded and Static Systems

Embedded, static, network-enabled, cyber-physical, and specialized systems are usually more limited or constrained based on their design or hardware capabilities compared to typical endpoint, server, and networking hardware. These constraints can have security implications.

Some embedded and specialized systems run on replaceable or rechargeable batteries. Others only receive a small amount of power from a USB plug or special power adapter/converter. These power limitations can restrict the speed of operations, which in turn can limit the execution of security components. If additional power is consumed, the device might overheat. This could result in slower performance, crashing, or destruction.

Most embedded and specialized systems use less-capable CPUs. This is due to cost and power savings or limitations. Fewer computing capabilities means fewer functions, which means fewer security operations.

Many embedded and specialized systems have limited network capabilities. These network capabilities could be limited to wired only or wireless only. Within wireless, the device could be limited to a specific Wi-Fi version, frequency, speed, and/or encryption. Some devices using wireless are limited to special communication protocols, such as Zigbee or Bluetooth Low Energy (BLE).

Many embedded and specialized systems are unable to process high-end encryption. The crypto on these special devices is often limited and may use older algorithms or poor keys, or just lack good key management. Some devices are known to have preshared and/or hardcoded encryption keys.

Some embedded and specialized systems are difficult to patch, whereas others might not even offer patching or upgrading. Without update and patch management, vulnerable code will remain at risk.

Some embedded and specialized systems do not use authentication to control subjects or restrict updates. Some devices use hard-coded credentials. These should be avoided. Only use equipment that allows for customized credentials, and choose devices that support mutualcertificate authentication.

Some embedded and specialized systems have a limited transmission range due to low-power antennae. This can restrict the device’s usefulness or require signal boosting to compensate.

Due to the low cost of some embedded and specialized systems, they might not include necessary security features. Other devices that do include needed security components may be too costly to be considered.

Similar to supply chain issues, when an embedded or specialized system is used, the organization is automatically trusting the vendor of the device and the cloud service behind it. This implied trust may be misguided. Always thoroughly investigate vendors before relying on their product, and even then, segregate specialized systems in their own constrained network segments. See zero trust in Chapter 8.

Based on these constraints and other concerns, security management of embedded and static systems must accommodate the fact that most are designed with a focus on minimizing costs and extraneous features. This often leads to a lack of security mechanisms and difficulty with upgrades or patches.

Static environments, embedded systems, network-enabled devices, cyber-physical systems, high-performance computing (HPC) systems, edge computing devices, fog computing devices, mobile devices, and other limited or single-purpose computing environments need security management. Although they may not have as broad an attack surface and aren’t exposed to as many risks as a general-purpose computer, they still require proper security government. Many of the same general security management principles used over servers and endpoints can be applied to embedded, static, and cyber-physical systems.

Network segmentation involves controlling traffic among networked devices. Complete or physical network segmentation occurs when a network is isolated from all outside communications, which means transactions can occur only between devices within the segmented network. You can impose logical network segmentation with switches using virtual local area networks (VLANs), or through other traffic-control means, including MAC addresses, IP addresses, physical ports, TCP or UDP ports, protocols, or application filtering, routing, and access control management. Network segmentation can be used to isolate embedded devices and static environments in order to prevent changes and/or exploits from reaching them. See Chapter 11 for more on segmentation.

An application firewall is a device, server add-on, virtual service, or system filter that defines a strict set of communication rules for a service and all users. It’s intended to be an application-specific server-side firewall to prevent application-specific protocol and payload attacks. A network firewall is a hardware device, typically called an appliance, designed for general network filtering. A network firewall is designed to provide broad protection for an entire network. An internal segmentation firewall (ISFW) is used to create a network division or segment. Every network needs a network firewall. Many application servers need an application firewall. However, the use of an application firewall generally doesn’t negate the need for a network firewall. You should use firewalls in a series to complement each other, rather than seeing them as competitive solutions. See Chapter 17 for more on firewalls.

Security layers exist where devices with different levels of classification or sensitivity are grouped together and isolated from other groups with different levels. This isolation can be absolute or one-directional. For example, a lower level may not be able to initiate communication with a higher level, but a higher level may initiate with a lower level. Isolation can also be logical or physical. Logical isolation requires the use of classification labels on data and packets, which must be respected and enforced by network management, OSs, and applications. Physical isolation requires implementing network segmentation or air gaps between networks of different security levels. See Chapter 5, “Protecting Security of Assets,” to learn more about managing data and asset classification.

Manual updates should be used in static environments to ensure that only tested and authorized changes are implemented. Using an automated update system would allow for untested updates to introduce unknown security reductions. As with manual software updates, strict control over firmware in a static environment is important. Firmware updates should be implemented on a manual basis, only after thorough testing and review. Firmware version control or oversight of firmware release should focus on maintaining a stable operating platform while minimizing exposure to downtime or compromise.

A wrapper is something used to enclose or contain something else. Wrappers are well known in the security community in relation to Trojan horse malware. A wrapper of that sort is used to combine a benign host with a malicious payload. Wrappers are also used as encapsulation solutions. Some static environments may be configured to reject updates, changes, or software installations unless they’re introduced through a controlled channel. That controlled channel can be a specific wrapper, such as an encrypted connection, mutualcertificate-based authentication, sourced from a preset IP address or domain name, and/or a digital signature. The wrapper may include integrity and authentication features to ensure that only intended and authorized updates are applied to the system.

Even embedded and static systems should be monitored for performance, violations, compliance, and operational status. Some of these types of devices can perform on-device monitoring, auditing, and logging, whereas others may require external systems to collect activity data. Any and all devices, equipment, and computers within an organization should be monitored to ensure high performance and minimal downtime, and to detect and stop violations and abuse.

As with any security solution, relying on a single security mechanism is unwise. Defense in depth uses multiple types of access controls in literal or theoretical concentric circles or layers. This form of layered security helps an organization avoid a monolithic security stance. A monolithic mentality is the belief that a single security mechanism is all that is required to provide sufficient security. With security control redundancy and diversity, a static environment can avoid the pitfalls of a single security feature failing; the environment has several opportunities to deflect, deny, detect, and deter any threat. Unfortunately, no security mechanism is perfect. Each individual security mechanism has a flaw or a workaround just waiting to be discovered and abused by a malicious hacker.

## Specialized Devices

**专用设备**是为**单一目的**或特定行业设计的计算设备，具有明确边界、有限功能和定制系统。

通常具备以下特点：

- 静态、不可变配置
- 多为嵌入式系统
- 有联网功能（网络使其更强大，同时也更脆弱）
- 控制现实世界的行为（CPS特性）

#### 典型专用设备类型及风险一览

| 设备类型            | 功能                       | 安全风险                               |
| ------------------- | -------------------------- | -------------------------------------- |
| **医疗设备**        | 监测或治疗患者，含远程操控 | 网络被攻破可致命（如心律调节器被关闭） |
| **车载系统**        | 控制驾驶/引导/娱乐系统     | 若被接管或植入恶意代码，车辆可失控     |
| **自动驾驶/无人机** | 自动导航/运输/飞行         | 遇到 DoS/信号干扰/远程劫持风险极高     |
| **智能电表**        | 远程测量/监控用电行为      | 可用于窃听生活模式，或被用于入侵电网   |
| **工业机器人**      | 组装、焊接等高精度作业     | 恶意指令可能造成设备损坏或人员受伤     |
| **智能燃气/水表**   | 数据采集与优化供应         | 攻击可造成账单错误、拒绝服务、系统瘫痪 |

#### 案例关联（CISSP 考题风格）

| 场景                 | 题干描述                            | 正确选项                         |
| -------------------- | ----------------------------------- | -------------------------------- |
| 医疗设备             | 一心律调节器默认启用蓝牙远程维护    | 建议禁用不必要的远程连接         |
| 智能车载娱乐系统     | 可通过 USB 安装应用，但缺少认证机制 | 高风险，应实施签名验证和访问控制 |
| 自动化无人机送货系统 | 系统中存在未加密指令传输            | 实施端到端加密与命令签名         |
| 智能电表平台         | 被注入假数据造成能源计费错误        | 引入签名验证与数据完整性检查     |

#### 安全控制策略与防护建议（CISSP 构建角度）

| 控制面         | 安全建议                                                    |
| -------------- | ----------------------------------------------------------- |
| **接入控制**   | 禁用默认账户，启用多因子认证                                |
| **通信安全**   | 所有通信必须加密（TLS、VPN）                                |
| **更新机制**   | 禁用自动更新，采用受控手动更新流程                          |
| **防干扰能力** | 对无人系统构建信号丢失下的“安全降级”策略（如自毁/自动返航） |
| **物理防护**   | 防止端口暴露、接口被接入攻击设备（如 USB 劫持）             |
| **日志与监控** | 外部系统进行行为监控与异常检测（SIEM 集成）                 |
| **零信任架构** | 将设备置于细粒度网络分段，默认拒绝除授权路径外所有通信      |

#### 关联标准参考

| 标准组织       | 标准文档                     | 内容概要                     |
| -------------- | ---------------------------- | ---------------------------- |
| **NIST**       | SP 800-82 / 800-53 / 800-183 | 工业控制系统与 CPS 安全框架  |
| **FDA**        | Medical Device Cybersecurity | 医疗设备网络安全指南（美国） |
| **ISO**        | ISO/IEC 81001-1:2021         | 医疗设备+IT 环境的网络安全   |
| **FAA / EASA** | 无人机/UAV 认证要求          | 控制与通信加密强制要求       |

#### 与其他架构关系

| 系统类型              | 与专用设备关系                           |
| --------------------- | ---------------------------------------- |
| **嵌入式系统**        | 专用设备本质上多为嵌入式系统             |
| **静态系统**          | 多数专用设备为非持久环境（用户无法更改） |
| **CPS**               | 典型控制现实世界的行为（如自动刹车）     |
| **IoT/IIoT**          | 通信能力让它们具有 IoT 架构属性          |
| **Edge Computing**    | 可独立处理边缘感知任务                   |
| **Cloud Integration** | 很多设备将数据回传云端（如智能电表）     |

#### CISSP 考试重点提示

| 类别         | 题型示例                   | 思维导图                      |
| ------------ | -------------------------- | ----------------------------- |
| 安全风险识别 | 医疗设备如何被攻击？       | 网络通信未加密 / 默认凭据     |
| 最佳做法     | 如何保护智能汽车系统？     | 网络隔离 + 本地签名验证       |
| 架构理解     | UAV 属于哪类系统？         | CPS + 自动化系统              |
| 场景分析     | 智能电表遭 DoS 攻击影响？  | 服务中断 + 客户数据错误       |
| 风控框架     | 哪种控制措施适合无人系统？ | Zero Trust + Signal Hardening |

##### 快速记忆口诀

> **“专设设备事关命，默认开启不可用；隔离通信要加密，更新认证重验证。”**

解释：

- 生命相关设备需重点防护（医疗/无人机）
- 默认开放的远程访问是风险
- 通信需要加密，更新流程要签名验证
- 网络必须隔离，不能混用主网

The realm of specialized equipment is vast and is always expanding. Specialized equipment is anything designed for one specific purpose, to be used by a specific type of organization, or to perform a specific function. They may be considered a type of DCS, IoT, smart device, endpoint device, or edge computing system. Some common examples of specialized devices are medical equipment, smart vehicles, autonomous aircraft, and smart meters.

A growing number of medical systems are specialized devices that have been integrated with IoT technology to make them remotely accessible for monitoring and management. This may be a great innovation for medical treatment, but it also has security risks. All computer systems are subject to attack and abuse. All computer systems have faults and failings that can be discovered and abused by an attacker. Although most medical device vendors strive to provide robust and secure products, it is not possible to consider and test for every possibility of attack, access, or abuse. There have already been several instances of medical devices being remotely controlled, disabled, accessed, or attacked with a DoS. When using any medical device, consider whether remote access, wired or wireless, is essential to the medical care it is providing. If not, it may still make sense to disable the network feature of the medical device. Although the breach of a personal computer or smartphone may be inconvenient and/or embarrassing, the breach of a medical device can be life-threatening.

In-vehicle computing systems can include the components used to monitor engine performance and optimize braking, steering, and suspension but can also include in-dash elements related to driving, environment controls, and entertainment. Early in-vehicle systems were static environments with little or no ability to be adjusted or changed, especially by the owner/driver. Modern in-vehicle systems may offer a wider range of capabilities, including linking a mobile device or running custom apps. In-vehicle computing systems may or may not have sufficient security mechanisms. Even if the system is only providing information, such as engine performance, entertainment, and navigation, it is important to consider what, if any, security features are included in the solution. Does it connect to cloud services? Are communications encrypted? How strong is the authentication? Is it easily accessible to unauthorized third parties? If the in-vehicle computing system is controlling the vehicle, which might be called automated driving or self-driving, it is even more important that security be a major design element of the system. Otherwise, a vehicle can be converted from a convenient means of transference to a box of death.

Automated pilot systems have been part of aircraft for decades. In most of the airplanes that you have flown on, a human pilot was likely only in full control of the craft during takeoff and landing, and not always even then. For most of the flight, the autopilot system was likely in control of the aircraft. The military, law enforcement, and hobbyists have been using uncrewed aerial vehicles (UAVs) or drones for years, but usually under remote control. Now, with flight automation systems, drones can take off, fly to a destination, and land fully autonomously. There are even many retail businesses experimenting with, and in some countries implementing, drone delivery of food and/or other packages. The security of automated aircraft, drones, and UAVs is a concern for all of us. Are these systems secure against malware infection, signal disruption, remote control takeover, AI failure, and remote code execution? Does the drone have authenticated connections to the authorized control system? Are the drone’s communications encrypted? What will the aircraft do in the event that all contact with the control system is blocked through DoS or signal jamming? A compromised drone could result in the loss of your pizza, a damaged product, a few broken shingles, or severe bodily injury.

A smart meter is a remotely accessible electrical meter. It allows the electricity provider to track energy use remotely. Some smart meters grant the customer the ability to view collected statistics as well. Third-party smart meters can be installed in a building that can identify equipment, appliances, and devices from their energy consumption signatures. These types of smart meters can track energy use by device and provide guidance on minimizing energy consumption.

## Microservices

微服务是一种将单一应用拆解为多个**独立部署、互相通信的服务单元**的软件架构。

| 特征           | 描述                                       |
| -------------- | ------------------------------------------ |
| **单一职责**   | 每个微服务只执行一项具体任务               |
| **松耦合**     | 各服务间依赖最小，接口调用完成交互         |
| **可独立部署** | 每个微服务可由不同团队用不同语言实现与部署 |
| **快速迭代**   | 支持 Agile、CI/CD 流程开发                 |
| **典型场景**   | 电商订单系统、金融清算服务、用户推荐服务等 |

#### 与 SOA（面向服务架构）的关系

| 对比项     | **SOA**      | **Microservices**         |
| ---------- | ------------ | ------------------------- |
| 架构粒度   | 粗           | 细（聚焦功能）            |
| 通信机制   | 通常使用 ESB | 通过轻量级 API（如 REST） |
| 部署模式   | 集中式       | 分布式（容器化）          |
| 技术栈依赖 | 常统一       | 可异构（语言/平台多样）   |

📌 **总结**：**微服务是 SOA 的微粒度演进版**，更灵活、更适合现代 DevOps/Cloud 环境。

#### 微服务架构的主要安全挑战

| 风险点               | 描述                           | 应对措施                                 |
| -------------------- | ------------------------------ | ---------------------------------------- |
| **API 攻击面扩大**   | 每个服务需暴露接口，增加暴露点 | 实施 API Gateway、认证、限速             |
| **认证与授权碎片化** | 每个服务可能使用不同机制       | 引入统一身份管理服务（SSO、OAuth）       |
| **通信数据泄露**     | 微服务间通信若未加密，风险高   | 全链路加密（mTLS）                       |
| **配置失控**         | 快速迭代可能带来配置不一致     | 使用“基础架构即代码”（IaC） + 配置管理   |
| **依赖链攻击**       | 组件复用，供应链风险暴露       | 签名验证、SBOM（软件物料清单）           |
| **日志审计困难**     | 分布式环境日志分散             | 集中日志收集与 SIEM 监控                 |
| **服务互信过度**     | 默认信任服务内部通信           | 实现 **Zero Trust 微分段（微服务网格）** |

#### Microservices 与 API 的关系

- **Microservices 是架构设计方式**
- **API 是接口规范与通信桥梁**

每个微服务都必须通过一个或多个 API 对外暴露功能。因此：

| API 安全控制 | 关键技术                        |
| ------------ | ------------------------------- |
| 身份认证     | OAuth 2.0 / JWT / API Key       |
| 访问控制     | RBAC / ABAC                     |
| 通信保护     | TLS / mTLS                      |
| 威胁防护     | API Gateway + WAF               |
| 输入验证     | JSON Schema / Payload Filtering |

It is important to evaluate and understand the vulnerabilities in system architectures, especially in regard to technology and process integration. As multiple technologies and complex processes are intertwined in the act of crafting new and unique business functions, new issues and security problems often surface. As systems are integrated, attention should be paid to potential single points of failure as well as to emergent weaknesses in serviceoriented architecture (SOA). An SOA constructs new applications or functions out of existing but separate and distinct software services. The resulting application is often new; thus, its security issues are unknown, untested, and unprotected. All new deployments, especially new applications or functions, need to be thoroughly vetted before they are allowed to go live into a production network or the public internet.

Microservices are an emerging feature of web-based solutions and are derivative of SOA. A microservice is simply one element, feature, capability, business logic, or function of a web application that can be called upon or used by other web applications. It is the conversion or transformation of a capability of one web application into a microservice that can be called upon by numerous other web applications.

Microservices are often created as a means to provide purpose-specific business capabilities through services that are independently deployed. Often, microservices are small and focused on a singular operation, designed with few dependencies, and are based on fast short-term development cycles (similar to Agile). It is also common to deploy microservices based on immutable architecture or infrastructure as code.

Microservices are a popular development strategy because they allow large complex solutions to be broken into smaller self-contained functions. This design also enables multiple programming groups to work on crafting separate elements or microservices simultaneously. The relationship to an application programming interface (API) is that each microservice must have a clearly defined (and secured!) API to allow for I/O between multiple microservices as well as to and from other applications. Microservices are a type of programming or design architecture, whereas APIs are a standardized framework to facilitate communications and data exchange.

### Service Delivery Platform (SDP) 

SDP 是一组用于**创建、部署、运行和管理服务**的框架架构，广泛用于电信、SaaS、VoIP 等场景。

SDP 本质上是微服务 + API + 管理调度 + DevOps 的集中化运营平台。

A service delivery platform (SDP) is a collection of components that provide the architecture for service delivery. SDP is often used in relation to telecommunications, but it can be used in many contexts, including VoIP, Internet TV, SaaS, and online gaming. An SDP is similar to a content delivery network (CDN) (see Chapter 11), as both are designed for the support of and efficient delivery of a resource (such as services of a SDP and multimedia of a CDN). The goal of an SDP is to provide transparent communication services to other content or service providers. Both SDPs and CDNs can be implemented using microservices.

#### CISSP 考试重点提示

| 类型   | 题干                           | 正确选项思维           |
| ------ | ------------------------------ | ---------------------- |
| 定义类 | 微服务与 API 的区别？          | 架构 vs 通信机制       |
| 风险类 | 微服务通信被监听风险？         | 未启用 TLS/mTLS        |
| 控制类 | 保护 API 的最佳方式？          | API Gateway + 身份验证 |
| 架构类 | SDP 的主要用途是？             | 管理服务创建与交付     |
| 场景类 | 某微服务未审计接口调用怎么办？ | 引入集中日志与追踪机制 |

**“微小服务多，接口须锁好；部署快更新，认证不可少。”**
**“微服务靠 API，接口即攻击面；SDP 总调度，集中保安全。”**

#### 实践建议总结表（CISSP 安全视角）

| 控制域     | 安全控制措施                             |
| ---------- | ---------------------------------------- |
| 身份认证   | 使用统一 OAuth、SSO 机制管理访问         |
| 通信安全   | 服务间开启 **mTLS** 双向认证通道         |
| API 管理   | 建立 API Gateway，设置频率限制和调用权限 |
| 最小权限   | 微服务调用间只授予必要调用权限           |
| 零信任策略 | 建立服务网格 + 微分段控制机制            |
| 漏洞管理   | 快速响应 CVE + 集中依赖跟踪（SBOM）      |

## Infra as Code

IaC 是将**基础设施管理自动化为可版本控制的代码**，使服务器、网络设备、存储等硬件资源的配置与变更，像软件开发那样统一管理。

| 特征           | 描述                              |
| -------------- | --------------------------------- |
| **自动化部署** | 通过脚本或模板快速部署/配置环境   |
| **版本控制**   | 使用 Git 等 VCS 工具管理配置变更  |
| **一致性**     | 跨环境部署保持一致（如测试/生产） |
| **可审计性**   | 所有变更都可溯源、审计与回滚      |
| **可测试性**   | 可对 IaC 脚本进行语法与逻辑测试   |

#### 常用工具

| 工具               | 类型     | 功能特点                           |
| ------------------ | -------- | ---------------------------------- |
| **Terraform**      | 声明式   | 云平台中立，广泛支持 AWS/Azure/GCP |
| **Ansible**        | 过程式   | 无 agent，适合配置管理             |
| **Puppet / Chef**  | 声明式   | 适合大规模自动化与合规性检查       |
| **CloudFormation** | AWS 专属 | 支持 JSON/YAML 模板                |

Infrastructure as code (IaC) is a change in how hardware management is perceived and handled. Instead of seeing hardware configuration as a manual, direct hands-on, one-on-one administration hassle, it is viewed as just another collection of elements to be managed in the same way that software and code are managed under DevSecOps (security, development, and operations). With IaC, the hardware infrastructure is managed in much the same way that software code is managed, including: version control, predeployment testing, customcrafted test code, reasonableness checks, regression testing, and consistency in a distributed environment.

This alteration in hardware management approach has allowed many organizations to streamline infrastructure changes so that they occur more easily, more rapidly, more securely and safely, and more reliably than before. IaC often uses definition files and rule sets that are machine readable to quickly deploy new settings and manage hardware consistently and efficiently. These files can be treated as software code in terms of development, testing, deployment, updates, and management. IaC is not just limited to hardware; it can also be used to oversee and manage virtual machines (VMs), storage area networks (SANs), and software-defined networking (SDN). IaC often requires the implementation of hardware management software, such as Puppet. Such solutions provide version control, continuous integration, and code review to the portion of an IT infrastructure that was not able to be managed in this manner in the past.

A derivative of IaC and DCE is software-defined networking (SDN). SDN is the management of networking as a virtual or software resource even though it technically still occurs over hardware. That is the same concept as IaC which treats the management of hardware as concept that can be managed in a means similar to how software can be managed. Similarly, just as DCE is a collection of individual systems that work together to support a resource or provide a service, so to is SDN a collection of hardware and software elements that are designed to provide a virtualization of networking management and control. Please see Chapter 11 for details on software-defined networking (SDN).

##### IaC 安全考点（CISSP 出题重点）

| 风险点                         | 安全建议                            |
| ------------------------------ | ----------------------------------- |
| **配置漂移**（部署后手动修改） | 推行 **不可变架构（immutable）**    |
| **敏感信息泄露**（秘钥硬编码） | 使用 Vault 或 AWS Secrets Manager   |
| **权限过大**                   | 实施最小权限原则（Least Privilege） |
| **代码供应链风险**             | SBOM，代码签名验证，自动化静态分析  |
| **未加密配置存储**             | 加密 IaC 存储库，限制访问范围       |
| **部署代码未经审批**           | 建立 CI/CD 审批流程，强制代码审查   |

#### Immutable Architecture（不可变架构）

一旦部署的服务器/实例不被更改，更新 = 构建新版本 + 替换旧实例
✅ 替换式部署，❌ 原地修改

优点

| 优势                  | 说明                               |
| --------------------- | ---------------------------------- |
| **一致性**            | 没有“雪花”服务器，环境统一         |
| **可预测性**          | 每次部署从零构建，杜绝“部署意外”   |
| **易于审计与回滚**    | 原有实例不变更，随时替换           |
| **配合 CI/CD 更安全** | 每次部署都是自动构建并验证过的结果 |

类比记忆法

- **Pet vs Cattle**：传统服务器像宠物，要悉心照料；不可变架构中的服务器像牛群，坏了就替换
- **Snowflake vs Phoenix**：雪花独一无二、难以复制；凤凰则是每次都从脚本中“重生”，一致且可控

Immutable architecture is the concept that a server never changes once it is deployed. If there is a need to update, modify, fix, or otherwise alter, a new server is built or cloned from the current one, the necessary changes are applied, and then the new server is deployed to replace the previous one. Once the new server is validated, the older server is decommissioned. VMs are destroyed and the physical hardware/system is reused for future deployments.

The benefits of immutable architecture are reliability, consistency, and a predictable deployment process. It eliminates issues common in mutable infrastructures where midstream updates and changes can cause downtime, data loss, or incompatibility.

The mindset of immutable architecture is often described with the analogy of pets versus cattle or snowflakes versus phoenixes. If a server is treated like a pet, when something goes wrong, everyone marshals to the rescue. However, if a server is treated like cattle, when something goes wrong, it is taken out back and shot, and another is brought in to replace it. If a server is managed uniquely, then it is a snowflake and requires specific focus and attention, causing an increase in administrative time and attention, not to mention complexity for the environment. If a server is always built from scratch, then when changes are needed a new system can be created with integrated improvements through automated processes, thus rising from the ashes (of previous decommissioned servers) like a phoenix. This minimizes administrative overhead, reduces deployment time, and maintains consistency in the environment.

##### 与 SDN 的关联性（补充理解）

**SDN（软件定义网络）** 是将网络设备管理抽象化为软件层，与 IaC 一样是“基础设施即代码”的延伸思维：

- IaC 管理 **服务器/存储等资源**
- SDN 管理 **网络配置/流量/安全策略**

它们都是为实现：

- **弹性部署**
- **可版本控制的基础设施**
- **自动化管理 & 安全可控**

## Virtualized Systems

Virtualization technology is used to host one or more OSs within the memory of a single host computer or to run applications that are not compatible with the host OS. This mechanism allows virtually any OS to operate on any hardware. It also allows multiple OSs to work simultaneously on the same hardware. Common examples include VMware Workstation Pro, VMware vSphere and vSphere Hypervisor, VMware Fusion for Mac, Microsoft Hyper-V Server, Oracle VirtualBox, Citrix Hypervisor, and Parallels Desktop for Mac.

Organizations are consistently implementing more virtualization technologies due to the huge cost savings available. For example, an organization may be able to reduce 100 physical servers to just 10 physical servers, with each physical server hosting 10 virtual servers. This reduces HVAC costs, power costs, and overall operating costs.

The hypervisor, also known as the virtual machine monitor/manager (VMM), is the component of virtualization that creates, manages, and operates the virtual machines. The computer running the hypervisor is known as the host OS, and the OSs running within a hypervisor-supported virtual machine are known as guest OSs or virtualized systems.

A type I hypervisor is a native or bare-metal hypervisor (Figure 9.3, top). In this configuration, there is no host OS; instead, the hypervisor installs directly onto the hardware where the host OS would normally reside. Type 1 hypervisors are often used to support server virtualization. This allows for maximization of the hardware resources while eliminating any risks or resource reduction caused by a host OS.

A type II hypervisor is a hosted hypervisor (Figure 9.3, bottom). In this configuration, a standard regular OS is present on the hardware, and then the hypervisor is installed as another software application. Type II hypervisors are often used in relation to desktop deployments, where the guest OSs offer safe sandbox areas to test new code, allow the execution of legacy applications, support apps from alternate OSs, and provide the user with access to the capabilities of a host OS.

Cloud computing is a natural extension and evolution of virtualization, the internet, distributed architecture, and the need for ubiquitous access to data and resources. However, it does have some potential security issues, including privacy concerns, regulation compliance difficulties, use of open versus closed source solutions, adoption of open standards, and whether or not cloud-based data is actually secured (or even securable). See Chapter 16 for details on cloud computing.

Virtualization has several benefits, such as being able to launch individual instances of virtual servers or services as needed, real-time scalability, and being able to run the exact OS version needed for a specific application. Virtualization can also provide a reasonably secure means to continue to operate End-of-life (EOL) and End-of-service-life (EOSL)/end-ofsupport (EOS) OSs to support legacy business applications. Virtualized servers and services are indistinguishable from traditional servers and services from a user’s perspective. Additionally, recovery from damaged, crashed, or corrupted virtual systems is often quick, simply consisting of replacing the virtual system’s main hard drive file with a clean backup version and then relaunching it.

Elasticity refers to the flexibility of virtualization and cloud solutions (see Chapter 16) to expand or contract resource utilization based on need. In relation to virtualization, host elasticity means additional hardware hosts can be booted when needed and then used to distribute the workload of the virtualized services over the newly available capacity. As the workload becomes smaller, you can pull virtualized services off unneeded hardware so that it can be shut down to conserve electricity and reduce heat. Elasticity can also refer to the ability of a VM/guest OS to take advantage of any unused hardware resources on the fly as needed, but then release those resources when they are not needed. For example, a hardware host supporting five VM-based guest OSs may have over 30 percent CPU computational capacity unused. If a process-intensive application is launched within one of the VMs, the additional hardware host CPU capacity could be consumed; then once the application completes its intensive work task, the resource would be released. Elasticity has been a common capability of classic standalone systems for decades, but now with virtualization, the use of resources is shared among more than just a few processes—it can span across multiple VMs on the same hardware host as well as potentially across numerous hardware hosts.

It is also important to understand scalability in relation to elasticity. These terms are similar, but they are describing different concepts. Elasticity is the expansion or contraction of resources to meet current processing needs, whereas scalability is the ability to take on more work or tasks. Usually, scalability is a software characteristic that can handle more tasks or workloads, whereas elasticity is a hardware or platform characteristic where resources are optimized to meet demands of current tasks. A scalable system must also be elastic, but an elastic system does not need to be scalable.

In relation to security, virtualization offers several benefits. It is often easier and faster to make backups of entire virtual systems than the equivalent native hardware-installed system. Snapshots (aka checkpoints) are backups of virtual machines. Plus, when there is an error or problem, the virtual system can be replaced by a snapshot backup in minutes. Malicious code compromise or infection of virtual systems rarely affects the host OS due to the hypervisor’s VM-to-VM and VM-to-host isolation. This allows for safe testing and experimentation.

Virtualization is used for a wide variety of new architectures and system design solutions. Locally (or at least within an organization’s private infrastructure), virtualization can be used to host servers, client OSs, limited user interfaces (i.e., virtual desktops), applications, and more.

### 1. Virtual Software

A virtual application or virtual software is a software product deployed in such a way that it is fooled into believing it is interacting with a full host OS. A virtual (or virtualized) application has been packaged or encapsulated so that it can execute but operate without full access to the host OS. A virtual application is isolated from the host OS so that it cannot make any direct or permanent changes to the host OS. Any changes, such as file writes, configuration file or registry modifications, or system setting alterations are intercepted by the isolation manager and recorded (typically into a single file). This allows the contained software to perceive it has interaction with the OS, without that interaction actually taking place. Thus, the virtualized application executes just like any regularly installed application, but it is only interacting and changing with a virtual representation of the OS, not the actual OS. In many instances, this concept is sandboxing. There are many products that provide software virtualization, including Citrix Virtual Apps, Microsoft App-V, Oracle Secure Global Desktop, Sandboxie, and VMware ThinApp.

In many cases, operating an application in a software virtualization tool can effectively transform an installed application into a portable application. This means the application’s encapsulation and file can be moved to another OS (with the same software virtualization product), where it can execute. It may also be possible to place the application’s encapsulation onto removable media and be able to execute the software from a portable storage device plugged into another computer system.

Some software virtualization solutions enable applications from one OS to be operated on another. For example, Wine allows some Windows software products to be executed on Linux.

The concept software virtualization has evolved into its own virtualization derivative concept known as containerization, which is covered in a later section, “Containerization.”

### 2. Virtualized Networking

The concept of OS virtualization has given rise to other virtualization topics, such as virtualized networks. A virtualized network or network virtualization is the combination of hardware and software networking components into a single integrated entity. The resulting solution allows for software control over all network functions: management, traffic shaping, address assignment, and so on. A single management console or interface can be used to oversee every aspect of the virtual network, a task that required physical presence at each hardware component in the past. Virtualized networks have become a popular means of infrastructure deployment and management by corporations worldwide. They allow organizations to implement or adapt other interesting network solutions, including SDNs, virtual SANs, guest OSs, and port isolation.

Custom virtual network segmentation can be used in relation to virtual machines to make guest OSs members of the same network division as that of the host, or guest OSs can be placed into alternate network divisions. A virtual machine can be made a member of a different network segment from that of the host or placed into a network that only exists virtually and does not relate to the physical network media (effectively an SDN; see Chapter 11).

### 3. Software-Defined Everything

Virtualization extends beyond just servers and networking. Software-defined everything (SDx) refers to a trend of replacing hardware with software using virtualization. SDx includes virtualization, virtualized software, virtual networking, containerization, serverless architecture, infrastructure as code, SDN (Chapter 11), VSAN (Chapter 11), software-defined storage (SDS) (Chapter 11), VDI, VMI, SDV, and software-defined data center (SDDC).

The SDx examples that are not defined elsewhere (either in this chapter or in Chapter 11) are discussed here.

Virtual desktop infrastructure (VDI) is a means to reduce the security risk and performance requirements of end devices by hosting desktop/workstation OS virtual machines on central servers that are remotely accessed by users. Thus, VDI is also known as a virtual desktop environment (VDE). Users can connect to the server to access their desktop from almost any system, including from mobile devices. Persistent virtual desktops retain a customizable desktop for the user. Nonpersistent virtual desktops are identical and static for all users. If a user makes changes, the desktop reverts to a known state after the user logs off. (See the discussion of static systems earlier in this chapter under “Static Systems.”)

The term virtual desktop can refer to at least three different types of technology:

- A remote access tool that grants the user access to a distant computer system by allowing remote viewing and control of the distant desktop’s display, keyboard, mouse, and so on.
- An extension of the virtual application concept encapsulating multiple applications and some form of “desktop” or shell for portability or crossOS operation. This technology offers some of the features/benefits/applications of one platform to users of another without the need for using multiple computers, dual-booting, or virtualizing an entire OS platform.
- An extended or expanded desktop larger than the display being used allows the user to employ multiple application layouts, switching between them using keystrokes or mouse movements.

VDI has been adopted into mobile devices and has already been widely used in relation to tablets and laptop computers. It is a means to retain storage control on central servers, gain access to higher levels of system processing and other resources, and allow lower-end devices access to software and services beyond their hardware’s capacity. This has led to virtual mobile infrastructure (VMI), where the OS of a mobile device is virtualized on a central server. Thus, most of the actions and activities of the traditional mobile device are no longer occurring on the mobile device itself. This remote virtualization allows an organization greater control and security than when using a standard mobile device platform. It can also enable personally owned devices to interact with the VDI without increasing the risk profile.

A thin client is a computer or mobile device with low to modest capability or a virtual interface that is used to remotely access and control a mainframe, virtual machine, VDI, or VMI. Thin clients were common in the 1980s when most computation took place on a central mainframe computer. Today, thin clients are being reintroduced as a means to reduce the expenses of high-end endpoint devices where local computation and storage are not required or are a significant security risk. A thin client can be used to access a centralized resource hosted on premises or in the cloud. All processing/storage is performed on the server or central system, so the thin client provides the user with display, keyboard, and mouse/touchscreen functionality.

Software-defined visibility (SDV) is a framework to automate the processes of network monitoring and response. The goal is to enable the analysis of every packet and make deep intelligence-based decisions on forwarding, dropping, or otherwise responding to threats. SDV is intended to benefit companies, security entities, and managed service providers (MSPs). The goal of SDV is to automate detection, reaction, and response. SDV provides security and IT management with oversight into all aspects of the company network, both on-premises and in the cloud, with an emphasis on defense and efficiency. SDV is another derivative of IaC.

Software-defined data center (SDDC) or virtual data center (VDC) is the concept of replacing physical IT elements with solutions provided virtually, and often by an external third party, such as a cloud service provider (CSP). SDDC is effectively another XaaS concept, namely IT as a service (ITaaS). It is similar to infrastructure as a service (IaaS), and thus some claim it is nothing more than a marketing or advertising term of misdirection.

#### Services Integration

Services integration, cloud integration, systems integration, and integration platform as a service (iPaaS) is the design and architecture of an IT/IS solution that stitches together elements from on-premises and cloud sources into a seamless productive environment. The goals of services integration are to eliminate data silos (a situation where data is contained in one area and thus inaccessible to other applications or business units), expand access, clarify processing visibility, and improve functional connectivity of onsite and offsite resources. This can also be viewed as an example of SDDC. See Chapter 16 for more on cloud services.

### 4. Virtualization Security Mangement

The primary software component in virtualization is a hypervisor. The hypervisor manages the VMs, virtual data storage, and virtual network components. As an additional layer of software on the physical server, it represents an additional attack surface. If an attacker can compromise a physical host, the attacker can potentially access all of the virtual systems hosted on the physical server. Administrators often take extra care to ensure that virtual hosts are hardened.

Although virtualization can simplify many IT concepts, it’s important to remember that many of the same basic security requirements still apply. Virtualization doesn’t lessen the security management requirements of an OS. Thus, patch management is still essential.

For example, each VM’s guest OS still needs to be updated individually. Updating the host system doesn’t update the guest OSs. Also, don’t forget that you need to keep the hypervisor updated as well.

When using virtualized systems, it’s important to protect the stability of the host. This usually means avoiding using the host for any purpose other than hosting the virtualized elements, especially in a server-focused deployment. If host availability is compromised, the availability and stability of the virtual systems are also compromised.

Additionally, organizations should maintain backups of their virtual assets. Many virtualization tools include built-in tools to create full backups of virtual systems and create periodic snapshots, allowing relatively easy point-in-time restores.

Virtualized systems should be security tested. The virtualized OSs can be tested in the same manner as hardware installed OSs, such as with vulnerability assessment and penetration testing.

VM sprawl occurs when an organization deploys numerous virtual machines without an overarching IT management or security plan in place. Although VMs are easy to create and clone, they have the same licensing and security management requirements as a metal-installed OS. Uncontrolled VM creation can quickly lead to a situation where manual oversight cannot keep up with system demand. To prevent or avoid VM sprawl, a policy for developing and deploying VMs must be established and enforced. This should include establishing a library of initial or foundation VM images that are to be used to develop and deploy new services. In some instances, VM sprawl relates to the use of lower-powered equipment that results in poorly performing VMs. VM sprawl is a virtual variation of server sprawl and could allow for virtual shadow IT. 、

VM escaping occurs when software within a guest OS is able to breach the isolationprotection provided by the hypervisor in order to violate the container of other guest OSs or to infiltrate a host OS. Several VM escape vulnerabilities have been discovered in a variety of hypervisors. Fortunately, the vendors have been fast to release patches. For example, Virtualized Environment Neglected Operations Manipulation (VENOM) (CVE-2015-3456) was able to breach numerous VM products that employed a compromised open source virtual floppy disc driver to allow malicious code to jump between VMs and even access the host.

VM escaping can be a serious problem, but steps can be implemented to minimize the risk. First, keep highly sensitive systems and data on separate physical machines. An organization should already be concerned about over-consolidation resulting in a single point of failure; running numerous hardware servers so that each supports a handful of guest OSs helps with this risk. Keeping enough physical servers on hand to maintain physical isolation between highly sensitive guest OSs will further protect against a VM escape exploit. Second, keep all hypervisor software current with vendor-released patches. Third, monitor attack, exposure, and abuse indexes for new threats to your environment.

#### Server Sprawl and Shadow IT

Server sprawl or system sprawl is the situation where numerous underutilized servers are operating in your organization’s server room. These servers are taking up space, consuming electricity, and placing demands on other resources, but their provided workload or productivity does not justify their presence. This can occur if an organization purchases cheap lower-end hardware in bulk instead of selecting optimal equipment for specific use cases.

Somewhat related to server sprawl is shadow IT.

Shadow IT is a term used to describe the IT components (physical or virtual) deployed by a department without the knowledge or permission of senior management or the IT group. The existence of shadow IT is often due to complex bureaucracy that makes the acquisition of needed equipment overly difficult and time-consuming. Other terms that might be used to refer to shadow IT include embedded IT, feral IT, stealth IT, hidden IT, secret IT, and client IT.

Shadow IT usually does not follow company security policy, and it might not be kept current and updated with patches. Shadow IT often lacks proper documentation, is not under consistent oversight and control, and may not be reliable or fault tolerant. Shadow IT greatly increases the risk of disclosure of sensitive, confidential, proprietary, and personal information to unauthorized insiders and outsiders. Shadow IT can be composed of physical devices, virtual machines, or cloud services.

## Containerization

Containerization is the next stage in the evolution of the virtualization trend for both internally hosted systems and cloud providers and services. A virtual machine–based system uses a hypervisor installed onto the bare metal of the host server and then operates a full guest OS within each virtual machine, and each virtual machine often supports only a single primary application. This is a resource-wasteful design and reveals its origins as separate physical machines.

Containerization or OS-virtualization is based on the concept of eliminating the duplication of OS elements in a virtual machine. Instead, each application is placed into a container that includes only the actual resources needed to support the enclosed application, and the common or shared OS elements are then part of the hypervisor. Some deployments claim to eliminate the hypervisor altogether and replace it with a collection of common binaries and libraries for the containers to call upon when needed. Containerization is able to provide 10 to 100 times more application density per physical server than that provided by traditional hypervisor virtualization solutions.

There are many different technological solutions that are grouped into the concept of containerization. Some refer to the application instances as containers, zones, cells, virtual private servers, partitions, virtual environments, virtual kernels, or jails. Some containerization solutions allow for multiple concurrent applications within a single container, whereas others are limited to one per container. Many containerization solutions allow for customization of how much interaction applications in separate containers is allowed.

## Serverless Architecture

Serverless architecture is a cloud computing concept where code is managed by the customer and the platform (i.e., supporting hardware and software) or server is managed by the cloud service provider (CSP). There is always a physical server running the code, but this execution model allows the software designer/architect/programmer/developer to focus on the logic of their code and not have to be concerned about the parameters or limitations of a specific server. This is also known as function as a service (FaaS).

Applications developed on serverless architecture are similar to microservices, and each function is crafted to operate independently and autonomously. This allows each function to be independently scaled by the CSP (Cloud Service Provider). This is distinct from platform as a service (PaaS), where an entire execution environment or platform is spun up to host an application, and it is always running, consuming resources, racking up costs, even when it is not actively being used. With serverless architecture or FaaS, the functions run only when called and then terminate when their operations are completed, thus minimizing costs.

## Mobile Devices

A device owned by an individual can be referenced using any of these terms: portable device, mobile device, personal mobile device (PMD), personal electronic device or portable electronic device (PED), and personally owned device (POD).

Mobile devices often contain sensitive data such as contacts, text messages, email, scheduling information, and possibly notes and documents. Any mobile device with a camera feature can take photographs of sensitive information or locations. The loss or theft of a mobile device could mean the compromise of personal and/or corporate secrets.

Many mobile devices also support USB connections to perform synchronization of communications and contacts with desktop and/or laptop computers as well as the transfer of files, documents, music, video, and so on. Thus, a mobile device can functionally serve as removable media to enable data exfiltration or transmission of malicious code. See Chapter 16 for more about mobile devices as removable media.

Additionally, mobile devices aren’t immune to eavesdropping. With the right type of sophisticated equipment, most mobile phone conversations can be tapped into—not to mention the fact that anyone within 15 feet can hear you talking. Employees should be coached to be discreet about what they discuss over mobile phones in public spaces.

### Android and iOS

Two of the most widely used device OSs are Android and iOS.

#### Android

Android is a mobile device OS based on Linux, which was acquired by Google in 2005.

In 2008, the first devices hosting Android were made available to the public. The Android source code is made open source through the Apache license, but most devices also include proprietary software. Although it’s mostly intended for use on phones and tablets, Android is being used on a wide range of devices, including televisions, game consoles, digital cameras, microwaves, watches, e-readers, cordless phones, and ski goggles.

The use of Android in phones and tablets allows for a wide range of user customization: you can install Google Play Store apps as well as apps from unknown external sources (such as Amazon’s App Store), and many devices support the replacement of the default version of Android with a customized or alternate version. However, when Android is used on other devices, it can be implemented as something closer to a static system.

Whether static or not, Android has numerous security vulnerabilities. These include exposure to malicious apps, running scripts from malicious websites, and allowing insecure data transmissions.

Improvements are made to Android security as new updates are released. Users can adjust numerous configuration settings to reduce vulnerabilities and risks. Also, users may be able to install apps that add additional security features to the platform.

Security-Enhanced Android (SEAndroid) is a security improvement for Android. SEAndroid is a framework to integrate elements of Security-Enhanced Linux into Android devices. These improvements include adding support for **mandatory access control (MAC)** and **middleware mandatory access control (MMAC)**, reducing privilege daemon vulnerabilities, sandboxing and isolating apps, blocking app privilege escalation, enabling app privilege adjustments both during installation and at runtime, and defining a centralized security policy that can be scrutinized.

#### iOS

iOS is the mobile device OS from Apple that is standard on the iPhone, iPad, and Apple TV. iOS isn’t licensed for use on any non-Apple hardware. Thus, Apple is in full control of the features and capabilities of iOS. However, iOS is not really an example of a static environment, because users can install any of over two million apps from the Apple App Store (although it can be argued that iOS is a static OS.)

### 1. Mobile Device Security Features

#### Mobile Device Management

Administrators register employee devices with a mobile device management (MDM) system. Mobile device management (MDM) is a software solution to the challenging task of managing the myriad mobile devices that employees use to access company resources. The MDM system monitors and manages mobile devices and ensures that they are kept up-to-date. The goals of MDM are to improve security, provide monitoring, enable remote management, and support troubleshooting. Many MDM solutions support a wide range of devices and can operate across many service providers. You can use MDM to push or remove apps, manage data, and enforce configuration settings both over the air (across a carrier network) and over Wi-Fi connections. MDM can be used to manage company-owned devices as well as personally owned devices.

Unified endpoint management (UEM) is a type of software tool that provides a single management platform to control mobile, PC, IoT, wearables, ICS, and other devices. UEM is intended to replace MDM and enterprise mobility management (EMM) products, by combining the features of numerous products into one solution.

#### Device Authentication

Authentication on or to a mobile device is often fairly simple, especially for mobile phones and tablets. This is known as device authentication. However, a swipe or pattern access shouldn’t be considered true authentication. Whenever possible, use a password, provide a **personal identification number (PIN)**, offer your eyeball or face for recognition, scan your fingerprint, provide a **USB key**, or use a proximity device such as a **near-field communication (NFC)** or **radio-frequency identification (RFID)** ring or tile. These means of device authentication are much more difficult for a thief to bypass if properly implemented. It’s also prudent to combine device authentication with device encryption to block access to stored information via a connection cable.

A strong password would be a great idea on a phone or other mobile device if locking the phone provided true security. But most mobile devices aren’t that secure, so even with a strong password, the device may still be accessible over Bluetooth, wireless, or a USB cable. If a specific mobile device blocked access to the device when the system lock was enabled, this would be a worthwhile feature to set to trigger automatically after a period of inactivity or manual initialization (often related to screen lock). This benefit is usually obtained when you enable both a device password and storage encryption.

#### Full-Device Encryption

Some mobile devices, including portable computers, tablets, and mobile phones, may offer full-device encryption (FDE). Many mobile devices either are pre-encrypted or can be encrypted by the user/owner. Once a mobile device is encrypted, the user’s data is protected whenever the screen is locked, which causes the physical data port on the device to be disabled. This prevents unauthorized access to data on the device through a physical cable connection as long as the screen remains locked.

If most or all of the storage media of a device can be encrypted, this is usually a worthwhile feature to enable. However, encryption isn’t a guarantee of protection for data, especially if the device is stolen while unlocked or if the system itself has a known backdoor attack vulnerability.

#### Communication Protection

Voice encryption may be possible on mobile devices when **Voice over Internet Protocol (VoIP)** services are used. VoIP service between computer-like devices is more likely to offer an encryption option than VoIP connections to a traditional landline phone or typical mobile phone. When a voice conversation is encrypted, eavesdropping becomes worthless because the contents of the conversation are undecipherable.

This concept of communication protection should be applied to any type of transmission, whether video, text, or data. There are numerous apps that provide encrypted communications, many using standard and well-respected cryptography solutions, such as the Signal protocol (see Chapters 6 and 7 for more on encryption).

#### Remote Wiping

Remote wipe or remote sanitization is to be performed if a device is lost or stolen. A remote wipe lets you delete all data and possibly even configuration settings from a device remotely. The wipe process can be triggered over mobile phone service or sometimes over any internet connection (such as Wi-Fi). However, a remote wipe isn’t a guarantee of data security. The wiping trigger signal might not be received by the device. Thieves may be smart enough to prevent connections that would trigger the wipe function while they dump out the data. This could be accomplished by removing the **subscriber identity module (SIM) card,** **disabling Wi-Fi, and/or placing the device in a Faraday cage.**

Additionally, a remote wipe is mostly a deletion operation and resetting the device back to factory conditions. The use of an undelete or data recovery utility can often recover data on a wiped device. To ensure that a remote wipe destroys data beyond recovery, the device should be encrypted (aka full-device encryption [FDE]). Thus, the undelete operation would only be recovering encrypted data, which the attacker should be unable to decipher.

#### Device Lockout

Lockout on a mobile device is similar to account lockout on a company workstation. When a user fails to provide their credentials after repeated attempts, the account or device is disabled (locked out) for a period of time or until an administrator clears the lockout flag.

Mobile devices may offer a device lockout feature, but it’s in use only if a screen lock has been configured. Otherwise, a simple screen swipe to access the device doesn’t provide sufficient security, because an authentication process doesn’t occur. Some devices trigger ever longer delays between access attempts as a greater number of authentication failures occur. Some devices allow for a set number of attempts (such as three) before triggering a lockout that lasts minutes or hours. Other devices trigger a persistent lockout and require the use of a different account or master password/code to regain access to the device. Some devices may even have a maximum number of logon attempts (such as 10), before securely wiping all data on the device and resetting back to factory settings. Be sure to know the exact nature of a device’s lockout mechanism before attempting to guess credentials; otherwise you might inadvertently trigger a security wipe.

#### Screen Locks

A screen lock is designed to prevent someone from casually picking up and being able to use your phone or mobile device. However, most screen locks can be unlocked by swiping across the screen or drawing a pattern. Neither of these is truly a secure operation. These easybypass options may be the default on the device but should be changed to something more secure and resistive of unauthorized access, such as a **PIN, password, or biometric**. Otherwise, it is functioning as a screen saver rather than a secure screen lock.

**Screen locks** may have workarounds on some devices, such as accessing the phone application through the emergency calling feature. And a screen lock doesn’t necessarily protect the device if a malicious hacker connects to it over Bluetooth, wireless, or a USB cable.

Screen locks are often triggered after a timeout period of nonuse. Most devices can be configured to auto-trigger a password-protected screen saver if the system is left idle for a few minutes. Similarly, many tablets and mobile phones can be set to trigger a screen lock and dim or turn off the display after a set time period, such as 30 seconds. The lockout feature ensures that if you leave your device unattended or it’s lost or stolen, it will be difficult for anyone else to be able to access your data or applications. To unlock the device, you must enter valid credentials (see the previous section, “Device Authentication”).

#### GPS and Location Services

The **Global Positioning System (GPS)** is a satellite-based geographical location service. Many mobile devices include a **GPS chip** to support and benefit from localized services, such as navigation, so it’s possible to track those devices. The GPS chip itself is usually just a receiver of signals from orbiting GPS satellites. However, applications on the mobile device can record the GPS location of the device and then report it to an online service. You can use GPS tracking to monitor your own movements, track the movements of others (such as minors or delivery personnel), or track down a stolen device. But for GPS tracking to work, the mobile device must have internet or wireless phone service over which to communicate its location information. Apps are able to provide location-based services as well as reveal the location of the device (and thus its user/owner) to third parties (sometimes without consent). This risk needs to be evaluated in regard to the organizational security policy and relative location-based risks.

Geolocation data is commonly used in navigation tools, authentication services, and many **location-based services, such as offering discounts or coupons to nearby retail stores.**

Location-based authorization policies for controlling access can be used to grant or deny resource access based on where the subject is located. This might be based on whether the network connection is local wired, local wireless, or remote. Location-based policies can also grant or deny access based on MAC address, IP address, OS version, patch level, and/ or subnet in addition to logical or geographical location (which is a feature of both network access control (NAC) (see Chapter 11) and context-aware authentication). Location-based policies should be used only in addition to standard authentication processes, not as a replacement for them.

**Geotagging** is the ability of a mobile device to include details about its location in any media created by the device, such as photos, videos, and social media posts. Mobile devices with location services enabled allow for the embedding of geographical location in the form of latitude and longitude as well as date/time information on photos taken with these devices. This allows an adversary (or angry ex) to view photos from social networking or similar sites and determine exactly when and where a photo was taken.

**Geotagging** can be used for nefarious purposes, such as determining when a person normally performs routine activities. Once a geotagged photo has been uploaded to the internet, a potential cyber-stalker may have access to more information than the uploader intended. This is prime material for security-awareness briefs for end users.

##### Other Location Services

The most commonly discussed location service of a mobile device is that of GPS. However, it is important to recognize that there are at least four other location determination services or capabilities in many mobile devices. These include **wireless positioning system (WiPS** or WFPS [Wi-Fi positioning system]), cellular/mobile service tower triangulation, Bluetooth location services, and environmental sensors. WiPS uses the known location of wireless access points/base stations to determine a mobile device’s location. WiPS is often used as a supplement to GPS when sufficient satellite signals are unavailable, such as when underground, inside buildings, or near tall structures. Due to U.S. 911 regulations (which established E911), mobile devices can be located using mobile service tower triangulation. However, E911 location tracking is not as accurate as GPS. iBeacon is a technology developed by Apple to track devices based on their Bluetooth device address and signal properties. Though originally designed to track people inside Apple stores, it is now used in many other contexts by a wide range of organizations to track devices via Bluetooth and their related user/owner. Environmental sensors on many mobile devices include accelerometers, compass, thermometer, altimeter (altitude sensor), and barometric pressure sensors. With this vast range of sensing data, if an initial location of a device is known or can be approximated, then its location at any future point in time can be determined if continuous sensor data is recorded. It is also possible for a device to be located through its camera and microphones, but so far this is not as reliable of a method than the others. This final concept measures light levels, intensity, and color to potentially determine if a device is outside or inside and if located near a window, which based on the time of day, may be able to determine the general area (such as a city) based on light levels caused by the sun’s position in the sky. This can then be combined with monitoring of background noise via the microphone to further refine the location. But this requires extensive knowledge of regional sounds, a massive dataset of noise from across the globe, or access to real-time microphone networks or sensors.

**Geofencing** is the designation of a specific geographical area that is then used to automatically implement features or trigger settings on mobile devices. A geofence can be defined by GPS coordinates, WiPS, or the presence of or lack of a specific wireless signal. A device can be configured to enable or disable features based on a geofenced area, such as an onboard camera or the Wi-Fi capability.

#### Content Management

Content management is the control over mobile devices and their access to content hosted on company systems as well as the control of access to company data stored on mobile devices. Typically, an MCM (mobile content management) system is used to control company resources and the means by which they are accessed or used on mobile devices. An MCM can take into account a device’s capabilities, storage availability, screen size, bandwidth limitations, memory (RAM), and processor capabilities when rendering or sending data to mobile devices.

The goal of a content management system (CMS) for mobile devices is to maximize performance and work benefit while reducing complexity, confusion, and inconvenience. An MCM may also be tied to an MDM to ensure secure use of company data.

A content filter, which may block access to resources, data, or services based on IP address, domain name, protocol, or keyword, is more often implemented as a firewall service rather than as an on-device mechanism. Therefore, content filtering is usually enforced by the network through which the communication is taking place.

#### Application Control

Application control or application management is a device-management solution that limits which applications can be installed onto a device. It can also be used to force specific applications to be installed or to enforce the settings of certain applications in order to support a security baseline or maintain other forms of compliance. Using application control can often reduce exposure to malicious applications by limiting the user’s ability to install apps that come from unknown sources or that offer non-work-related features. This mechanism is often implemented by an MDM. Without application control, users could theoretically install malicious code, run data stealing software, operate apps that reveal location data, or not install business-necessary applications.

**Application allow listing** (previously known as **whitelisting**) is a security option that prohibits unauthorized software from being able to execute. Allow listing is also known as deny by default or implicit deny. In application security, allow listing prevents any and all software, including malware, from executing unless it’s on the preapproved exception list: the allow list. This is a significant departure from the typical device-security stance, which is to allow by default and deny by exception (also known as deny listing or block listing, previously known as blacklisting). Deny listing allows anything and everything, both benign and malicious, to execute by default, unless it is added to the deny list, which prevents it from that point forward.

Due to the growth of malware, an application allow listing approach is one of the few options remaining that shows real promise in protecting devices and data. However, no security solution is perfect, including allow listing. All known allow listing solutions can be circumvented with kernel-level vulnerabilities and application configuration issues.

**Mobile application management (MAM)** is similar to an MDM but focuses only on app management rather than managing the entire mobile device.

#### Push Notifications

Push notification services are able to send information to your device rather than having the device (or its apps) pull information from an online resource. Push notifications are useful in being notified about a concern immediately, but they can also be a nuisance if they are advertising or spam. Many apps and services can be configured to use push and/or pull notifications. Mostly, push notifications are a distraction, but it is possible to perform social engineering attacks via these messages as well as distribute malicious code or links to abusive sites and services.

Push notifications are also a concern in browsers for both mobile devices and PCs. Another issue is that malicious or pernicious notifications may capture a user in a push locker. If the user denies agreement to a push prompt, it may redirect them to a subdomain where another push notification is displayed. If they deny again, then they are redirected again to yet another subdomain, to then see another push notification. This can be repeated indefinitely. Until your browser and/or **host-based intrusion detection system (HIDS)** can detect and respond to push lockers, the only response is to close/terminate the browser and not return to the same URL.

#### Third-Party Application Stores

The **first-party** application (aka app) stores of **Apple iTunes and Google Play** are reasonable sources for apps for use on the typical or standard iOS and Android smartphone or device. For Android devices, the **second-party Amazon Appstore** is also a worthwhile source of apps. However, most other sources of apps for either smart-device platform are labeled as third-party application stores. Third-party app stores often have less rigorous security rules regarding hosting an app. On Android devices, simply enabling a single feature to install apps from unknown sources allows the use of third-party app stores (as well as sideloading; see the section “Sideloading,” later in this chapter). For Apple iOS devices, you are limited to the official iTunes App Store unless you jailbreak or root the device (which is not usually a security recommendation).

When a mobile device is being managed by an organization, especially when using an MDM/UEM/MAM, most third-party sources of apps will be blocked. Such third-party app sources represent a significant increase in risk of data leakage or malware intrusion to an organizational network.

#### Storage Segmentation

Storage segmentation is used to artificially compartmentalize various types or values of data on a storage medium. On a mobile device, storage segmentation may be used to isolate the device’s OS and preinstalled apps from user-installed apps and user data. Some MDMs/ UEMs further impose storage segmentation in order to separate company data and apps from user data and apps. This allows for ownership and rights over user data to be retained by the user, while granting ownership and rights over business data (such as remote wiping) to the organization, even on devices owned by the employee.

With or without storage segmentation, risk can be reduced by minimizing the storage of nonessential data, sensitive data, and personal data (i.e., PII and PHI) on a device. So, even if a device is lost or stolen, the loss potential is kept to a minimum if there is little to no valuable data on the system for an adversary to gain access to.

#### Asset Tracking and Inventory Control

**Asset tracking** is the management process used to maintain oversight over an inventory, such as deployed mobile devices. An asset-tracking system can be passive or active. Passive systems rely on the asset itself to check in with the management service on a regular basis, or the device is detected as being present in the office each time the employee arrives at work. An active system uses a polling or pushing technology to send out queries to devices in order to elicit a response.

You can use asset tracking to verify that a device is still in the possession of the assigned authorized user. Some asset-tracking solutions can locate missing or stolen devices.

Some **asset-tracking solutions** expand beyond hardware inventory management and can oversee the **installed apps, app usage, stored data, and data access on a device**. You can use this type of monitoring to verify compliance with security guidelines or to check for exposure of confidential information to unauthorized entities.

**Inventory control** is the concept of using a mobile device as a means of tracking inventory in a warehouse or storage cabinet. Most mobile devices have a camera. Using a mobile device’s camera, apps that can take photos, scan bar codes, recognize things by shape/design, or interpret Quick Response (QR) codes can be used to track physical goods. Those mobile devices with RFID or NFC capabilities may be able to interact with objects or their containers that have been electronically tagged.

#### Removable Storage

Many mobile devices support removable storage. Some devices support microSD cards, which can be used to expand available storage on a mobile device. However, most mobile phones require the removal of a back plate and sometimes removal of the battery in order to add or remove a storage card. Larger mobile phones, tablets, and laptop computers may support an easily accessible card slot on the side of the device.

Many mobile devices also support external USB storage devices, such as flash drives and external hard drives. These may require a special on-the-go (OTG) cable. USB On-The-Go (OTG) is a specification that allows a mobile device with a USB port to act as a host and use other standard peripheral USB equipment, such as storage devices, mice, keyboards, and digital cameras. USB OTG is a feature that can be disabled via MDM/UEM if it is perceived as a risk vector for mobile devices used within an organization.

In addition, there are mobile storage devices that can provide Bluetooth- or Wi-Fi-based access to stored data through an onboard wireless interface.

Organizations need to consider whether the use of removable storage on portable and mobile devices is a convenient benefit or a significant risk vector. If the former, proper access limitations and use training are necessary. If the latter, then a prohibition of removable storage can be implemented via MDM/UEM.

#### Connection Methods

Mobile devices may support a number of various connection options. These may be network connections that link to an external provider, such as a telco, or the local private network.

For any organization, it is important to consider the scenarios where workers are in need of reliable communications. These may be standard in-office employees, telecommuters, or even those on location at a client’s facility. Only consider deploying those services that can provide reliable and secure (encrypted) communications.

A range of wireless or radio-wave based communication concepts are covered in Chapter 11, including radio frequency identification (RFID), near-field communication (NFC), wireless/Wi-Fi (IEEE 802.11), Bluetooth (IEEE 802.15), and cellular/mobile networks.

#### Disabling Unused Features

Although enabling security features is essential for them to have any beneficial effect, it’s just as important to remove apps and disable features that aren’t essential to business tasks or common personal use. The wider the range of enabled features and installed apps, the greater the chance that an exploitation or software flaw will cause harm to the device and/ or the data it contains. Following common security practices, such as hardening, reduces the attack surface of mobile devices.

#### Rooting or Jailbreaking

Rooting or jailbreaking (the special term for rooting Apple devices) is the action of breaking the digital rights management (DRM) security on the bootloader of a mobile device in order to be able to operate the device with root or full system privileges. Most mobile devices are locked in such a way as to restrict end-user activity to that of a limited user. But a **root user can manipulate the OS, enable or disable hardware features, and install software applications that are not available to the limited user.** Rooting may enable a user to change the core OS or operate apps that are unavailable in the standard app stores. However, this is not without its risks. Operating in rooted status also reduces security, since any executable also launches with full root privileges. Many forms of malicious code cannot gain footing on normal mode devices but can easily take root (pun intended) when the user has rooted or jailbroken their device.

Generally, an organization should prohibit the use of rooted devices on the company network or even access to company resources whenever possible.

It is legal to root a device if you fully own the device, if you are in a one- or two-year contract with a hardware fee, or if you are in a lease-to-own contract and you do not fully own the device until that contract is fulfilled. Legal root does not require a manufacturer, vendor, or telco to honor any warranty. In most cases, any form of system tampering, including rooting, voids your warranty. Rooting may also void your support contract or replacement contract. Rooting is actively suppressed by the telcos, many carriers, and some product vendors, Apple being the main example. A rooted device might be prohibited to operate over a telco network, access resources, download apps, or receive future updates. Thus, though it is often legal to root a device, there are numerous consequences to consider prior to altering a mobile device in that manner.

#### Sideloading

Sideloading is the activity of installing an app on a device by bringing the installer file to the device through some form of file transfer or USB storage method. Most organizations should prohibit user sideloading, because it may be a means to bypass security restrictions imposed by an app store, application allow listing, or the MDM/UEM/MAM. An MDM/UEM/MAMenforced configuration can require that all apps be digitally signed; this would eliminate sideloading and likely jailbreaking as well.

#### Custom Firmware

Mobile devices come preinstalled with a vendor- or telco-provided firmware or core OS. If a device is rooted or jailbroken, it can allow the user to install alternate custom firmware in place of the default firmware. Custom firmware may remove bloatware, add or remove features, and streamline the OS to optimize performance. You can find online discussion forums and communities, such as xda-developers.com and howardforums.com, that specialize in custom firmware for Apple and Android devices.

An organization should not allow users to operate mobile devices that have custom firmware unless that firmware is preapproved by the organization.

#### Carrier Unlocking

Most mobile devices purchased directly from a telco are carrier locked. This means you are unable to use the device on any other telco network until the carrier lock is removed or carrier unlocked. Once you fully own a device, the telco should freely carrier unlock the phone, but you will have to ask for it specifically because they don’t do so automatically. If you have an account in good standing and are traveling to another country with compatible telco service, you may be able to get a telco to carrier unlock your phone for your trip so that you can temporarily use another SIM card for local telco services. Note that SIM cards are used for **Global System for Mobile communication (GSM)**-related phones, whereas Code Division Multiple Access (CDMA)-based phones use an electronic serial number (ESN), which is embedded into the phone to identify the device and user as well as control the device’s service and use.

Having a device carrier unlocked is not the same as rooting. Carrier unlocked status only allows the switching of telco services (which is technically possible only if your device uses the same radio frequencies as the telco). A carrier unlocked device should not represent any additional risk to an organization; thus, there is likely no need for a prohibition of carrier unlocked devices on company networks.

#### Firmware Over-the-Air (OTA) Updates

Firmware over-the-air (OTA) updates are firmware updates that are downloaded from the telco or vendor over-the-air (via a data connection either provided by the carrier or via Wi-Fi). Generally, as a mobile device owner, you should install new firmware OTA updates onto a device once they become available. However, some updates may alter the device configuration or interfere with MDM/UEM restrictions. You should attempt to test new updates before allowing managed devices to receive them. You may have to establish a waiting period so that the MDM/UEM vendor can update their management product to properly oversee the deployment and configuration of the new firmware update. An organization’s standard patch management, configuration management, and change management policies should be applied to mobile devices.

#### Key Management

Key management is always a concern when cryptography is involved. Most of the failures of a cryptosystem are based on the key management rather than on the algorithms. Good key selection is based on the quality and availability of random numbers. Most mobile devices must rely locally on poor random-number-producing mechanisms or access more robust random number generators (RNGs) over a wireless link. Once keys are created, they need to be stored in such a way as to minimize exposure to loss or compromise. The best option for key storage is usually removable hardware (such as a MicroSD HSM) or the use of a Trusted Platform Module (TPM), but these are not universally available on mobile devices.

#### Credential Management

The storage of credentials in a central location is referred to as credential management. Given the wide range of internet sites and services, each with its own particular logon requirements, it can be a burden to use unique names and passwords. Credential management solutions offer a means to securely store a plethora of credential sets. Often these tools employ a master credential set (multifactor being preferred) to unlock the dataset when needed. Some credential-management options can even provide auto-login options for apps and websites.

A password vault is another term for a credential manager. These are often software solutions, sometimes hardware based, sometimes local only, and sometimes using cloud storage. They are used to generate and store credentials for sites, services, devices, and whatever other secrets you want to keep private. The vault itself is encrypted and must be unlocked to regain access to the stored items. Most password vaults use Password-Based Key Derivation Function 2 (PBKDF2) or Bcrypt (see Chapter 7) to convert the vault’s master password into a reasonably strong encryption key.

#### Text Messaging

Short Message Service (SMS), Multimedia Messaging Service (MMS), and Rich Communication Services (RCS) are all useful communication systems, but they also serve as an attack vector (such as smishing and SPIM, discussed in Chapter 2, “Personnel Security and Risk Management Concepts”). These testing and messaging services are primarily operated and supported by the telco providers. Texting can be used as an authentication factor known as SMS-based 2FA. SMS-based 2FA is better than single-factor password only authentication, but it is not recommended if any other second factor option is available. See Chapter 13 for more on SMS-based 2FA.

Many non-telco/non-carrier texting and messaging services are supported via apps on mobile devices. These include Google Hangouts, Android Messenger, Facebook Messenger, WeChat, Apple/iPhone iMessages, WhatsApp, Slack, Discord, and Microsoft Teams. It is important to keep any messaging service app updated and restrict its use to nonsensitive content.

### 2. Mobile Device Deployment Policies

A number of deployment models are available for allowing and/or providing mobile devices for employees to use while at work and to perform work tasks when away from the office. A mobile device deployment policy must address the wide range of security concerns regarding the use of a PED in relation to the organization’s IT infrastructure and business tasks.

Users need to understand the benefits, restrictions, and consequences of using mobile devices at work and for work. Reading and signing off on the BYOD, COPE, CYOD, COMS/COBO, etc., policy along with attending an overview or training program may be sufficient to accomplish reasonable awareness. These topics are covered in the next sections

#### 1.Bring Your Own Device (BYOD)

Bring your own device (BYOD) is a policy that allows employees to bring their own personal mobile devices to work and may allow them to use those devices to connect to business resources and/or the internet through the company network. Although BYOD may improve employee morale and job satisfaction, it increases security risk to the organization. If the BYOD policy is open-ended, any device may be allowed to connect to the company network. Not all mobile devices have sufficient security features, and thus such a policy allows noncompliant devices onto the production network.

This is likely the least secure option for the organization since company data and applications will be on the personal mobile device, it exposes the organization’s network to malicious code from the PEDs, and the devices will have the widest range of variation and security capabilities (or more likely the lack of security capabilities). Additionally, this option potentially exposes the worker’s PII on the device to the organization.

#### 2. Corporate-Owned, Personally Enabled (COPE)

The concept of corporate-owned, personally enabled (COPE) is for the organization to purchase devices and provide them to employees. Each user is then able to customize the device and use it for both work activities and personal activities. COPE allows the organization to select exactly which devices are to be allowed on the organizational network—specifically only those devices that can be configured into compliance with the security policy.

This option reduces the mobile devices to those preselected by the organization and that have the minimum security capabilities mandated by company security policy. However, this option still has the risk of exposing company data through user error, exposes the organization to malware via the device, and puts worker PII at risk of being accessed by the organization.

#### 3. Choose Your Own Device (CYOD)

The concept of choose your own device (CYOD) provides users with a list of approved devices from which to select the device to implement. A CYOD policy can be implemented so that employees purchase their own devices from the approved list (a BYOD variant) or the company can purchase the devices for the employees (a COPE variant).

This option attempts to keep the expense of devices the responsibility of workers rather than the organization, but it often results in much more complex and challenging situations. For example, how will it handle a situation wherein a worker has already spent considerable money on a device that is not on the preapproved list? Will they be given money to purchase an approved device? What about the person who paid for an approved device—will the company reimburse them because they already paid for someone else’s device? What about the person who decides they don’t want to use a mobile device for work activities—will they be paid the funds anyway, allowing them to treat it as a paycheck bonus?

Also, this option has the same security issues as COPE: the potential for malware transfer and the comingling of business and personal data on the same device.

#### 4. Corporate-Owned Mobile Strategy (COMS)

A corporate-owned mobile strategy (COMS) or corporate-owned, business-only (COBO) strategy is when the company purchases the mobile devices that can support security compliance with the security policy. These devices are to be used exclusively for company purposes, and users should not perform any personal tasks on the devices. This often requires workers to carry a second device for personal use.

This is the best option for both the organization as well as the individual worker. The option maintains clear separation between work activities and personal activities, since the device is for work use exclusively. This option protects company resources from personal activity risks, and it protects personal data from unauthorized or unethical organizational access. Yes, it is a hassle to carry a second device for personal activities, but that inconvenience is well worth the security benefits for both parties.

#### Mobile Device Deployment Policy Details

No matter which mobile device deployment policy you select and implement, your policy needs to address the many device security features listed earlier in this section. You can ensure this by defining required features and how they are to be configured for company security policy compliance. The mobile device deployment policy must also address several other concerns that are operational, legal, and logistic based as well. 

##### 1. Data Ownership

When a personal device is used for business tasks, commingling of personal data and business data is likely to occur. Some devices can support storage segmentation, but not all devices can provide data-type isolation. Establishing data ownership can be complicated. For example, if a device is lost or stolen, the company may wish to trigger a remote wipe, clearing the device of all valuable information. However, the employee will often be resistant to this, especially if there is any hope that the device will be found or returned. A wipe may remove all business and personal data, which may be a significant loss to the individualespecially if the device is recovered, because then the wipe would seem to have been an overreaction. Clear policies about data ownership should be established. Some MDM/UEM solutions can provide data isolation/segmentation and support business data sanitization without affecting personal data.

The mobile device deployment policy regarding data ownership should address backups for mobile devices. Business data and personal data should be protected by a backup solution—either a single solution for all data on the device or separate solutions for each type or class of data. Backups reduce the risk of data loss in the event of a remote-wipe event as well as device failure or damage.

##### 2. Support Ownership

When an employee’s mobile device experiences a failure, a fault, or damage, who is responsible for the device’s repair, replacement, or technical support? The mobile device deployment policy should define what support will be provided by the company and what support is left to the individual and, if relevant, their service provider.

##### 3. Patch and Update Management

The mobile device deployment policy should define the means and mechanisms of secure patch management and update management for a personally owned mobile device. Is the user responsible for installing updates? Should the user install all available updates? Should the organization test updates prior to on-device installation? Are updates to be handled over the air (via service provider) or over Wi-Fi? Are there versions of the mobile OS that cannot be used? What patch or update level is required? These issues should be addressed both for the primary OS of the device and for all apps installed on the device.

##### 4. Security Product Management

The mobile device deployment policy should dictate whether antivirus, antimalware, antispyware scanners, firewalls, HIDS, or other security tools are to be installed on mobile devices. The policy should indicate which products/apps are recommended for use, as well as the settings for those solutions.

##### 5. Forensics

The mobile device deployment policy should address forensics and investigations related to mobile devices. Users need to be aware that in the event of a security violation or a criminal activity, their devices might be involved. An investigation would mandate gathering evidence from those devices. Some processes of evidence gathering can be destructive, and some legal investigations require the confiscation of devices. An owner of a personal device may refuse access to the contents of their device, even when that content is, in theory, the property of the organization. A company-owned device could have a secondary account, a master password, or remote management tool preinstalled that would grant the organization the ability to access the device’s contents without the user’s consent.

##### 6. Privacy

The mobile device deployment policy should address privacy and monitoring. When a personal device is used for business tasks, the user often loses some or all of the privacy they enjoyed prior to using their mobile device at work. Workers may need to agree to be tracked and monitored on their mobile device, even when not on company property and outside work hours. A personal device in use under BYOD or CYOD should be considered by the individual to be quasi-company property.

A primary way for a worker to protect their privacy in regard to a mobile device is to not use a single device for both work and personal activities.

##### 7. Onboarding/Offboarding

The mobile device deployment policy should address personal mobile device onboarding and offboarding procedures. Mobile device onboarding includes installing security, management, and productivity apps along with implementing secure and productive configuration settings. These configuration enforcement processes can be implemented by an MDM/UEM solution. Mobile device offboarding includes a formal wipe of the business data along with the removal of any business-specific applications. In some cases, a full device wipe and factory reset may be prescribed. Either of these processes can result in the loss of or modification of personal data. You should make your users aware of those risks before subjecting their devices to an onboarding/offboarding process.

##### 8. Adherence to Corporate Policies

A mobile device deployment policy should clearly indicate that using a personal mobile device for business activities doesn’t exclude a worker from adhering to corporate policies. A worker should treat mobile device equipment as company property and thus stay in compliance with all restrictions, even when off premises and during off hours.

##### 9. User Acceptance

A mobile device deployment policy must be clear and specific about all the elements of using a personal device at work. For many users, the restrictions, security settings, and MDM/ UEM tracking implemented under company policy will be much more onerous than they expect. Thus, you should make the effort to fully explain the details of a mobile device deployment policy before allowing a personal device into your production environment. Only after an employee has expressed consent and acceptance, typically through a signature, should their device be onboarded.

Architecture/Infrastructure Considerations

When implementing mobile device deployment policies, organizations should evaluate their network and security design, architecture, and infrastructure. If every worker brings in a personal device, the number of endpoint devices on the network may double. This requires planning to handle IP assignments, communications isolation, data-priority management, and increased intrusion detection system (IDS)/intrusion prevention system (IPS) monitoring load, as well as increased bandwidth consumption, both internally and across any internet link. Most mobile devices are wireless enabled, so this will likely require a more robust wireless network and dealing with Wi-Fi congestion and interference. Your mobile device deployment policy must be considered in light of the additional infrastructure costs it will trigger.

##### 10. Legal Concerns

Company attorneys should evaluate the legal concerns of mobile devices. Using personal devices in the execution of business tasks probably means an increased burden of liability and risk of data leakage. Mobile devices may make employees happy, but it might not be a worthwhile or cost-effective endeavor for your organization if it increases risk and legal liability significantly.

##### 11. Acceptable Use Policy

The mobile device deployment policy should either reference the company acceptable use policy (AUP) or include a mobile device–specific version focusing on unique issues. The use of personal mobile devices at work is accompanied by an increased risk of information disclosure, distraction, and access to inappropriate content. Workers should remain mindful that the primary goal when at work is to accomplish productivity tasks.

##### 12. Onboard Camera/Video

The mobile device deployment policy needs to address mobile devices with onboard cameras. Some environments disallow cameras of any type. This would require that mobile devices be without a camera. If cameras are allowed, a description of when they may and may not be used should be clearly documented and explained to workers. A mobile device can act as a storage device, provide an alternate wireless connection pathway to an outside provider or service, and may be used to collect images and video that disclose confidential information or equipment.

If geofencing is available, it may be possible to use MDM/UEM to implement a locationspecific hardware-disable profile in order to turn off the camera (or other components) while the device is on company premises but return the feature to operational status once the device leaves the geofenced area.

##### 13. Recording Microphone

Most mobile devices with a speaker also have a microphone. The microphone can be used to record audio, noise, and voices nearby. Many mobile devices also support external microphones connected by a USB adapter, Bluetooth, or a 1/8″ stereo jack. If microphone recording is deemed a security risk, this feature should be disabled using an MDM/UEM or deny presence of mobile devices in sensitive areas or meetings.

##### 14. Wi-Fi Direct

Wi-Fi Direct is the new name for the wireless topology of ad hoc or peer-to-peer connections. It is a means for wireless devices to connect directly to each other without the need for an intermediary base station. Wi-Fi Direct supports WPA2 and WPA3, but not all devices are capable of supporting these optional encryption schemes. Wi-Fi Direct is used for a wide range of capabilities, including transmitting media for display on a monitor or television, sending print jobs to printers, controlling home automation products, interacting with security cameras, and managing photo frames.

In a business environment, Wi-Fi Direct should be used only where WPA2 or WPA3 can be used. Otherwise, the plaintext communication presents too much risk.

##### 15. Tethering and Hotspots

Tethering is the activity of sharing the cellular network data connection of a mobile device with other devices. This is also known as a hotspot. This effectively allows the mobile device to act as a portable wireless access point (WAP). The sharing of data connection can take place over Wi-Fi, Bluetooth, or USB cable. Some service providers include tethering in their service plans, whereas others charge an additional fee and some block tethering completely.

Tethering may represent a risk to the organization. It is a means for a user to grant internet access to devices that are otherwise network isolated, and it can be used as a means to bypass the company’s filtering, blocking, and monitoring of internet use. Thus, tethering should be blocked while a mobile device is within a company facility.

Hotspot devices are available that operate as portable WAPs and can be used to create a Wi-Fi network linked to a telco’s or carrier’s data network. Hotspot devices should be barred from use in most organizations because they provide a direct link to the internet without a company’s security restrictions being enforced.

##### 16.  Contactless Payment Methods

A number of mobile device–based payment systems, called contactless payment methods, do not require direct physical contact between the mobile device and the point-of-sale (PoS) device. Some are based on NFC, others on RFID, some on SMS, and still others on optical camera–based solutions, such as scanning Quick Response (QR) codes. Mobile payments are convenient for the shopper but might not always be a secure mechanism. Users should only employ mobile payment solutions that require a per-transaction confirmation or that require the device to be unlocked and an app launched to perform a transaction. Without these precautions, it may be possible to clone your device’s contactless payment signals and perform transaction abuse.

Your organization is unlikely to see any additional risk based on mobile payment solutions. However, use caution when implementing them on company-owned equipment or when they are linked to your company’s financial accounts.

##### 17. SIM Cloning

Subscriber identity module (SIM) cards are used to associate a device with a subscriber’s identity and service at a mobile or wireless telco. SIMs can be easily swapped between devices and cloned to abuse a victim’s telco services. If a SIM card is cloned, then the cloned SIMs may be able to connect other devices to the telecommunications services and link the use back to the account of the original owner. Physical control must be maintained on mobile devices and an account or service lock established on mobile services with the telco carrier.

## Essential Security Protection Mechanisms

All third-party software is written by someone other than the OS creator, that software might cause problems. Thus, treating all non-OS software as potentially damaging allows the OS to prevent many disastrous occurrences through the use of software management protection mechanisms.

The OS must employ protection mechanisms to keep the computing environment stable and to keep processes isolated from one another. Without these efforts, the security of data could never be reliable or even possible. This is effectively applying the principle of zero trust (see Chapter 8).

Computer system designers should adhere to a number of common protection mechanisms when designing secure systems. These principles are specific instances of the more general security rules that govern safe computing practices. Designing security into a system during the earliest stages of development will help ensure that the overall security architecture has the best chance for success and reliability.

### 1. Process Isolation

Process isolation requires that the OS provide separate memory spaces for each process’s instructions and data. It also requires that the OS enforce those boundaries, preventing one process from reading or writing data that belongs to another process. There are two major advantages to using this technique:

- It prevents unauthorized data access.
- It protects the integrity of processes.

Without such controls, a poorly designed process could go haywire and write data to memory spaces allocated to other processes, causing the entire system to become unstable rather than affecting only the execution of the errant process. In a more malicious vein, processes could attempt (and perhaps even succeed at) reading or writing to memory spaces outside their scope, intruding on or attacking other processes.

Many modern OSs address the need for process isolation by implementing virtual machines on a per-user or per-process basis. A virtual machine presents a user or process with a processing environment—including memory, address space, and other key system resources and services—that allows that user or process to behave as though they have sole, exclusive access to the entire computer. This allows each user or process to operate independently without requiring it to take cognizance of other users or processes that might be active simultaneously on the same machine. As part of the mediated access to the system that the OS provides, it maps virtual resources and access in user mode so that they use supervisory mode calls to access corresponding real resources. This not only makes things easier for programmers, but also protects individual users and processes from one another.

### 2. Hardware Segmentation

Hardware segmentation is similar to process isolation in purpose—it prevents access to information that belongs to a different process/security level. The main difference is that hardware segmentation enforces these requirements through the use of physical hardware controls rather than the logical process isolation controls imposed by an OS. Such implementations are rare, and they are generally restricted to national security implementations, where the extra cost and complexity is offset by the sensitivity of the information involved and the risks inherent in unauthorized access or disclosure.

### 3. System Security Policy

Just as security policy guides the day-to-day security operations, processes, and procedures in organizations, they have an important role to play when designing and implementing systems. This is equally true whether a system is entirely hardware based, entirely software based, or a combination of both. In this case, the role of a system security policy is to inform and guide the design, development, implementation, testing, and maintenance of a particular system. Thus, this kind of security policy tightly targets a single implementation effort. (Although it may be adapted from other, similar efforts, it should reflect the target as accurately and completely as possible.)

For system developers, a system security policy is best encountered in the form of a document that defines a set of rules, practices, and procedures that describe how the system should manage, protect, and distribute sensitive information. Security policies that prevent information flow from higher security levels to lower security levels are called multilevel security policies. As a system is developed, the security policy should be designed, built, implemented, and tested as it relates to all applicable system components or elements, including any or all of the following: physical hardware components, firmware, software, and how the organization interacts with and uses the system. The overall point is that security must be considered for the entire life of the project. When security is applied only at the end, it typically fails.

## Common Security Architecture Flaws and Issues

No security architecture is totally secure. Every computer system has weaknesses and vulnerabilities. The goal of security models and architectures is to address as many known weaknesses as possible. Due to this fact, corrective actions must be taken to resolve security issues. The following sections present some common security issues that affect computer systems in relation to vulnerabilities of security architectures. You should understand each of the issues and how they can degrade the overall security of your system. Some issues and flaws overlap one another and are used in creative ways to attack systems. Although the following discussion covers the most common flaws, the list is not exhaustive. Attackers are very clever.

Many attacks and exploits are covered elsewhere that are also relevant to this chapter’s content, such as Denial of Service (DoS) (Chapter 17), buffer overflow (Chapter 21), malware (Chapter 21), escalation of privilege (Chapter 21), and maintenance hooks/backdoors (Chapter 21). We covered numerous malicious issues earlier in this chapter, such as emanation eavesdropping, the cold boot attack against memory, phlashing, mobile-code-based client-side attacks, exploitation of local internet caches, and VM escaping. Several additional adversarial threats are included here, such covert channels, design/coding flaws, rootkits, and incremental attacks.

### 1. Covert Channels

A covert channel is a method that is used to pass information over a path that is not normally used for communication. Because the path is not normally used for communication, it may not be protected by the system’s normal security controls. Using a covert channel provides a means to violate, bypass, or circumvent a security policy undetected. Covert channels are one of the important examples of vulnerabilities of security architectures.

As you might imagine, a covert channel is the opposite of an overt channel. An overt channel is a known, expected, authorized, designed, monitored, and controlled method of communication. Therefore, a covert channel is an unknown, unexpected, unauthorized, not designed (at least not by the original system designers), unmonitored, and uncontrolled method of data transfer.

There are two basic types of covert channels:

Covert Timing Channel A covert timing channel conveys information by altering the performance of a system component or modifying a resource’s timing in a predictable manner. Using a covert timing channel is generally a method to secretly transfer data and is very difficult to detect.

Covert Storage Channel A covert storage channel conveys information by writing data to a common storage area where another process can read it. When assessing the security of software, be diligent for any process that writes to any area of memory that another process can read.

Examples of covert timing channels include the following:

- Blinking a light visible outside the building so that if a reading is taken every two seconds when the light is on count it as a 1 and when the light is off count it as a 0. With an external camera linked to a recording system, a slow transmission of binary data can occur.
- Using a microphone to listen to the noise occurring in an area or related to a computer system. Then modify a case fan to spin faster (for a 1) or slower (for a 0) to force a change in the noise generated every 10 seconds.
- Monitoring utilization levels of an internet connection when an insider is artificially padding or restricting traffic every 30 seconds. When traffic is above 80 percent utilization, record a 1; when below 40 percent utilization, record a 0.

Here are examples of covert storage channels; notice that they all involve placing data in a location that is either unseen by the OS or ignored by the OS:

- Writing data into unallocated or unpartitioned space, which may be accomplished using a hex editor
- Writing data directly into a bad sector of an HDD or a bad block on an SSD
- Writing data into the unused space at the end of a cluster, an area known as slack space
- Writing data directly into sectors or clusters without proper registration with the directory system, file container, or header

Both types of covert channels rely on the use of communication techniques to exchange information with otherwise unauthorized subjects. Because the covert channel is outside the normal data transfer environment, detecting it can be difficult. The best defense is to implement detailed and thorough auditing of all user and application activities and analyze log files for any covert channel activity, which may be anomalous behavior or may elicit known malicious activities via heuristics or pattern matching.

### 2. Attacks Based on Design or Coding Flaws

Certain attacks may result from poor design techniques, questionable implementation practices and procedures, or poor or inadequate testing. Some attacks may result from deliberate design decisions when special points of entry, built into code to circumvent access controls, login, or other security checks often added to code while under development, are not removed when that code is put into production. For what we hope are obvious reasons, such points of egress are properly called maintenance hooks or backdoors because they avoid security measures by design. Extensive testing and code review are required to uncover such covert means of access, which are easy to remove during final phases of development but can be incredibly difficult to detect during the testing and maintenance phases.

Poor coding practices and lack of security consideration are common sources or causes of vulnerabilities in system architectures that can be attributed to failures in design, implementation, prerelease code cleanup, or out-and-out coding mistakes. Although such flaws are avoidable, finding and fixing them requires rigorous security-conscious design from the beginning of a development project and extra time and effort spent in testing and analysis. This helps to explain the often lamentable state of software security, but it does not excuse it! Although functionality testing is commonplace for commercial code and applications, separate testing for security issues has been gaining attention and credibility only in the past few years, courtesy of widely publicized virus and worm attacks, SQL injection attacks, cross-site scripting attacks, and occasional defacements of or disruptions to widely used public sites online. Check out the OWASP Top 10 Web Application Security Risks report at owasp.org/www-project-top-ten. Most of these coding concerns are addressed in Chapter 20, “Software Development Security,” and Chapter 21.

Humans will never write completely secure (flawless) code. Any program that does not handle any exception gracefully is in danger of exiting in an unstable state. It is possible to cleverly crash a program after it has increased its security level to carry out a normal task. If an attacker is successful in crashing the program at the right time, they can attain the higher security level and cause damage to the confidentiality, integrity, and availability of your system. These are just a few of the myriad ways that code can be compromised.

Perfect security might be impossible, but you can definitely take many strong measures to better secure your code. Source code analysis tools implemented throughout the development cycle will minimize the number of flaws in the production release, and the flaws identified prior to production release will cost much less to mitigate. All programs that are executed directly or indirectly must be fully tested to comply with your security model. Make sure you have the latest version of any software installed, and be aware of any known security vulnerabilities. Because each security model, and each security policy, is different, you must ensure that the software you execute does not exceed the authority you allow. Writing secure code is difficult, but it’s certainly possible. Make sure all programs you use are designed to address security concerns. The concepts of code review and testing are covered in Chapter 15, “Security Assessment and Testing.”

### 3. Rootkits

A rootkit is malware that embeds itself deep within an OS. The term is a derivative of the concept of rooting and a utility kit of hacking tools. Rooting is gaining total or full control over a system.

A rootkit can manipulate information seen by the OS and displayed to users. A rootkit may replace the OS kernel, shim itself under the kernel, replace device drivers, or infiltrate application libraries so that whatever information it feeds to or hides from the OS, the OS thinks is normal and acceptable. This allows a rootkit to hide itself from detection, prevent its files from being viewed by file management tools, and prevent its active processes from being viewed by task management or process management tools. Thus, a rootkit is a type of invisibility shield used to hide itself and other malicious tools.

Several rootkit-detection tools are available, some of which are able to remove known rootkits. However, once you suspect a rootkit is on a system, the only truly secure response is to reconstitute or replace the entire computer. Reconstitution involves performing a thorough storage sanitization operation on all storage devices on that system, reinstalling the OS and all applications from trusted original sources, and then restoring files from trusted rootkit-free backups. Obviously, the best protection against rootkits is defense (i.e., don’t get infected in the first place) rather than response.

There are often no noticeable symptoms or indicators of compromise related to a rootkit infection. In the moments after initial rootkit installation there might be some system sluggishness and unresponsiveness as the rootkit installs itself, but otherwise it will actively mask any symptoms. In some rootkit infections, the initial infector, dropper, or installer of the malware will perform privilege escalation.

A means to potentially detect the presence of a rootkit is to notice when system files, such as device drivers and dynamic-link libraries (DLLs), have a file size and/or hash value change. File hash tracking can be performed manually by an administrator or automatically by HIDSs and system monitoring security tools.

### 4. Incremental Attacks

Some forms of attack occur in slow, gradual increments rather than through obvious or recognizable attempts to compromise system security or integrity. Two such forms of incremental attack are data diddling and the salami attack.

Data diddling occurs when an attacker gains access to a system and makes small, random, or incremental changes to data during storage, processing, input, output, or transaction rather than obviously altering file contents or damaging or deleting entire files. Such changes can be difficult to detect unless files and data are protected by encryption or unless some kind of integrity check (such as a checksum or message digest) is routinely performed and applied each time a file is read or written. Encrypted filesystems, file-level encryption techniques, or some form of file monitoring (which includes integrity checks performed by file integrity monitoring [FIM] tools) usually offer adequate guarantees that no data diddling is under way. Data diddling is often considered an attack performed more often by insiders rather than outsiders (external intruders). It should be obvious that since data diddling is an attack that alters data, it is considered an active attack.

The salami attack is more mythical by all published reports. The name of the attack refers to a systematic whittling at assets in accounts or other records with financial value, where very small amounts are deducted from balances regularly and routinely. Metaphorically, the attack may be explained as stealing a very thin slice from a salami each time it’s put on the slicing machine when it’s being accessed by a paying customer. In reality, though no documented examples of such an attack are available, most security experts concede that salami attacks are possible, especially when organizational insiders could be involved. Only by proper separation of duties and proper control over code can organizations completely prevent or eliminate such an attack. Setting financial transaction monitors to track very small transfers of funds or other items of value should help to detect such activity; regular employee notification of the practice should help to discourage attempts at such attacks.

## Summary

Shared responsibility is the security design principle indicating that organizations do not operate in isolation. It is because we participate in shared responsibility that we must research, implement, and manage engineering processes using secure design principles.

Designing secure computing systems begins with an investigation of hardware, software, and firmware and how those pieces fit into the security puzzle. It’s important to understand the principles of common computer and network organizations, architectures, and designs; the difference between address space and memory space; and machine types (real, virtual, multitasking, multiprogramming, multiprocessing, multiprocessor, and multiuser).

Additionally, a security professional must have a good grasp of operating modes (user, supervisor, privileged), storage types (primary, secondary, real, virtual, volatile, nonvolatile, random, sequential), and common protection mechanisms (such as process isolation and hardware segmentation).

System function, purpose, and design work toward establishing and supporting security or against it. Client-based systems should be concerned about running code from unknown sources as well as protecting local caches. Server-based systems need to manage data flow and optimize operations using large-scale parallel data systems, grid computing, or peer-to-peer solutions when appropriate. Additional concerns relate to industrial control systems, the Internet of Things, specialized devices, microservices, and infrastructure as code.

Virtualization technology is used to host one or more OSs within the memory of a single host computer. Virtual software, virtual networking, software-defined everything, containerization, serverless architecture, and other related advancements often dictate the need for virtualization security management.

Static environments, embedded systems, network-enabled devices, cyber-physical systems, HPC systems, edge computing devices, and fog computing devices, mobile devices, and other limited or single-purpose computing environments need security management.

No matter how sophisticated a security architecture is, flaws exist that attackers can exploit. Some flaws are introduced by programmers, whereas others are architectural design issues.

## Exam Essentials

