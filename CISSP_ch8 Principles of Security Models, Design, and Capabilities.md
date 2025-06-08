# Principles of Security Models, Design, and Capabilities

- Domain 3.0: Security Architecture and Engineering

## Secure Design Principles（**安全设计原则**）

Security should be a consideration at every stage of a system’s development. Programmers, developers, engineers, and so on should strive to build security into every application or system they develop, with greater levels of security provided to critical applications and those that process sensitive information. It’s extremely important to consider the security implications of a development project in the early stages because it’s much easier to build security into a system during development than it is to add security to an existing system. Developers should research, implement, and manage engineering processes using secure design principles.

### 1. Objects and Subjects

访问控制模型（如 MAC、DAC、RBAC）均是围绕 Subject/Object 和 Access 权限设计。

| 概念                | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| **Subject（主体）** | 主动发起访问请求的实体，如：用户、进程、服务、程序、主机等。 |
| **Object（对象）**  | 被访问的资源，如：文件、数据库、内存、打印机、服务等。       |
| **Access（访问）**  | 是 Subject 与 Object 之间的关系，如读取、写入、删除、备份、打印等行为。 |

Controlling access to any resource in a secure system involves **two entities.** 

#### Subject

The ***subject*** is the active entity that makes a request to access a resource. A subject is commonly a user, but it can also be a process, program, computer, or organization. 

#### Object

The ***object*** is the passive entity that the subject wants to access. An object is commonly a resource, such as a file or printer, but it can also be a user, process, program, computer, or organization.

You want to keep a broad understanding of the terms of subject and object, rather than only considering users and files. 

**Access is the relationship between a subject and object,** which could include reading, writing, changing, deleting, printing, moving, backing up, and many other operations or activities.

Keep in mind that the actual entities referenced by the terms subject and object are specific to an individual access request. The entity serving as the object in one access event could serve as the subject in another. 

#### Transitive trust（传递信任）

- 传递信任 = A 信任 B，B 又信任 C ⇒ A 间接信任 C；
- 安全风险：如果 B 被攻击，A 可能在不知情情况下将信任传递给不安全的 C；
- 例子：SSO 系统链式跳转；联合身份认证；B2B API 信任链。

It  is the concept that if A trusts B and B trusts C, then A inherits trust of C through the transitive property. When A requests data from B and then B requests data from C, the data that A receives is essentially from C. Transitive trust is a serious security concern because it may enable bypassing of restrictions or limitations between A and C, especially if A and C both support interaction with B.

### 2. Closed and Open Systems

Systems are designed and built according to one of two differing philosophies. 

#### Closed system（闭合系统）

It  is designed to work well with a narrow range of other systems, generally all from the same manufacturer. The standards for closed systems are often proprietary and not normally disclosed. 

Closed systems are harder to integrate with unlike systems, but this “feature” could make them more secure. A closed system is often composed of proprietary hardware and software that does not incorporate industry standards or offer an open API. This lack of integration ease means that attacks that typically focus on generic system components either will not work or must be customized to be successful. In many cases, attacking a closed system is harder than launching an attack on an open system, since a unique exploit of a unique vulnerability would be required. In addition to the lack of known vulnerable components on a closed system, it is often necessary to possess more in-depth knowledge of the specific target system to launch a successful attack.

#### Open system（开放系统）

 It is designed using agreed-upon industry standards. Open systems are much easier to integrate with systems from different manufacturers that support the same standards or that use compatible *application programming interfaces (APIs)*.

