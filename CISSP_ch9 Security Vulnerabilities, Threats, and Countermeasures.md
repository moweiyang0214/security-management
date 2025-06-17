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

It is important to evaluate and understand the vulnerabilities in system architectures, especially in regard to technology and process integration. As multiple technologies and complex processes are intertwined in the act of crafting new and unique business functions, new issues and security problems often surface. As systems are integrated, attention should be paid to potential single points of failure as well as to emergent weaknesses in serviceoriented architecture (SOA). An SOA constructs new applications or functions out of existing but separate and distinct software services. The resulting application is often new; thus, its security issues are unknown, untested, and unprotected. All new deployments, especially new applications or functions, need to be thoroughly vetted before they are allowed to go live into a production network or the public internet.

Microservices are an emerging feature of web-based solutions and are derivative of SOA. A microservice is simply one element, feature, capability, business logic, or function of a web application that can be called upon or used by other web applications. It is the conversion or transformation of a capability of one web application into a microservice that can be called upon by numerous other web applications.

Microservices are often created as a means to provide purpose-specific business capabilities through services that are independently deployed. Often, microservices are small and focused on a singular operation, designed with few dependencies, and are based on fast short-term development cycles (similar to Agile). It is also common to deploy microservices based on immutable architecture or infrastructure as code.

Microservices are a popular development strategy because they allow large complex solutions to be broken into smaller self-contained functions. This design also enables multiple programming groups to work on crafting separate elements or microservices simultaneously. The relationship to an application programming interface (API) is that each microservice must have a clearly defined (and secured!) API to allow for I/O between multiple microservices as well as to and from other applications. Microservices are a type of programming or design architecture, whereas APIs are a standardized framework to facilitate communications and data exchange.

### Service Delivery Platform (SDP) 

A service delivery platform (SDP) is a collection of components that provide the architecture for service delivery. SDP is often used in relation to telecommunications, but it can be used in many contexts, including VoIP, Internet TV, SaaS, and online gaming. An SDP is similar to a content delivery network (CDN) (see Chapter 11), as both are designed for the support of and efficient delivery of a resource (such as services of a SDP and multimedia of a CDN). The goal of an SDP is to provide transparent communication services to other content or service providers. Both SDPs and CDNs can be implemented using microservices.

## Infra as Code

Infrastructure as code (IaC) is a change in how hardware management is perceived and handled. Instead of seeing hardware configuration as a manual, direct hands-on, one-on-one administration hassle, it is viewed as just another collection of elements to be managed in the same way that software and code are managed under DevSecOps (security, development, and operations). With IaC, the hardware infrastructure is managed in much the same way that software code is managed, including: version control, predeployment testing, customcrafted test code, reasonableness checks, regression testing, and consistency in a distributed environment.

This alteration in hardware management approach has allowed many organizations to streamline infrastructure changes so that they occur more easily, more rapidly, more securely and safely, and more reliably than before. IaC often uses definition files and rule sets that are machine readable to quickly deploy new settings and manage hardware consistently and efficiently. These files can be treated as software code in terms of development, testing, deployment, updates, and management. IaC is not
