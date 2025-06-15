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

loosely-coupled 分布式计算网络，用**“志愿节点”**聚合空闲资源完成大任务。

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

## Industrial Control Systems

## Distributed Systems

## High-Performance Computing (HPC) Systems

## Internet of Things

## Edge and Fog Computing

## Embedded Devices and Cyber-Physical Systems