Open systems are generally far easier to integrate with other open systems. It is easy, for example, to create a local area network (LAN) with a Microsoft Windows Server machine, a Linux machine, and a Macintosh machine. Although all three computers use different operating systems and could represent up to three different hardware architectures, each supports industry standards and open APIs, which makes it easy for network (or other) communications to occur. This ease of interoperability comes at a price, however. Because standard communications components are incorporated into each of these three open systems, there are far more predictable entry points and methods for launching attacks. In general, their openness makes them more vulnerable to attack, and their widespread availability makes it possible for attackers to find plenty of potential targets. Also, open systems are more popular and widely deployed than closed systems and thus attract more attention from attackers. An attacker who develops basic attacking skills will find more targets that are open systems than closed ones. Inarguably, there’s a greater body of shared experience and knowledge on how to attack open systems than there is for closed systems. The security of an open system is therefore more dependent on the use of secure and defensive coding practices and a thoughtful defense-in-depth deployment strategy.

#### 闭合系统 vs. 开放系统

| 特性     | **Closed System**          | **Open System**          |
| -------- | -------------------------- | ------------------------ |
| 接口标准 | 专有，非公开               | 行业标准，公开           |
| 可扩展性 | 差，不易集成               | 强，易于扩展             |
| 安全性   | 较高（不透明，攻击门槛高） | 较弱（透明性带来攻击面） |
| 示例     | 军用通信设备、某些工控系统 | 企业 IT 系统、互联网服务 |

**总结**：

- 封闭系统安全性更强，但缺乏兼容性；
- 开放系统易被攻击，但也更灵活、更普及，因此需更多**防御性编程**和**深度防御**策略。

#### APIs

| 维度     | 描述                                                   |
| -------- | ------------------------------------------------------ |
| **定义** | 一种允许不同组件（服务、应用、平台）之间通信的接口标准 |
| **组成** | 包括请求结构、参数类型、认证方式、数据格式、安全控制等 |
| **作用** | 实现系统之间互操作；现代网络架构的“连接器”             |

⚠️ **API 安全关注点**：

- 身份认证（如 OAuth、API 密钥）
- 输入验证（防止注入攻击）
- 访问控制（只允许授权资源访问）
- 日志审计和速率限制（防滥用）

An API is a defined set of interactions allowed between computing elements, such as applications, services, networking, firmware, and hardware. An API defines the types of requests that can be made, the exact means to make the requests, the data forms of the exchange, and other related requirements (such as authentication and/or session encryption).

APIs make interoperability of computing elements possible. Without APIs, computing components would be unable to directly interact and information sharing would not be easy. APIs are what make modern computing and the internet possible. The app on your smartphone talks to the phone’s operating system via an API; the phone’s operating system talks over the telco or Wi-Fi network via an API to reach the cloud service’s API in order to submit a request and receive a response.

#### Open Source vs. Closed Source（开源 vs. 闭源）

| 类型         | 描述                   | 优劣分析                                      |
| ------------ | ---------------------- | --------------------------------------------- |
| **开源软件** | 代码公开，支持社区审计 | 优：审查透明，协同修复 劣：攻击者也能看到漏洞 |
| **闭源软件** | 代码保密，由供应商维护 | 优：不易逆向 劣：“安全通过模糊”非长久之计     |

⚠️ **注意区分术语：**

- “开源/闭源” 是关于“源码是否公开”的属性；
- “开放/闭合系统” 是关于“系统架构是否标准化”的属性；
- 二者**不是同一个概念**，但 CISSP 会刻意混淆考查，需精准辨别。

An **open source solution** is one where the source code, and other internal logic, is exposed to the public. A closed source solution is one where the source code and other internal logic is hidden from the public. Open source solutions often depend on public inspection and review to improve the product over time. 

**Closed source solutions** are more dependent on the vendor/programmer to revise the product over time. Both open source and closed source solutions can be available for sale or at no charge, but the term commercial typically implies closed source. However, closed source code is sometimes revealed through either vendor compromise or through decompiling or disassembly. The former is always a breach of ethics and often the law, whereas the latter is a standard element in ethical reverse engineering or systems analysis.

It is also the case that a closed source program can be either an open system or a closed system, and an open source program can be either an open system or a closed system. Since these terms are so similar, it is essential to read questions carefully. 

**CISSP考点**

| 考点                                     | 你需要记住的是                           |
| ---------------------------------------- | ---------------------------------------- |
| **Access 三元组**                        | 主体 Subject、对象 Object、行为 Access   |
| **API 的关键安全问题**                   | 认证、授权、输入验证、加密传输、日志审计 |
| **开放系统安全策略**                     | 防御性编程 + 零信任 + 深度防御           |
| **开源 vs 闭源 不等于 开放 vs 闭合系统** | 读题时注意语义区别                       |
| **传递信任的风险**                       | 尽量限制跨系统间的信任链传播             |

### 3. Secure Defaults（安全默认设置）

**默认设置 ≠ 安全设置**

- **核心理念**：**产品出厂默认配置通常并不安全。**
- 主要原因：
  - 厂商更注重功能可用性、兼容性，而非默认安全性；
  - 安全配置通常意味着**禁用某些特性、加强访问控制、降低易用性**；
  - 默认配置是面向所有用户设计的，不能满足组织定制的安全策略。

Never assume that the default settings of any product are secure. They typically are not, because secure settings would likely get in the way of existing business tasks or system operations. It is always up to the system’s administrator and/or company security staff to alter a product’s settings to comply with the organization’s security policies. Unless your organization hired the developer, that developer did not craft the code or choose settings specifically for your organization’s use of their product.

A much better assumption is that the default settings of a product are the worst possible options for your organization. Therefore, you need to review each and every setting to determine what it does and what you need it to be configured to do in order to optimize security while supporting business operations.

**Secure by Default 代表理念**

- Microsoft SDL 中的 SD3+C（Secure by Design, by Default, by Deployment + Communication）；
- 一些现代安全产品已尝试默认启用最安全的配置，如默认启用 TLS 加密、默认禁用外部 API 接入。

Fortunately, there is some movement toward more secure defaults. Microsoft’s Security Development Lifecycle (SDL) has a motto named SD3+C, which includes the phrase “**Secure by Default**.” Some products, especially security products, may now be designed with their most secure settings enabled by default. However, such a locked-down product will have fewer enabled capabilities and will likely be less user friendly. Thus, while being more secure, secure defaults may be an obstacle for those who only want their systems to function.

##### 安全专家的职责

| 安全管理员职责                   | 开发者职责                         |
| -------------------------------- | ---------------------------------- |
| 审核所有设置项，评估风险         | 设计文档说明配置项的作用、安全影响 |
| 配置产品使其符合组织安全标准     | 提供“安全默认模板”或配置导入文件   |
| 采用“最小权限”和“功能最少化”原则 | 采纳 Secure by Default 原则        |

If you are a developer, then it is your responsibility to create detailed explanations of each of the configuration options of your product. You can’t assume that customers know everything about your product, especially what the configuration settings are and what each option does to alter its features, operations, communications, and so forth. 

You may be required to have default settings to make the product as easy to install as possible, but you may be able to provide one or more configurations in either written instructional form or in a file that can be imported or applied. This will go a long way to assist customers with gaining the most advantage from your product while minimizing the security risks.

### 4. Fail Securely（安全故障处理）

**定义：**系统发生错误或崩溃时，仍能维护最小安全边界，不让攻击者趁虚而入。

System failures can occur due to a wide range of causes. Once the failure event occurs, how the system or environment handles the failure is important. The most desired result is for an application to fail securely. The first type of failure management is programmatic error handling (aka ***exception handling***). This is the process where a programmer codes in mechanisms to anticipate and defend against errors in order to avoid the termination of execution. Error handling is the inclusion of code that will attempt to handle errors when they arise before they can cause harm or interrupt execution.

#### **编程层面的安全失败（Exception Handling）**

| 方法             | 描述                                                 |
| ---------------- | ---------------------------------------------------- |
| `try...catch`    | 捕获潜在错误，不让程序直接崩溃或暴露内部信息         |
| **输入验证**     | 检查长度、字符类型、黑名单过滤、转义元字符，防止注入 |
| **错误输出控制** | 不泄露堆栈信息、路径、变量名，防止信息泄露漏洞       |

One such mechanism, which is supported by many languages, is a ***try..catch statement***. This logical block statement is used to place code that could result in an error on the try branch, and then code that will be executed if there is an error on the catch branch. This is similar to if..then..else statements, but it is designed to deftly handle errors.

Other mechanisms are to avoid or prevent errors, especially as related to user input. ***Input sanitization, input filtering, or input validation*** are some of the terms used to refer to this concept. This often includes checking the input for length, filtering against a block list of unwanted input, and escaping metacharacters.

#### 系统级故障响应设计：Fail-Safe vs. Fail-Secure

##### ✅ **Fail-Safe（物理优先，保护人）**

- 应用于涉及人身安全的物理设备，如门禁、电梯、自动灭火装置；
- 失效状态下，系统**自动放行**，优先保障人员逃生、生命安全；
- 也称：**Fail-Open（在物理场景中）**

📌 例子：大楼火灾时，电磁锁门禁失效，自动打开。

------

##### ✅ **Fail-Secure（数字优先，保护数据）**

- 应用于数字系统，目标是**维护数据机密性和完整性**；
- 失效状态下，系统**关闭服务或连接**，阻止未授权访问；
- 又称：**Fail-Closed、Fail-Safe（在数字领域）**

📌 例子：防火墙或 VPN 系统在系统异常或崩溃时中断所有连接，防止通信泄露。

When a program fails securely, it was able to do so only because it was designed and programmed to. When secure failure is integrated into a system, the designer must make a few difficult choices about what the results of a failure event will be. The first question to be resolved is whether the system can operate in a fail-soft mode. To ***fail-soft*** is to allow a system to continue to operate after a component fails. This is an alternative to having a failure cause a complete system failure. An example is a typical multitasking operating system that can support numerous simultaneous applications. If one application fails, the others can typically continue to operate.

If fail-soft isn’t a viable option, then the designer needs to consider the type of product, its deployment scenarios, and the priorities related to failure response. In other words, when the product fails without a fail-soft design, it will fail completely. The designer/developer needs to decide what type of complete failure to perform and what to protect or sacrifice to achieve the planned failure result. There are numerous scenarios to consider. The initial distinction is whether the product is something that affects the physical world, such as a door locking mechanism, or is it primarily a digital asset focused product, such as a firewall.

If a product can affect the physical world, then the life and safety of humans needs to be considered and likely prioritized. This human protection prioritization is called ***fail-safe***. The idea is that when a failure occurs, the system, device, or product will revert to a state that protects the health and safety of people. For example, a fail-safe door will open easily in an emergency in order to allow people to escape a building. But this implies that the protection of assets may be sacrificed in favor of personnel safety.

##### Fail-Open vs. Fail-Closed（数字语境）

| 模式                     | 优先保障        | 风险         |
| ------------------------ | --------------- | ------------ |
| **Fail-Open**            | 高可用性        | 暴露数据风险 |
| **Fail-Closed / Secure** | 高机密性/完整性 | 可用性中断   |

📌 举例：

- 防火墙崩溃后继续放行所有数据（fail-open）：用户体验好但易被攻击；
- 崩溃后自动断开连接（fail-secure）：保护数据但可能影响业务。

In the context of the physical world, the terms **failopen** is a synonym to fail-safe and **fail-closed** is a synonym of fail-secure.

**Fail Terms Definitions Related to Physical and Digital Products**

| Physical       | ← State →   | Digital                             |
| -------------- | ----------- | ----------------------------------- |
| Protect People | Fail-Open   | Protect Availability                |
| Protect People | Fail-Safe   | Protect Confidentiality & Integrity |
| Protect Assets | Fail-Closed | Protect Confidentiality & Integrity |
| Protect Assets | Fail-Secure | Protect Confidentiality & Integrity |

If the product is primarily digital, then the focus of security is completely on digital assets. That means the designer must then decide upon the security aspect to prioritize—namely, availability or confidentiality and integrity. If the priority is for maintaining availability, then when the product fails, the connection or communication is allowed to continue. This is known as fail-open. If the priority is for maintaining confidentiality and integrity, then when the product fails, the connection or communication is cut off. This is known as fail-secure, fail-closed, and/or fail-safe (again, in the context of a digital environment). (Note: the IETF recommends avoiding the use of the term fail-safe when discussing digital only issues as it introduces the concept of human safety which is not a concern in a digital context and thus causes unnecessary confusion).

Take note that when the context switches from the physical world to the digital world, the definition of fail-safe changes. An example could be a firewall, which if designed to failopen would allow communications without filtering, whereas if implement a fail-secure, fail-closed, or fail-safe solution would cut off communications. The fail-open state protects availability through the sacrifice of confidentiality and integrity, whereas the fail-closed state sacrifices availability in order to protect confidentiality and integrity. Another example of a digital environment event following a fail-secure, fail-closed, and/or fail-safe procedure is when an operating system encounters a processing or memory isolation violation, it terminates all executions, then initiates a reboot. This mechanism is known as a stop error, or the Blue Screen of Death (BSoD) in Windows.

##### 多任务系统中的 Fail-Soft

- **Fail-Soft**：某组件故障不导致全系统崩溃；
- 如：操作系统中的任务隔离机制，浏览器中的多标签崩溃隔离。

#### CISSP考点总结

| 概念                          | 要点                                                     |
| ----------------------------- | -------------------------------------------------------- |
| **默认设置安全性**            | 不可信，需自定义配置，采用“最小权限”与“最少功能”原则     |
| **Secure by Default**         | 优先启用最安全配置，限制功能，需要详细说明与辅助导入配置 |
| **Fail-Safe vs. Fail-Secure** | 物理 vs. 数字场景，人员安全 vs. 数据安全                 |
| **Fail-Open vs. Fail-Closed** | 可用性 vs. 机密性/完整性，根据应用优先级抉择             |
| **异常处理机制**              | 输入验证、try-catch、错误信息控制，防止攻击者利用异常    |

### 5. Keep It Simple

#### **KISS（Keep It Simple, Stupid）原则** 

KISS原则是软件开发和安全设计中的经典理念，强调：**设计越简单越好，复杂度是安全的敌人。**

##### 安全设计中为何强调“简单化”？

| 复杂系统问题 | 安全风险                             |
| ------------ | ------------------------------------ |
| 功能过多     | 扩大攻击面（Attack Surface）         |
| 代码庞大     | 更难审计和测试，Bug 难以发现         |
| 集成组件复杂 | 第三方依赖越多，供应链风险越大       |
| 配置项繁多   | 安装部署出错率更高，容易被误配或误解 |

**一句话总结**：**越复杂 → 越难管理 → 越容易出错 → 越容易被攻击。**

Keep it simple is a shortened form of the classic statement of “keep it simple, stupid” or “keep it stupid simple.” This is sometimes called the KISS principle. In the realm of security, this concept is the encouragement to avoid overcomplicating the environment, organization, or product design. The more complex a system, the more difficult it is to secure. The more lines of code, the more challenging it is to thoroughly test it. The more parts there are, the more places there are for things to go wrong. The more features and capabilities, the larger the attack surface.

#### 相关开发理念（KISS 的衍生思想）

| 原则                                 | 含义                       | 对安全的益处                     |
| ------------------------------------ | -------------------------- | -------------------------------- |
| **DRY (Don’t Repeat Yourself)**      | 避免重复代码，提高一致性   | 统一修补逻辑漏洞，不易遗漏       |
| **Computing Minimalism**             | 最少资源依赖和功能实现     | 降低攻击面，减少配置错误         |
| **Rule of Least Power**              | 用最弱的语言/技术完成任务  | 减少程序执行意外或被滥用的可能   |
| **Worse Is Better**                  | 功能越少，质量可能越高     | 少即是多，避免功能堆砌带来的风险 |
| **YAGNI (You Aren’t Gonna Need It)** | 不要写“未来可能会用”的功能 | 避免未使用代码暴露新漏洞         |

There are many other concepts that have a similar or related emphasis, such as the following:

- **“Don’t Repeat Yourself” (DRY)** The idea of eliminating redundancy in software by not repeating the same code in multiple places, which would increase the difficulty if changes are needed.
- **Computing Minimalism**  Crafting code so that it uses the least necessary hardware and software resources possible; this is also the goal of the program evaluation and review technique (PERT), which is discussed in Chapter 20.
- **Rule of Least Power**  Use the least powerful programming language that is suitable for the needed solution.
- **“Worse Is Better” (aka New Jersey Style)**  The quality of software does not necessarily increase with an increase in capabilities and functions; there is often a worse software state (i.e., fewer functions), which is the better (i.e., preferred, maybe more secure) option.
- **“You Aren’t Gonna Need It” (YAGNI)**  Programmers should not add capabilities and functions until they are actually necessary, so rather than create it when you think of it, instead create it only when you actually need it.

It is easy to get caught up in adding complexity to a system, whether that system is a software program or an organizational IT security structure. The KISS principle encourages us all to avoid the overly complex in favor of the streamlined, optimized, and reduced solution. Simpler solutions are easier to secure, easier to troubleshoot, and easier to verify.

#### CISSP考点总结

- CISSP 倡导 **Security by Design** 和 **Defense in Depth**；

- 但任何安全机制设计都要避免“过度设计”或“工具泛滥”；

- KISS 原则是落实“**最小化攻击面（Minimize Attack Surface）**”与“**简化控制路径**”的重要保障。

##### 实际应用举例：

| 场景             | KISS 原则的应用                                 |
| ---------------- | ----------------------------------------------- |
| **安全架构设计** | 不引入不必要的 VPN/跳板层，避免链路冗长难以排查 |
| **代码安全**     | 简单逻辑处理比复杂多态结构更安全、更易审计      |
| **身份验证系统** | 使用集中认证（如 SSO）代替重复的账号体系        |
| **策略配置**     | 清晰少量的 ACL、IAM 规则优于层层嵌套的规则组    |

- KISS ≠ 简陋，而是 **精炼+实用+可控**；

- CISSP 解题中若遇到“过度集成功能、多余逻辑”，优先排除；

- 安全系统应当 **越简单，越容易做到“验证-测试-控制”**。

### 6. Zero Trust

### 7. Privacy by Design

### 8. Trust but Verify

## Techniques for Ensuring CIA

### 1. Confinement

### 2. Bounds

### 3. Isolation

### 4. Access Controls

### 5. Trust and Assurance

## Understand the FUndamental Concepts of Security Models

### 1. Trusted Computing Base

### 2. State Machine Model

### 3. Information Flow Model

### 4. Noninterference Model

### 5. Take-Grant Model

### 6. Access Control Matrix

### 7. Bell-LaPadula Model

### 8. Biba Model

### 9. Clark-Wilson Model

### 10. Brewer and Nash Model

### 11. Goguen-Meseguer Model

### 12. Sutherland Model

### 13. Graham-Denning Model

### 14. Harrison-Ruzzo-Ullman Model

## Select Controls Based on Systems Security Requirements 

### 1. Common Criteria

### 2. Authorization to Operate

## Understand Security Capabilities of Information Systems

### 1. Memory Protection

### 2. Virtualization

### 3. Trusted Platform Module

### 4. Interfaces

### 5. Fault Tolerance 

### 6. Encryption/Decryption

## Summary



## Exam Essentials

