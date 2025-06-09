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

### 6. Zero Trust（零信任架构）

📌 核心理念：**永不信任，始终验证**

- **假设已经被入侵**（Assume Breach）
- 每一次访问都必须被 **认证（Authentication）、授权（Authorization）、加密（Encryption）**
- 没有“内部信任”或“默认信任” —— 所有用户、设备、服务 **一律不信任**

实现要素

| 核心机制                        | 描述                                 |
| ------------------------------- | ------------------------------------ |
| **身份和访问管理（IAM）**       | 每次访问都需要验证身份               |
| **多因素认证（MFA）**           | 防止账户被轻易接管                   |
| **最小权限原则**                | 只授予执行任务所需最少权限           |
| **微分段（Microsegmentation）** | 网络切分成多个小段，控制横向移动     |
| **持续监测与行为分析**          | 实时监控用户活动，检测异常行为       |
| **动态策略评估**                | 考虑上下文信息（如设备、位置、时间） |

📖 标准文档

- **NIST SP 800-207：Zero Trust Architecture**
- 定义 ZT 的核心组件、实施路径、与现有系统的集成方式。

Zero trust is an alternate approach to security where nothing is automatically trusted. Instead, each request for activity or access is assumed to be from an unknown and untrusted location until otherwise verified. The concept is “never trust, always verify.” Since anyone and anything could be malicious, every transaction should be verified before it is allowed to occur. The zero trust model is based around “assume breach,” meaning that you should always assume a security breach has occurred and that whoever or whatever is making a request could be malicious. The goal is to have every access request be authenticated, authorized, and encrypted prior to the access being granted to a resource or asset. The implementation of a zero trust architecture does involve a significant shift from historical security management concepts. This shift typically requires internal microsegmentation and strong adherence to the principle of least privilege. This approach prevents lateral movement so that if there is a breach or even a malicious insider, their ability to move about the environment is severely restricted.

Zero trust is implemented using a wide range of security solutions, including internal segmentation firewalls (ISFWs), multifactor authentication (MFA), identity and access management (IAM), and next-generation endpoint security. A zero trust approach to security management can only be successful if a means to continuously validate and monitor user activities is implemented. If a one-time validation mechanism is used, then the opportunity to abuse the system remains since threats, users, and connection characteristics are always subject to change. Thus, zero trust networking can only work if real-time vetting and visibility into user activities is maintained.

#### Air Gap（物理隔离）

- **完全不连接网络**，既无有线也无无线连接；
- 适用于超高保密性场景（如核设施、军工控制系统）；
- 属于比 Zero Trust 更极端的隔离模型。

In some situations, complete isolation may be needed instead of controlled and filtered interaction. This type of isolation is achieved using an air gap. An air gap is a network security measure employed to ensure that a secure system is physically isolated from other systems. Air gap implies that neither cabled nor wireless network links are available.

In order to implement a zero trust system, an organization must be capable of and willing to abandon some long-held assumptions about security. First and foremost, it must be understood that there is no such thing as a trusted source. No entity, asset, or subject—internal or external—is to be trusted by default. Instead, always assume attackers are already on the inside, on every system. From this new “no assumed trust” position, it is obvious that traditional default access controls are insufficient. Each and every subject, each and every time, needs to be authenticated, authorized, and encrypted. From there, a continuous real-time monitoring system needs to be established to look for violations and suspicious events. But even with zero trust integrated into the IT architecture, it is only an element of a holistic security strategy that is integrated into the entire organization’s management processes.

Zero trust has been formalized in NIST SP 800-207, “Zero Trust Architecture.”

### 7. Privacy by Design（内建隐私）

📌 核心理念：**将隐私保护融入系统的设计之初，而非事后弥补**

类似于“Security by Design”，强调开发过程从一开始就**主动防护隐私**。

Privacy by Design (PbD) is a guideline to integrate privacy protections into products during the early design phase rather than attempting to tack it on at the end of development. It is effectively the same overall concept as “security by design” or “integrated security,” where security is to be an element of design and architecture of a product starting at initiation and being maintained throughout the software development lifecycle (SDLC).

#### 七大原则

| 原则                | 含义                                   |
| ------------------- | -------------------------------------- |
| **1. 预防为主**     | 主动防御隐私泄露，不是等出事再处理     |
| **2. 默认隐私**     | 默认设置下用户隐私受保护，无需手动开启 |
| **3. 内嵌设计**     | 隐私保护是架构的一部分，不是附加功能   |
| **4. 双赢策略**     | 功能性和隐私性可以共存，不是零和博弈   |
| **5. 生命周期安全** | 数据从采集到销毁全过程保护隐私         |
| **6. 透明可见**     | 系统必须对用户公开处理机制、用途       |
| **7. 尊重用户**     | 用户对其个人信息应有控制权与选择权     |

As described in Ann Cavoukian’s paper “Privacy by Design – The 7 Foundational Principles: Implementation and Mapping of Fair Information Practices”, the PbD framework is based on seven foundational principles:

- Proactive not reactive; preventive not remedial
- Privacy as the default
- Privacy embedded into design
- Full functionality – positive-sum, not zero-sum
- End-to-end security – full lifecycle protection
- Visibility and transparency
- Respect for user privacy

The goal of PbD is to have developers integrate privacy protections into their solutions in order to avoid privacy violations in the first place. The overall concept focuses on preventions rather than remedies for violations.

#### GPS - Global Privacy Standard

- 推动全球统一隐私立法和组织内部隐私设计；
- 与 **GDPR** 的“**Privacy by Design & Default**”理念一致。

PbD is also the driving factor behind an initiative to have privacy protections integrated throughout an organization, not just by developers. That business operations and systems design can also integrate privacy protections into their core functions. This in turn has led to the **Global Privacy Standard (GPS),** which was crafted to create a single set of universal and harmonized privacy principles. GPS is to be adopted by countries to use as a guide in developing privacy legislation, used by organizations to integrate privacy protection into their operations, and used by developers to integrate privacy into the products they produce. There is some integration of a few of the principles of PbD in the EU’s GDPR (see gdpr-info.eu/ issues/privacy-by-design and Chapter 4, “Laws, Regulations, and Compliance”).

### 8. Trust but Verify（信任但需验证）

📌 特点：**默认信任 + 补充验证**

- 曾是许多组织的默认安全策略；
- 一旦进入“内部网络”就认为安全，造成了 **横向移动（Lateral Movement）** 的巨大隐患；
- 无法有效抵御：
  - **内部威胁（Insider Threats）**
  - **被攻陷终端（Compromised Hosts）**
  - **凭据滥用（Credential Abuse）**

A more traditional security approach of trusting subjects and devices within the company’s security perimeter (i.e., internal entities) automatically can be called “trust but verify.” This type of security approach leaves an organization vulnerable to insider attacks and grants intruders the ability to easily perform lateral movement among internal systems. Often the trust but verify approach depended on an initial authentication process to gain access to the internal “secured” environment, and then relied on generic access control methods. Due to the rapid growth and changes in the modern threatscape, the trust but verify model of security is no longer sufficient. Most security experts now recommend designing organizational security around the zero trust model.

#### 适用性降低

随着云计算、远程办公、移动设备接入增多，**信任但验证模型**已不适应现代威胁模型。

因此 **CISSP 考试及实际安全架构推荐转向 Zero Trust**：

| 模型                 | 核心特点                     | 安全水平   |
| -------------------- | ---------------------------- | ---------- |
| **Trust but Verify** | 仅初始验证，后续操作不再检查 | ⚠️ 中等偏低 |
| **Zero Trust**       | 所有操作全程验证与监控       | ✅ 高       |

## Techniques for Ensuring CIA（保障机密性、完整性、可用性的方法）

在 CISSP 的核心目标中，**Confidentiality（保密性）**、**Integrity（完整性）** 和 **Availability（可用性）** 是一切安全控制设计的出发点。为了有效保护数据及其处理系统，必须借助软件工程和操作系统中具备的“安全隔离机制”实现对 CIA 的技术保障。

To ensure the confidentiality, integrity, and availability (CIA) of data, you must ensure that all components that have access to data are secure and well behaved. Software designers use different techniques to ensure that programs do only what is required and nothing more. Although the concepts we discuss in the following sections all relate to software programs, they are also commonly used in all areas of security. For example, physical confinement guarantees that all physical access to hardware is controlled.

### 1. Confinement（限制）

又称 **沙箱（sandboxing）**，是最直接体现**最小权限原则**的机制。

✅ 核心作用：

- 限制进程或程序只能访问其被允许的内存、文件、资源；
- 防止未经授权的数据泄露或越权访问。

📌 应用方式：

| 类型         | 示例                                               |
| ------------ | -------------------------------------------------- |
| 操作系统级别 | Linux cgroups、Windows AppContainer、macOS Sandbox |
| 独立软件工具 | Sandboxie, Docker                                  |
| 虚拟化手段   | VMware, VirtualBox                                 |

CISSP考点：

- **Process confinement** = “Least privilege for processes”
- 沙箱 ≠ 虚拟机，但目的类似：**资源和行为隔离**

Software designers use process confinement to restrict the actions of a program. Simply put, process confinement allows a process to read from and write to only certain memory locations and resources. This is also known as sandboxing. It is the application of the principle of least privilege to processes. The goal of confinement is to prevent data leakage to unauthorized programs, users, or systems.

The operating system, or some other security component, disallows illegal read/write requests. If a process attempts to initiate an action beyond its granted authority, that action will be denied. In addition, further actions, such as logging the violation attempt, may be taken. Generally, the offending process is terminated. Confinement can be implemented in the operating system itself (such as through process isolation and memory protection), through the use of a confinement application or service (for example, Sandboxie at sandboxie.com), or through a virtualization or hypervisor solution (such as VMware or Oracle’s VirtualBox).

### 2. Bounds（边界）

定义进程可访问资源范围的**边界条件**

核心作用：

- 将不同权限级别的进程分配到受限资源空间；
- 防止权限提升（如用户模式访问内核空间）；

📌 边界类型：

| 类型         | 说明                                           |
| ------------ | ---------------------------------------------- |
| **逻辑边界** | 操作系统控制访问权限（如内存页保护）           |
| **物理边界** | 更强隔离，如专用硬件区段、专用内存芯片（昂贵） |

联动机制：

- **Bounds 是实现 confinement 的“规则”层面**；
- **Bounds 是实现 isolation 的“基础条件”**

Each process that runs on a system is assigned an authority level. The authority level tells the operating system what the process can do. In simple systems, there may be only two authority levels: user and kernel. The authority level tells the operating system how to set the bounds for a process. The bounds of a process consist of limits set on the memory addresses and resources it can access. The bounds state the area within which a process is confined or contained. In most systems, these bounds segment logical areas of memory for each process to use. It is the responsibility of the operating system to enforce these logical bounds and to disallow access to other processes. More secure systems may require physically bounded processes. Physical bounds require each bounded process to run in an area of memory that is physically separated from other bounded processes, not just logically bounded in the same memory space. Physically bounded memory can be very expensive, but it’s also more secure than logical bounds. Bounds can be a means to enforce confinement.

### 3. Isolation（隔离）

从技术上**阻止一个进程影响另一个进程的行为或资源访问**

核心作用：

- 限制进程相互访问；
- 当进程崩溃时，不影响其他进程或操作系统；
- 阻止内存空间、系统调用、文件描述符的非法共享。

📌 典型实现方式：

- 现代操作系统进程隔离机制（内核 vs 用户态）
- 虚拟化/容器技术（如 Docker、KVM、Hyper-V）
- 浏览器 tab 进程沙箱化

🔁 三者关系图解：

````
[Confinement]
    |
    V
[ Bounds ] ---------> 定义权限边界
    |
    V
[ Isolation ] -------> 保证独立运行、故障不影响其他模块
````

When a process is confined through enforcing access bounds, that process runs in isolation. Process isolation ensures that any behavior will affect only the memory and resources associated with the isolated process. Isolation is used to protect the operating environment, the kernel of the operating system, and other independent applications. Isolation is an essential component of a stable operating system. Isolation is what prevents an application from accessing the memory or resources of another application, whether for good or ill. Isolation allows for a fail-soft environment so that separate processes can operate normally or fail/crash without interfering or affecting other processes. Isolation is achieved through the enforcement of containment using bounds. 

These three concepts (confinement, bounds, and isolation) make designing secure programs and operating systems more difficult, but they also make it possible to implement more secure systems. Confinement is making sure that an active process can only access specific resources (such as memory). Bounds is the limitation of authorization assigned to a process to limit the resources the process can interact with and the types of interactions allowed. Isolation is the means by which confinement is implemented through the use of bounds. The goals of the concepts is the ensure that the predetermined scope of resource access is not violated and any failure or compromise of a process has minimal to no affect on any other process.

### 4. Access Controls（访问控制）

对 Subject 与 Object 之间的**访问行为进行控制**

✅ 作用目标：

- 仅允许被授权主体访问目标资源；
- 区分不同的访问操作（读、写、执行、删除等）；

📌 主要模型

| 模型                | 特点                       |
| ------------------- | -------------------------- |
| DAC（自主访问控制） | 所有者控制，灵活但风险高   |
| MAC（强制访问控制） | 安全级别分层，军事常用     |
| RBAC（基于角色）    | 企业应用广泛               |
| ABAC（基于属性）    | 高灵活性、现代云环境支持好 |

To ensure the security of a system, you need to allow subjects to access only authorized objects. Access controls limit the access of a subject to an object. Access rules state which objects are valid for each subject. Further, an object might be valid for one type of access and be invalid for another type of access. There are a wide range of options for access controls, such as discretionary, role-based, and mandatory. Please see Chapter 14 for an in-depth discussion of access controls.

### 5. Trust and Assurance（信任与保障）

| 项目          | 定义                               | 关键含义                                 |
| ------------- | ---------------------------------- | ---------------------------------------- |
| **Trust**     | 安全机制存在（Security Mechanism） | 系统具备一定的保护能力                   |
| **Assurance** | 安全机制的可靠性（Confidence）     | 这些保护机制是否**有效、持续、安全运行** |

保障机制：

- 安全功能测试（如 Common Criteria、EAL）
- 变更管理、补丁管理、配置基线（持续维护 assurance）
- 可信启动（Trusted Boot）或 TPM 支持

🧠 记忆提示：

- **Trust 是“你有什么”**
- **Assurance 是“你怎么知道它有效”**

A trusted system is one in which all protection mechanisms work together to process sensitive data for many types of users while maintaining a stable and secure computing environment. In other words, trust is the presence of a security mechanism, function, or capability. Assurance is the degree of confidence in satisfaction of security needs. In other words, assurance is how reliable the security mechanisms are at providing security. Assurance must be continually maintained, updated, and reverified. This is true if the secured system experiences a known change (good or bad—i.e., a vendor patch or a malicious exploit) or if a significant amount of time has passed. In either case, change has occurred at some level. Change is often the antithesis of security; it often diminishes security. This is why change management, patch management, and configuration management are so important to security management.

Assurance varies from one system to another and often must be established on individual systems. However, there are grades or levels of assurance that can be placed across numerous systems of the same type, systems that support the same services, or systems that are deployed in the same geographic location. Thus, trust can be built into a system by implementing specific security features, whereas assurance is an assessment of the reliability and usability of those security features in a real-world situation.

#### 总结表格

| 技术名                | 作用说明                             | 关键术语/机制                 |
| --------------------- | ------------------------------------ | ----------------------------- |
| **Confinement**       | 限制进程访问范围                     | 沙箱、虚拟化、最小权限        |
| **Bounds**            | 定义进程行为和访问边界               | 权限级别、逻辑/物理内存隔离   |
| **Isolation**         | 确保进程互不干扰、独立运行           | 进程隔离、容器、虚拟化        |
| **Access Control**    | 控制访问对象的权限和方式             | DAC、MAC、RBAC、ABAC          |
| **Trust & Assurance** | 系统安全机制存在与可靠性的评估与验证 | TPM、Common Criteria、EAL等级 |

## Understand the Fundamental Concepts of Security Models

**安全模型（Security Model）** 是信息安全领域中用于**形式化安全策略**的一种方法。其作用是：

- 将抽象的安全策略（如“谁可以访问什么”）**映射成具体的、可操作的机制**；
- 为系统设计者提供可以用来衡量实现是否符合安全目标的**技术蓝图**；
- 通常包括 **一组规则 + 一种系统结构或机制**，对“访问控制”、“信息流”、“完整性”、“权限授权”等问题做出定义。

**安全模型 ≠ 安全策略**

- 策略定义“要做什么”
- 模型定义“怎么做、谁来做、做的机制是什么”

In information security, models provide a way to formalize security policies. Such models can be abstract or intuitive, but all are intended to provide an explicit set of rules that a computer can follow to implement the fundamental security concepts, processes, and procedures of a security policy. A security model provides a way for designers to map abstract statements into a security policy that prescribes the algorithms and data structures necessary to build hardware and software. Thus, a security model gives software designers something against which to measure their design and implementation.

#### Tokens, Capabilities, and Labels

Several different methods are used to describe the necessary security attributes for an object. A security token is a separate object that is associated with a resource and describes its security attributes. This token can communicate security information about an object prior to requesting access to the actual object. In other implementations, various lists are used to store security information about multiple objects. A capabilities list maintains a row of security attributes for each controlled object. Although not as flexible as the token approach, a capabilities list generally offers quicker lookups when a subject requests access to an object. A third common type of attribute storage is called a security label, which is generally a permanent part of the object to which it’s attached. Once a security label is set, it usually cannot be altered. This permanence provides another safeguard against tampering that neither tokens nor capabilities lists provide.

##### 1. Security Token

- **定义**：一个**独立的安全属性对象**，与受控资源关联；
- **用法**：在访问资源前，**先传递 token** 给访问控制机制，以便验证；
- **特点**：
  - 可拆分、易于传递；
  - 适合**面向对象或分布式系统**；
  - 安全性需额外保障（token 本身可能被伪造或篡改）；

📌 **例子**：OAuth 2.0 访问令牌、Kerberos Ticket

##### 2. Capability List

- **定义**：系统为每个**对象**维护一张能力表，记录它可被哪些用户（或进程）访问、具备什么权限；
- **本质**：一种列出“谁可以做什么”的访问控制列表；
- **特点**：
  - 查找快；
  - **不太灵活**（需要逐个对象配置）；
  - **不易管理大规模权限组合**；

📌 类似于 Linux 中的 file permission bits（如 rwxr-xr--）

##### 3. Security Label

- **定义**：标签是一个**嵌入对象本身**的属性，标记了其安全属性（如机密级别）；
- **特点**：
  - 不可篡改（或只能由特权管理员修改）；
  - 常用于**强制访问控制模型**（MAC）；
  - 实现了对**信息流的控制**（如高密级对象不能向低密级写）；

📌 **例子**：

- **Bell-LaPadula 模型** 使用安全标签实现机密性等级（Top Secret, Secret, Confidential）
- **SELinux** 用标签控制系统进程对资源的访问

| 机制类型          | 定位         | 存储位置       | 灵活性     | 安全性       | 应用模型示例       |
| ----------------- | ------------ | -------------- | ---------- | ------------ | ------------------ |
| Security Token    | 外部对象     | 分离于资源本体 | 高         | 中（需加密） | Kerberos, OAuth    |
| Capabilities List | 系统级权限表 | 系统表         | 中         | 中           | ACLs, DAC 系统     |
| Security Label    | 嵌入对象     | 对象自身       | 低（固定） | 高（防篡改） | Bell-LaPadula, MAC |

“**Token 携带通行证，Label 贴在对象上，Capability 记在我手上。**”

- **Token** → 像票证一样随身带、可转移
- **Label** → 像标签贴在物体上，不易更改
- **Capability** → 像清单在你手中，清楚写着“我能干啥”

CISSP 考试中的要点理解

- Security Models 是将策略（如 MAC、DAC、RBAC）**技术落地的框架**
- **标签机制（Labels）** 是 MAC 的典型实现形式；
- **Token 和 Capability List** 适合 DAC/RBAC 情境；
- 考题常通过场景描述，要求识别使用的是哪种机制；
- 掌握三种机制的特点、适用场景、优劣对比是答题关键；

CISSP考点

若题目提到“**一个主体带有对象权限的列表**” → Capability List

若题目强调“**每个对象标记了一个不可更改的安全级别**” → Security Label（MAC）

若题目说“**每个对象携带一个可分发的访问凭证或临时授权**” → Token（常见于临时会话或 SSO）

### 1. Trusted Computing Base (TCB)

**Trusted Computing Base (TCB)** 是指一个计算系统中被信任用来**强制执行安全策略**的全部软硬件组合。它是：

- 操作系统 + 安全机制中最**核心、最可信、最小化**的子系统；
- 其**完整性与正确性**是整个系统安全的基础；
- 安全目标：**机密性、完整性、访问控制策略的执行**

📌 理想设计中，**TCB 越小越好**，这样更易于验证其安全性与功能正确性（安全最小化原则）。

The trusted computing base (TCB) design principle is the combination of hardware, software, and controls that work together to form a trusted base to enforce your security policy. The TCB is a subset of a complete information system. It should be as small as possible so that a detailed analysis can reasonably ensure that the system meets design specifications and requirements. The TCB is the only portion of that system that can be trusted to adhere to and enforce the security policy. It is the responsibility of TCB components to ensure that a system behaves properly in all cases and that it adheres to the security policy under all circumstances.

#### Security Perimeter（安全半径）

**Security Perimeter** 是一个**逻辑边界**，用于隔离 TCB 与系统的其他部分。其作用是：

- 防止非授权代码直接访问 TCB；
- 强制所有访问 TCB 的操作都通过受控通道进行。

Trusted Path（受信通道）

- 是 TCB 与用户或外部系统交互的**安全通道**；
- 防止中间人攻击、恶意干扰；
- 常见实现包括：**Ctrl+Alt+Del 登录界面**（Windows）确保用户输入不会被恶意程序捕捉。

Trusted Shell（受信命令行）

- 允许用户安全地使用命令行操作；
- 防止用户“逃逸”出 shell 影响 TCB，也阻止其他恶意程序劫持 shell；
- 多用于 **高安全级别的 CLI 环境**（如特权 shell、Secure Boot 控制台等）

The security perimeter of your system is an imaginary boundary that separates the TCB from the rest of the system. This boundary ensures that no insecure communications or interactions occur between the TCB and the remaining elements of the computer system. For the TCB to communicate with the rest of the system, it must create secure channels, also called trusted paths. A trusted path is a channel established with strict standards to allow necessary communication to occur without exposing the TCB to security exploitations.

A security perimeter may also allow for the use of a trusted shell. 

A trusted shell allows a subject to perform command-line operations without risk to the TCB or the subject. 

A trusted shell prevents the subject from being able to break out of isolation to affect the TCB and in turn prevents other processes from breaking into the shell to affect the subject.

#### Reference Monitors and Security Kernels

##### Reference Monitor（参考监控器）

这是 TCB 中的一个 **核心概念**，其主要职责为：

| 功能         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| 访问控制判定 | 验证每一个对资源（object）的访问请求是否符合访问策略（policy） |
| 独立性       | 独立于应用和用户，无法被篡改或绕过                           |
| 完整性       | 每次访问都必须经过它（不可跳过）                             |
| 审计能力     | 所有访问尝试都可被记录（包括成功与失败）                     |

参考监控器是**访问控制模型的实践者**，如 MAC、DAC、RBAC 都可通过其实施。

##### Security Kernel（安全内核）

- 是参考监控器的**技术实现体**；
- 包含了实现访问控制检查所需的所有硬件、固件、软件组件；
- 提供**最小可信执行环境**，类似于 hypervisor 的“ring 0”级别。

💡可以将 Reference Monitor 看作“访问控制的理论模型”，Security Kernel 是它的“实际执行引擎”。

The part of the TCB that validates access to every resource prior to granting access requests is called the reference monitor. The reference monitor stands between every subject and object, verifying that a requesting subject’s credentials meet the object’s access requirements before any requests are allowed to proceed. Effectively, the reference monitor is the access control enforcer for the TCB. The reference monitor enforces access control or authorization based on the desired security model, whether discretionary, mandatory, role-based, or some other form of access control. The collection of components in the TCB that work together to implement reference monitor functions is called the security kernel. The reference monitor is a concept or theory that is put into practice via the implementation of a security kernel in software and hardware. The purpose of the security kernel is to launch appropriate components to enforce reference monitor functionality and resist all known attacks. The security kernel mediates all resource access requests, granting only those requests that match the appropriate access rules in use for a system.

##### CISSP考点总结

| 概念               | 说明                                                        |
| ------------------ | ----------------------------------------------------------- |
| TCB                | 系统中负责强制执行安全策略的最小可信组件集合                |
| Security Perimeter | 分隔 TCB 与系统其他部分的边界，所有访问需通过受控通道       |
| Trusted Path       | 保障用户与 TCB 间交互不被篡改，如 Ctrl+Alt+Del 登录界面     |
| Reference Monitor  | 核心访问控制机制，所有 subject-object 请求必须通过它判断    |
| Security Kernel    | Reference Monitor 的实际代码+硬件实现，系统最敏感的部分之一 |

### 2. State Machine Model（状态机模型）

**状态机模型** 是一种理论模型，用于描述如何通过**系统状态的变化**来确保系统始终处于安全状态。它是许多安全模型（如 Bell-LaPadula、Biba）的**理论基础**。

该模型的核心思想源于计算机科学中的**有限状态机（Finite State Machine，FSM）**，FSM 是一个基于当前输入与当前状态，决定下一状态与输出的模型。

| 概念                         | 说明                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| **状态（State）**            | 系统在某一特定时刻的快照，包括用户会话、访问权限、系统资源等 |
| **输入（Input）**            | 用户行为、系统事件、指令或外部交互                           |
| **状态转移（Transition）**   | 接收输入或生成输出时，系统从一个状态转变到另一个状态         |
| **安全状态（Secure State）** | 当前系统状态满足安全策略的所有要求                           |
| **状态函数**                 | 数学表达为：`next_state = F(current_state, input)`           |
| **输出函数**                 | 表达为：`output = F(current_state, input)`                   |

#### State Machine 在安全中的应用

##### 🎯 核心安全思想：

如果系统从 **一个安全状态** 通过 **合法的输入与处理逻辑** 只能转移到 **另一个安全状态**，那么整个系统将始终维持在一个**安全状态机**中运行。✅ 这是一种对系统行为进行严格控制和验证的方法，确保**任意时间点**下都不偏离安全策略。

------

##### 🔄 示例说明

示例：访问控制状态机

假设有一个系统资源 `File_A`，其访问策略如下：

- 仅当用户角色是“Manager”时才能读取；
- 每当用户请求读取时，系统会检查当前状态（用户身份）与输入（读取请求）；
- 只有当 `current_state = Manager` 且 `input = Read_Request` 时，系统才允许状态转移为 `Access_Granted`。

其他任何组合都会导致转移为 `Access_Denied`。

> 📌 每个可能的“状态转移路径”都必须**显式验证是否会破坏安全性**。这就要求开发者在设计时**穷举并验证所有可能路径**。

**🧩 优点与实际意义**

| 优点                             | 说明                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| ✅ 强安全性验证基础               | 提供了形式化验证系统安全状态的理论模型                       |
| ✅ 可作为其他模型的基础（如 BLP） | Bell-LaPadula、Biba、Clark-Wilson 等都在其基础上建立安全约束 |
| ✅ 易于建模动态系统               | 模拟系统中的用户行为、指令处理、资源访问等状态变换           |

#### 🧪 安全状态机模型的三大要求

1. **系统启动于安全状态**；
2. **每次状态转移都验证是否安全**；
3. **仅允许合规的访问请求引起状态变化**；

如果这三项都满足，就可以说该系统是一个“**安全状态机模型**”。

------

#### 🧠 与 TCB 和 Reference Monitor 的关系

- **Reference Monitor** 依据安全策略决定是否允许某个状态转移；
- **Security Kernel** 实现这一判断机制；
- **State Machine Model** 则是理论基础，确保每次操作（即状态转移）都是合法的。

The state machine model describes a system that is always secure no matter what state it is in. It’s based on the computer science definition of a **finite state machine (FSM)**. An FSM combines an external input with an internal machine state to model all kinds of complex systems, including parsers, decoders, and interpreters. Given an input and a state, an FSM transitions to another state and may create an output. Mathematically, the next state is a function of the current state and the input next state—that is, the next state = F(input, current state). Likewise, the output is also a function of the input and the current state output—that is, the output = F(input, current state).

According to the state machine model, a state is a snapshot of a system at a specific moment in time. If all aspects of a state meet the requirements of the security policy, that state is considered secure. A transition occurs when accepting input or producing output.

A transition always results in a new state (also called a state transition). All state transitions must be evaluated. If each possible state transition results in another secure state, the system can be called a secure state machine. A secure state machine model system always boots into a secure state, maintains a secure state across all transitions, and allows subjects to access resources only in a secure manner compliant with the security policy. The secure state machine model is the basis for many other security models.

### 3. Information Flow Model（信息流模型）

📌 核心目标：控制信息在系统内**流动的合法性**

#### 定义与本质

信息流模型基于 **状态机模型** 构建，其核心思想是：**只允许授权的信息流通，不允许未授权的信息跨越边界。**

它不仅关注 **信息的“流向”**（如从高密级到低密级是否合理），还关注 **信息的“流类型”**（是否通过受控方式传输、是否包含敏感字段等）。

#### 主要作用

1. **防止信息泄露**
   确保高安全级别的信息不能通过直接或间接路径（如 covert channels，隐蔽通道）泄露到低级别。
2. **跨级别安全控制**
   实施在具有多级安全策略（Multilevel Security，MLS）的系统中，控制不同级别 Subject 与 Object 之间的信息流向。
3. **时间维度上的对象转换追踪**
   可用于比较一个对象在不同时间点的两个状态之间的信息变化，判断是否存在未经授权的修改或泄漏。

#### 信息流路径控制

在该模型中，系统中任意两个组件之间的通信都必须明确声明并被授权：

- ✔ 允许的信息路径（Authorized Flow）
- ❌ 禁止的路径：如 covert channel（隐蔽路径）、side-channel（侧信道）

例如：高密级用户向低密级用户复制文件——这是未授权的**向下信息流动**（write down），模型将拒绝此操作。

The information flow model focuses on controlling the flow of information. Information flow models are based on the state machine model. Information flow models don’t necessarily deal with only the direction of information flow; they can also address the type of flow.

Information flow models are designed to prevent unauthorized, insecure, or restricted information flow, often between different levels of security (known as multilevel models). Information flow can be between subjects and objects at the same or different classification levels. An information flow model allows all authorized information flows, and prevents all unauthorized information flows.

Another interesting perspective on the information flow model is that it is used to establish a relationship between two versions or states of the same object when those two versions or states exist at different points in time. Thus, information flow dictates the transformation of an object from one state at one point in time to another state at another point in time. The information flow model also addresses covert channels by specifically excluding all undefined flow pathways.

### 4. Noninterference Model（非干扰模型）

核心目标：**低级别用户不应感知到高级别用户的行为**

#### 定义与本质

非干扰模型是建立在信息流模型基础之上的更严格模型，其理念是：

> “一个高级别用户的行为**不能对**低级别用户产生**任何可感知的影响**。”

这是信息流模型的一个**保密性扩展**，强调**不可见性**与**系统状态的独立性**。

#### 问题示例

假设 Subject A 是一个拥有密级信息的高级别用户，Subject B 是一个访客用户。

- 若 A 执行某操作导致系统反应时间变慢，B 可能感知到此行为，从而**推断出某些信息**；
- 即使没有直接信息传递，只要存在“干扰”行为，也可能泄露敏感信息。

因此，非干扰模型试图构建这样一种环境：

> **高密级的用户活动是“透明”的，低密级用户无法感知系统中其他人的行为。**

#### 应用场景

- 防止 covert channel、timing channel 等隐蔽通道攻击；
- 适用于对信息隔离要求极高的军事或政府系统；
- 防范恶意软件（如木马程序）通过间接方式泄露敏感数据。

The noninterference model is loosely based on the information flow model. However, instead of being concerned about the flow of information, the noninterference model is concerned with how the actions of a subject at a higher security level affect the system state or the actions of a subject at a lower security level. Basically, the actions of subject A (high) should not affect or interfere with the actions of subject B (low) or even be noticed by subject B. If such violations occur, subject B may be placed into an insecure state or be able to deduce or infer information about a higher level of classification. This is a type of information leakage and implicitly creates a covert channel. Thus, the noninterference model can be imposed to provide a form of protection against damage caused by malicious programs, such as Trojan horses, backdoors, and rootkits.

#### Composition Theories（组合理论）

组合理论进一步分析多个系统之间如何组合时确保信息流的安全性。

| 模型                  | 描述                                                     |
| --------------------- | -------------------------------------------------------- |
| **Cascading（级联）** | 系统 A 的输出作为系统 B 的输入，用于信息逐层传递         |
| **Feedback（反馈）**  | 系统 A 和 B 互为输入输出，形成**循环路径**，信息双向流动 |
| **Hookup（连接）**    | 系统 A 既将信息传给系统 B，又将信息发往外部实体          |

这些理论帮助分析**系统组合**后信息流模型是否依然成立，从而避免系统间联合导致的新信息泄露路径。

Some other models that fall into the information flow category build on the notion of inputs and outputs between multiple systems. These are called composition theories because they explain how outputs from one system relate to inputs to another system. There are three composition theories:

- Cascading: Input for one system comes from the output of another system.
- Feedback: One system provides input to another system, which reciprocates by reversing those roles (so that system A first provides input for system B and then system B provides input to system A).
- Hookup: One system sends input to another system but also sends input to external entities.

| 模型                       | 关注重点                         | 目标                                       |
| -------------------------- | -------------------------------- | ------------------------------------------ |
| **Information Flow Model** | 信息在系统内的“合法路径”与“途径” | 限制未经授权的信息泄露，规范流向和流量     |
| **Noninterference Model**  | 高级行为是否被低级感知           | 确保敏感活动对外不可见，避免推测与泄露     |
| **Composition Theories**   | 多系统联合后的信息流行为         | 判断系统组合后是否出现非法路径或新泄露通道 |

### 5. Take-Grant Model

#### 核心理念

用图论描述权限的“获取与传播”。Take-Grant 模型使用**有向图**（Directed Graph）来表示系统中 **权限如何在主体和对象之间传递**。图中的每个节点代表主体（subject）或对象（object），边（edge）上标注的是当前的访问权限或操作能力。

#### 四大规则（基本操作）

| 规则                  | 描述                                                         |
| --------------------- | ------------------------------------------------------------ |
| **1. Take（取得）**   | 如果主体 `X` 有“take”权限，则 `X` 可以从另一个主体 `Y` 处“取得”某个权限。 |
| **2. Grant（授予）**  | 如果主体 `X` 有“grant”权限，则 `X` 可以将自己拥有的某个权限授予给另一个主体 `Y`。 |
| **3. Create（创建）** | 允许主体创建新对象并自动成为其拥有者，也可新建权限边。       |
| **4. Remove（移除）** | 允许主体删除其对某对象的权限。                               |

四个操作定义了**权限传播**的完整生命周期，从生成 (Create)、赋予 (Grant)、扩散 (Take)，到撤销 (Remove)。

The take-grant model employs a directed graph to dictate how rights can be passed from one subject to another or from a subject to an object. Simply put, a subject (X) with the grant right can grant another subject (Y) or another object (Z) any right that subject (X) possesses. Likewise, a subject (X) with the take right can take a right from another subject (Y). In addition to these two primary rules, the take-grant model has a create rule and a remove rule to generate or delete rights. The key to this model is that using these rules allows you to figure out when rights in the system can change and where leakage (that is, unintentional distribution of permissions) can occur.

In essence, here are the four rules of the take-grant model:

1. Take rule: Allows a subject to take rights over an object
2. Grant rule: Allows a subject to grant rights to an object
3. Create rule: Allows a subject to create new rights
4. Remove rule: Allows a subject to remove rights it has

It is interesting to ponder that the take and grant rules are effectively a copy function. This can be recognized in modern OSes in the process of inheritance, such as subjects inheriting a permission from a group or a file inheriting ACL values from a parent folder. The two additional rules (create and remove), which are not defined by a directed graph, are also commonly present in modern operating systems. For example, to obtain permission on an object, that permission does not have to be copied from a user account that already has that permission; instead, it is simply created by an account with privilege capability of create or assign permissions (which can be the owner of an object or a subject with full control or administrative privileges over the object).

#### 安全分析与权限泄漏

该模型可以用来分析：

- **权限是否会“泄漏”**：即是否存在主体在没有明确授权的前提下，通过链式传播间接获得敏感权限。
- **最小权限传播路径**：可以通过图遍历算法找到某个权限可能扩散的最短路径。

现代操作系统中，“继承权限”（如 Windows 文件夹权限继承）就可以看作 take-grant 的一种表现形式。

#### 应用场景

- 文件系统权限分析
- 操作系统中权限继承推理
- 访问路径可达性验证（是否存在非法权限传播路径）

### 6. Access Control Matrix（访问控制矩阵）

**核心理念：二维矩阵形式展现“谁可以对什么资源做什么事”**

该模型通过一个矩阵表示**主体（subjects）对客体（objects）拥有的操作权限**：

|        | Object A | Object B | Object C |
| ------ | -------- | -------- | -------- |
| User X | Read     | Write    | —        |
| User Y | —        | Read     | Execute  |

其中：

- 行（Row）对应于 **主体（User/Process）**
- 列（Column）对应于 **对象（File/Printer）**
- 单元格的内容即为该用户对该资源的**访问权限集合**

An access control matrix is a table of subjects and objects that indicates the actions or functions that each subject can perform on each object. Each column of the matrix is an access control list (ACL) pulled from objects. Once sorted, each row of the matrix is a capabilities list for each listed subject. An ACL is tied to an object; it lists the valid actions each subject can perform. A capability list is tied to the subject; it lists valid actions that can be taken on each object included in the matrix.

From an administration perspective, using only capability lists for access control is a management nightmare. A capability list method of access control can be accomplished by storing on each subject a list of rights the subject has for every object. This effectively gives each user a key ring of accesses and rights to objects within the security domain. To remove access to a particular object, every user (subject) that has access to it must be individually manipulated. Thus, managing access on each user account is much more difficult than managing access on each object (in other words, via ACLs). A capabilities table can be created by pivoting an access control matrix; this results in the columns being subjects and the rows being ACLs from objects.

#### 衍生术语

| 概念                            | 定义                                                   | 本质结构   |
| ------------------------------- | ------------------------------------------------------ | ---------- |
| **ACL（访问控制列表）**         | 针对某个对象 (Object)，记录所有允许访问它的主体及操作  | **列视角** |
| **Capabilities List（能力表）** | 针对某个主体 (Subject)，列出其对所有对象拥有的操作权限 | **行视角** |

#### ACL vs. Capabilities 对比

| 特征       | ACL（基于对象）       | Capabilities（基于主体） |
| ---------- | --------------------- | ------------------------ |
| 管理便捷性 | ✅ 只改一处（对象）    | ❌ 多用户要同步修改权限   |
| 灵活性     | ✅ 适合资源共享控制    | ❌ 不适合频繁变化的环境   |
| 现实应用   | Windows/Unix 文件系统 | 通常不直接暴露           |
| 安全审计   | ✅ 适合进行资源级审计  | ❌ 难以集中管理资源       |

#### 现实意义

访问控制矩阵被广泛应用于：

- **文件系统权限管理（Windows ACL、Linux chmod）**
- **数据库访问控制（如 GRANT 语句）**
- **用户角色权限设计（RBAC/ABAC 的底层原型）**
- **安全策略自动审计工具中用于检测权限过度分配**

#### 总结对比

| 模型                      | 特点                           | 优势                       | 缺点                            |
| ------------------------- | ------------------------------ | -------------------------- | ------------------------------- |
| **Take-Grant 模型**       | 图结构表达权限转移（动态演化） | 模拟权限继承/传播路径      | 分析较复杂，不直观              |
| **Access Control Matrix** | 矩阵表达静态访问权限           | 清晰直观，适合静态权限管理 | 可扩展性差，主体/对象多时不实用 |

### 7. Bell-LaPadula Model（保密性导向）- BLP模型 - 以机密性为核心

Bell–LaPadula 模型由美国国防部（DoD）于 1970 年代开发，专为多级安全策略（Multilevel Security, MLS）设计，**重点是防止敏感信息泄漏**。

它适用于军事或政府级系统，特别关注保密性（Confidentiality），通过控制信息从“高等级”向“低等级”流动来防止信息泄露。

#### 三大核心规则

| 属性                                | 说明                                              | 别名                       |
| ----------------------------------- | ------------------------------------------------- | -------------------------- |
| **Simple Security Property**        | **“No Read Up”**：不能读取比自己更高级别的对象    | 防止低权限人员访问敏感信息 |
| **Star (\*) Property**              | **“No Write Down”**：不能写入比自己低级别的对象   | 防止信息向低密级泄露       |
| **Discretionary Security Property** | 使用访问控制矩阵来进行基于所有者的访问控制（DAC） | 限定在同级别中的操作       |

✅重点记忆方式：

- **Simple = Read，Star = Write**
- Bell–LaPadula = **No Read Up, No Write Down**

The U.S. Department of Defense (DoD) developed the Bell–LaPadula model in the 1970s based on the DoD’s multilevel security policies. The multilevel security policy states that a subject with any level of clearance can access resources at or below its clearance level. However, within clearance levels, access to compartmentalized objects is granted only on a need-to-know basis.

By design, the Bell–LaPadula model prevents the leaking or transfer of classified information to less secure clearance levels. This is accomplished by blocking lower-classified subjects from accessing higher-classified objects. With these restrictions, the Bell–LaPadula model is focused on maintaining confidentiality and does not address any other aspects of object security.

#### Lattice-Based Access Control（格状访问控制）

BLP 是**强制访问控制（MAC）**的一种实现形式，安全级别构成一个**“格”（Lattice）**。
主体只能访问“**上下界**”之间的资源 —— 比如：机密（Confidential）只能访问“保密 ≤ 等级 ≤ 机密”的对象。

#### Trusted Subject 特权用户例外

特权用户（trusted subject）可以打破 * 属性规则（即允许写入低级别对象），用于**合法的信息降密操作**（如公开解密文档）。

#### 局限性

- 只关注**保密性** (Confidentiality)，忽略完整性 (Integrity) 与可用性 (Availability)；
- 假设所有系统转换都安全；
- 不支持现代特性如共享、联网；
- 不防止 covert channel（隐蔽通道）泄漏。

Subjects under lattice-based access controls are assigned positions in a lattice (i.e., a multilayered security structure or multileveled security domains). Subjects can access only those objects that fall into the range between the least upper bound (LUB) (the nearest security label or classification higher than their lattice position) and the greatest (i.e., highest) lower bound (GLB) (the nearest security label or classification lower than their lattice position) of the labels or classifications for their lattice position.

This model is built on a state machine concept and the information flow model. It also employs mandatory access controls and is a lattice-based access control concept. The lattice tiers are the classification levels defined by the security policy of the organization.

There are three basic properties of this state machine:

1. The Simple Security Property states that a subject may not read information at a higher sensitivity level (no read-up).

2. The * (star) Security Property states that a subject may not write information to an object at a lower sensitivity level (no write-down). This is also known as the Confinement Property.

3. The Discretionary Security Property states that the system uses an access matrix to enforce discretionary access control.

These first two properties define the states into which the system can transition. No other transitions are allowed. All states accessible through these two rules are secure states. Thus, Bell–LaPadula–modeled systems offer state machine model security.

The Bell–LaPadula properties are in place to protect data confidentiality. A subject cannot read an object that is classified at a higher level than the subject is cleared for. Because objects at one level have data that is more sensitive or secret than data in objects at a lower level, a subject (who is not a trusted subject) cannot write data from one level to an object at a lower level. That action would be similar to pasting a top-secret memo into an unclassified document file. The third property enforces a subject’s job/role-based need to know in order to access an object.

An exception in the Bell–LaPadula model states that a “trusted subject” is not constrained by the * Security Property. A trusted subject is defined as “a subject that is guaranteed not to consummate a securitybreaching information transfer even if it is possible.” This means that a trusted subject is allowed to violate the * Security Property and perform a write-down, which is necessary when performing valid object declassification or reclassification.

The Bell–LaPadula model was designed in the 1970s, so it does not support many operations that are common today, such as file sharing and networking. It also assumes secure transitions between security layers and does not address covert channels

### 8. Biba Model - 以完整性为核心

核心区别：关注数据是否被篡改 - Integrity
Biba 模型诞生于 Bell–LaPadula 之后，是其“镜像模型”，关注防止数据污染，强调保持数据完整性（Integrity），特别适用于财务系统、数据库系统等对数据真实性要求极高的场景。

#### 两大核心规则

| 属性                             | 说明                                             | 别名               |
| -------------------------------- | ------------------------------------------------ | ------------------ |
| **Simple Integrity Property**    | **“No Read Down”**：不能读取较低完整性级别的数据 | 防止引入不可信输入 |
| **Star (\*) Integrity Property** | **“No Write Up”**：不能写入较高完整性级别的数据  | 防止污染可信输出   |

✅记忆方法：

- **Simple = Read，Star = Write**
- Biba = **No Read Down, No Write Up**

#### 举例说明

假设一个“高完整性”财务报表系统中，某员工账户等级较低，则：

- 他**不能读取（read）**未经验证的数据（如互联网用户输入）；
- 他**不能写入（write）**正式报表，以防引入错误或恶意修改。

------

#### 设计目标

- 防止未授权主体修改对象；
- 防止授权主体误改对象；
- 保证对象的内部一致性（如校验和）和外部一致性（数据源准确性）；

------

#### 局限性

- 不支持机密性（Confidentiality）或可用性（Availability）；
- 假设程序能正确控制内部权限；
- 不考虑权限分配策略；
- 同样不防止 covert channel 攻击。

The Biba model was designed after the Bell–LaPadula model, but it focuses on integrity. The Biba model is also built on a state machine concept, is based on information flow, and is a multilevel model. In fact, the Biba model is the inverted Bell–LaPadula model. The properties of the Biba model are as follows:

1. The Simple Integrity Property states that a subject cannot read an object at a lower integrity level (no read-down).

2. The * (star) Integrity Property states that a subject cannot modify an object at a higher integrity level (no write-up).

In both the Biba and Bell–LaPadula models, there are two properties that are inverses of each other: simple and * (star). However, they may also be labeled as axioms, principles, or rules. What you should focus on is the simple and star designations. Take note that simple is always about reading and star is always about writing. In both cases, the rules define what cannot or should not be done. Usually, what is not prevented or blocked is allowed. Thus, even though a rule is stated as a No declaration, its opposite direction is implied as allowed. On the exam, the first and best answer as to the definition or meaning of a property is the negative statement, but if that is not an option, then the opposite implied operation is the next best selection.

Consider the Biba properties. The second property of the Biba model is pretty straightforward. A subject cannot write to an object at a higher integrity level. That makes sense. What about the first property? Why can’t a subject read an object at a lower integrity level? The answer takes a little thought. Think of integrity levels as being like the purity level of air. You would not want to pump air from the smoking section into the clean room environment. The same applies to data. When integrity is important, you do not want unvalidated data read into validated documents. The potential for data contamination is too great to permit such access.

Biba was designed to address three integrity issues:

1. Prevent modification of objects by unauthorized subjects
2. Prevent unauthorized modification of objects by authorized subjects
3. Protect internal and external object consistency

Biba requires that all subjects and objects have a classification label (it is still a DoD-derived security model). Thus, data integrity protection is dependent on data classification.

Critiques of the Biba model reveal a few drawbacks:

- It addresses only integrity, not confidentiality or availability.
- It focuses on protecting objects from external threats; it assumes that internal threats are handled programmatically.
- It does not address access control management, and it doesn’t provide a way to assign or change an object’s or subject’s classification level.
- It does not prevent covert channels.

Memorizing the properties of Bell–LaPadula and Biba can be challenging, but there is a shortcut. If you can memorize the graphical layout in Figure 8.6 above the dotted line, then you can figure out the rest. Notice that Bell–LaPadula is placed on the left and Biba is on the right, and the security benefit of each is listed below the model name. Then only the Bell–LaPadula model’s simple property is listed. That property is “No Read Up,” which is represented by an arrow pointing upward that is crossed out and labeled by an “S” for simple and an “R” for read. From there, all of the other rules are the opposing element of the pair or inverted. By memorizing the top graphic, once you are in the exam, you can draw that out on the provided dry-erase board. Then, you can quickly create the other rules. First, under Bell–LaPadula draw an arrow pointing down, cross it out, then label it with an “*” for start and a “W” for write. Now you have the “No Write Down” star property. You can then draw dotted arrows in the opposite direction of these two to indicate the implied opposite direction is allowed. Then take these four arrows of Bell–LaPadula and completely flip them over top to bottom to create the rules for Biba. The result should be the bottom graphic below the dotted line.

#### Bell–LaPadula vs Biba 对比总结

| 特征             | Bell–LaPadula                 | Biba                               |
| ---------------- | ----------------------------- | ---------------------------------- |
| 关注点           | **机密性（Confidentiality）** | **完整性（Integrity）**            |
| 应用场景         | 军事、情报、国家安全          | 商业、财务、工业控制系统           |
| Simple 属性      | No Read Up                    | No Read Down                       |
| Star (*) 属性    | No Write Down                 | No Write Up                        |
| 防止信息泄露方向 | 从高机密向低机密              | 从低完整性向高完整性               |
| 允许的例外       | Trusted Subject 可降密        | 无特权主体可以破例写入高完整性数据 |
| 安全属性覆盖     | 只关注保密性                  | 只关注完整性                       |

#### 记忆图形法（考试技巧）

- Bell–LaPadula（机密）→ ❌↑读，❌↓写
- Biba（完整性）→ ❌↓读，❌↑写
- 两者图形对称：一个关注信息**向下泄露**，一个关注信息**向上传染**

### 9. Clark-Wilson Model - **基于商业完整性的保护**

**模型目标**: Clark–Wilson 模型专注于**商业环境中的数据完整性保护**。其核心理念是：**不允许用户直接访问数据，而是必须通过受控程序（Transformation Procedure, TP）进行访问或修改**。

#### 核心机制：访问控制三元组（Access Control Triplet）

| 组成部分                           | 作用                           |
| ---------------------------------- | ------------------------------ |
| **Subject（用户）**                | 发起操作请求的人或进程         |
| **TP（Transformation Procedure）** | 控制对数据操作的受限程序接口   |
| **Object（对象）**                 | 被访问的数据项（如数据库记录） |

用户只能通过 TP 接口访问数据，这种“间接访问”是模型的根本。

#### 关键概念

| 项目                                        | 定义                             |
| ------------------------------------------- | -------------------------------- |
| **CDI（Constrained Data Item）**            | 被模型保护的敏感数据             |
| **UDI（Unconstrained Data Item）**          | 未受控制的输入或输出数据         |
| **TP（Transformation Procedure）**          | 仅有的可用于修改 CDI 的程序      |
| **IVP（Integrity Verification Procedure）** | 用于扫描验证数据完整性的一种机制 |

#### 两大核心原则

1. **Well-Formed Transactions（结构良好的事务）**
   只有通过授权 TP 才能修改数据，防止未授权篡改。
2. **Separation of Duties（职责分离）**
   操作分离（如一人录入、一人审批），防止内部欺诈或滥用。

------

#### 其他特性

- 使用**受限接口模型**，可限制用户只能看到/操作授权内容；
- 虽设计用于完整性，但中间层 TP 也可兼顾保密性；
- 常用于金融、ERP、商业数据系统。

The Clark–Wilson model uses a multifaceted approach to enforcing data integrity. Instead of defining a formal state machine, the Clark–Wilson model defines each data item and allows modifications through only a limited or controlled intermediary program or interface.

The Clark–Wilson model does not require the use of a lattice structure; rather, it uses a three-part relationship of subject/program/object (or subject/transaction/object) known as a triple or an access control triplet. Subjects do not have direct access to objects. Objects can be accessed only through programs. Through the use of two principles—well-formed transactions and separation of duties—the Clark–Wilson model provides an effective means to protect integrity.

Well-formed transactions take the form of programs. A subject is able to access objects only by using a program, interface, or access portal. Each program has specific limitations on what it can and cannot do to an object (such as a database or other resource). This effectively limits the subject’s capabilities. This is known as a constrained, limiting, or restrictive interface. If the programs are properly designed, then the triple relationship provides a means to protect the integrity of the object.

Clark–Wilson defines the following items and procedures:

- A constrained data item (CDI) is any data item whose integrity is protected by the security model.
- An unconstrained data item (UDI) is any data item that is not controlled by the security model. Any data that is to be input and hasn’t been validated, or any output, would be considered an unconstrained data item.
- An integrity verification procedure (IVP) is a procedure that scans data items and confirms their integrity.
- Transformation procedures (TPs) are the only procedures that are allowed to modify a CDI. The limited access to CDIs through TPs forms the backbone of the Clark–Wilson integrity model.

The Clark–Wilson model uses security labels to grant access to objects, but only through transformation procedures and a restricted interface model. A restricted interface model uses classification-based restrictions to offer only subject-specific authorized information and functions. One subject at one classification level will see one set of data and have access to one set of functions, whereas another subject at a different classification level will see a different set of data and have access to a different set of functions. The different functions made available to different levels or classes of users may be implemented by either showing all functions to all users but disabling those that are not authorized for a specific user or by showing only those functions granted to a specific user. Through these mechanisms, the Clark–Wilson model ensures that data is protected from unauthorized changes from any user. In effect, the Clark–Wilson model enforces separation of duties. The Clark–Wilson design makes it a common model for commercial applications.

**Note:** The Clark–Wilson model was designed to protect integrity using the access control triplet. However, though the intermediary interface can be programmed to limit what can be done to an object by a subject, it can just as easily be programmed to limit or restrict what objects are shown to a subject. Thus, this concept can lend itself readily to protect confidentiality. In many situations there is an intermediary program between a subject and an object. If the focus of that intermediary is to protect integrity, then it is an implementation of the Clark–Wilson model. If it is intended to protect confidentiality, then they are benefiting from an alternate use of the intermediary program. Use of the access control triplet to protect confidentiality does not seem to have its own model name.

### 10. Brewer and Nash Model（中国墙模型）

模型目标: Brewer–Nash 模型聚焦于**动态访问控制 + 冲突隔离**，专为解决“**利益冲突问题**”而设计，例如会计师不能同时服务于两家竞争公司。

#### 应用场景

- 财务审计
- 咨询公司
- 法律服务
- 任何可能产生**利益冲突**的环境

#### 工作原理

- 一旦用户访问了一个**冲突类（Conflict Class）中的数据（如公司 A 的文档），系统将自动屏蔽**该用户访问该冲突类中其他实体（如公司 B）数据的权限。
- 这种**“信息气泡”或“动态隔离”**机制称为 **Cone of Silence** 或 Ethical Wall。
- 冲突类与用户权限是**动态变化的**，随着访问行为自动调整。

#### 组成元素

| 项目                           | 定义                                     |
| ------------------------------ | ---------------------------------------- |
| **Subject（用户）**            | 操作系统的主体                           |
| **Object（数据对象）**         | 如公司文档、项目文件等                   |
| **Conflict Class（冲突类）**   | 一组相互存在利益冲突的对象（如竞争公司） |
| **Access History（访问历史）** | 用于动态决定当前允许访问的数据集         |

### 示例说明

审计员 A 第一次访问了“公司 X”的财务报表，那么系统将自动阻止他访问“公司 Y”（竞争对手）的任何敏感数据，直到当前任务结束。

The Brewer and Nash model was created to permit access controls to change dynamically based on a user’s previous activity (making it a kind of state machine model as well). This model applies to a single integrated database; it seeks to create security domains that are sensitive to the notion of conflict of interest (for example, someone who works at company C who has access to proprietary data for company A should not also be allowed access to similar data for company B if those two companies compete with each other). This model creates a class of data that defines which security domains are potentially in conflict and prevents any subject with access to one domain that belongs to a specific conflict class from accessing any other domain that belongs to the same conflict class. Metaphorically, this puts a wall around all other information in any conflict class. Thus, this model also uses the principle of data isolation within each conflict class to keep users out of potential conflict-of-interest situations (for example, management of company datasets). Because company relationships change all the time, dynamic updates to members of and definitions for conflict classes are important.

Another way of looking at or thinking of the Brewer and Nash model is of an administrator having full control access to a wide range of data in a system based on their assigned job responsibilities and work tasks. However, at the moment an action is taken against any data item, the administrator’s access to any conflicting data items is temporarily blocked. Only data items that relate to the initial data item can be accessed during the operation. Once the task is completed, the administrator’s access returns to full control.

Brewer and Nash was sometimes known as the Chinese Wall model, but this term is deprecated. Instead, other terms of “ethical wall” and “cone of silence” have been used to describe Brewer and Nash.

| 特征           | **Clark–Wilson 模型**                | **Brewer–Nash 模型**               |
| -------------- | ------------------------------------ | ---------------------------------- |
| 核心目标       | **保护完整性**（防止数据被随意更改） | **避免利益冲突**（防止多重访问）   |
| 模型类型       | **三元组模型（Subject–TP–Object）**  | **动态状态模型（基于访问历史）**   |
| 是否使用中间层 | ✅ 通过受控接口程序访问数据           | ❌ 直接动态隔离                     |
| 应用场景       | 商业系统、金融、ERP                  | 法律、财务、咨询等有冲突需求的环境 |
| 动态权限调整   | ❌ 静态访问控制，需预定义角色和接口   | ✅ 根据用户行为动态调整权限         |
| 是否关注保密性 | 可扩展保护保密性（非原始设计目的）   | 可实现隐式保密（通过隔离实现）     |

#### 总结记忆建议

- **Clark–Wilson**：强调流程控制 + 数据接口 → 强完整性 + 适合商业系统
- **Brewer–Nash**：强调动态利益隔离 + 避免冲突 → 适合法律财务

### 11. Goguen-Meseguer Model（非干扰模型的奠基）

模型类型：**完整性模型**（非传统）

#### 模型核心思想

- 基于 **自动化理论** 和 **领域分离（domain separation）**。
- 每个主体（subject）被事先指定能访问的一组对象（object）。
- 主体只能对**预定义对象集合**执行**预定义操作**，不允许任意行为。
- **一个主体域的成员不能影响另一个域的成员**，实现行为隔离。

**目标：**通过预定义访问规则和分组隔离，**防止主体之间的交叉干扰（interference）**，实现高完整性控制。

The Goguen–Meseguer model is an integrity model, although not as well known as Biba and the others. In fact, this model is said to be the foundation of noninterference conceptual theories. Often when someone refers to a noninterference model, they are actually referring to the Goguen–Meseguer model.

The Goguen–Meseguer model is based on predetermining the set or domain (i.e., a list) of objects that a subject can access. This model is based on automation theory and domain separation. This means subjects are allowed only to perform predetermined actions against predetermined objects. When similar users are grouped into their own domain (that is, collective), the members of one subject domain cannot interfere with the members of another subject domain. Thus, subjects are unable to interfere with each other’s activities.

### 12. Sutherland Model（非干扰的形式化表达）

模型类型：**完整性模型**

#### 模型核心

- 基于 **状态机模型（State Machine）** 和 **信息流模型（Information Flow）**；
- 不强调具体的保护机制，而是关注：
  - 合法的初始状态；
  - 被允许的状态转换；
  - 系统状态不可被非授权主体操控。

应用场景举例：

- 防止 **隐蔽通道（Covert Channel）**；
- 保护决策过程或计算过程不被信息泄露或篡改。

The Sutherland model is an integrity model. It focuses on preventing interference in support of integrity. It is formally based on the state machine model and the information flow model. However, it does not directly indicate specific mechanisms for protection of integrity. Instead, the model is based on the idea of defining a set of system states, initial states, and state transitions. Through the use of only these predetermined secure states, integrity is maintained and interference is prohibited.

A common example of the Sutherland model is its use to prevent a covert channel from being used to influence the outcome of a process or activity. 

### 13. Graham-Denning Model - **面向对象/主体生命周期的权限模型**

模型类型：**访问控制模型**

模型特色: 通过**八种操作规则（protection rules）**实现主体与对象的安全生命周期管理。

#### 八个操作

1. 创建对象
2. 创建主体
3. 删除对象
4. 删除主体
5. 授予读取权限
6. 授予传递（Grant）权限
7. 授予删除权限
8. 授予转移（Transfer）权限

这些操作作用于 **访问控制矩阵（Access Control Matrix）** 上——类似于现代操作系统的权限分配逻辑。

The Graham–Denning model is focused on the secure creation and deletion of both subjects and objects. Graham–Denning is a collection of eight primary protection rules or actions that define the boundaries of certain secure actions:

- Securely create an object.
- Securely create a subject.
- Securely delete an object.
- Securely delete a subject.
- Securely provide the read access right.
- Securely provide the grant access right.
- Securely provide the delete access right.
- Securely provide the transfer access right.

Usually the specific abilities or permissions of a subject over a set of objects is defined in an access matrix (aka access control matrix).

### 14. Harrison-Ruzzo-Ullman Model (HRU) 模型：**可修改访问矩阵的模型**

模型类型：**动态访问控制模型**

#### HRU 的核心扩展

- 是 **Graham–Denning 模型的扩展**；
- 强调：
  - 权限的**动态赋予与撤销**；
  - 对权限操作本身的控制流程；
  - 系统状态由一个可修改的**访问控制矩阵**表示；
  - 权限编辑由一组**原语（primitives）命令**实现。

#### 原语操作包括

- 增加/移除 权限；
- 增加/移除 主体与对象；
- 所有操作必须满足一致性规则：**事务原子性（要么全部成功，要么全部失败）**。

The Harrison–Ruzzo–Ullman (HRU) model focuses on the assignment of object access rights to subjects as well as the resilience of those assigned rights. It is an extension of the Graham–Denning model. It is centered around the establishment of a finite set of procedures (or access rights) that can be used to edit or alter the access rights of a subject over an object. The state of access rights under HRU can be expressed in a matrix, where the rows are subjects and the columns are objects (which will include the subjects because they can be objects as well). The intersection of each row and column will include the specific procedures that each subject is allowed to perform against each object. Additionally, a finite set of commands or primitives is defined that controls how the matrix can be modified by authorized subjects. These primitives include adding or removing access rights, subjects, and/or objects from the matrix. There are also integrity rules, such as: in order to create or add a subject or object to the matrix, it must not already exist; in order to remove a subject or object from the matrix, it must already exist; and if several commands are performed at once, they must all operate successfully or none of the commands will be applied.

#### Disambiguating the Word “Star” in Models

##### 关于“Star”的多重含义

| 使用位置               | 含义                              | 说明                                                        |
| ---------------------- | --------------------------------- | ----------------------------------------------------------- |
| Bell–LaPadula 模型     | *（星号）安全属性                 | **不允许向低级别写入（No Write Down）**，保护**保密性**     |
| Biba 模型              | *（星号）完整性属性               | **不允许向高完整性对象写入（No Write Up）**，保护**完整性** |
| CSA STAR Program       | Security Trust Assurance and Risk | **云安全联盟的认证与审计计划**，非模型                      |
| Galbraith's Star Model | 企业组织结构模型                  | 侧重于战略、结构、人事等组织管理，**与信息安全无关**        |

在考试或实际环境中遇到“star”，请结合上下文判断是：

- 安全模型的属性（Bell–LaPadula / Biba）；
- 云服务审计框架（CSA STAR）；
- 组织设计理论（Galbraith）；

The term star presents a few challenges when it comes to security models. For one thing, there is no formal security model named “Star Model.” However, both the Bell–LaPadula and the Biba models have a star property, which is discussed in their respective sections in this chapter.

Although not a model, the Cloud Security Alliance (CSA) also has a STAR program. CSA’s Security Trust Assurance and Risk (STAR) program focuses on improving cloud service provider (CSP) security through auditing, transparency, and integration of standards.

Although not related to security, there is also Galbraith’s Star Model, which helps businesses organize divisions and departments to achieve business missions and goals and adjust over time for long-term viability. This model is based around five main areas of business administration that need to be managed, balanced, and harnessed toward the mission and goals of the organization. The five areas of Galbraith’s Star Model are Strategy, Structure, Processes, Rewards, and People.

Understanding how “star” is used in the context of the Bell–LaPadula and Biba models, CSA’s STAR program, and Galbraith’s Star Model will help you distinguish what is meant when you see the word used in different contexts.

总结对比

| 模型            | 类型         | 关键概念                  | 特点/适用                               |
| --------------- | ------------ | ------------------------- | --------------------------------------- |
| Goguen–Meseguer | 完整性       | 域隔离、预定义访问        | 非干扰理论基础                          |
| Sutherland      | 完整性       | 状态限制、防止干扰        | 应用于隐蔽通道防护                      |
| Graham–Denning  | 访问控制     | 8项安全操作               | 安全生命周期管理                        |
| HRU             | 访问控制     | 权限动态编辑+矩阵模型     | 对权限演化建模                          |
| “Star” 属性     | 安全模型概念 | * 读/写限制（与方向相关） | 保密性（Bell-LaPadula）与完整性（Biba） |

#### **信息安全模型对照总览表**

| 模型名称                        | 模型类型                   | 核心关注点               | 关键属性                                   | 适用场景/优势                       |
| ------------------------------- | -------------------------- | ------------------------ | ------------------------------------------ | ----------------------------------- |
| **Bell–LaPadula**               | 机密性（Confidentiality）  | 防止信息泄露             | - No Read Up- No Write Down（* Star）- DAC | 多级保密系统，军用/政府保密数据环境 |
| **Biba**                        | 完整性（Integrity）        | 防止数据被低完整性污染   | - No Read Down- No Write Up（* Star）      | 商业场景，数据不能被篡改或污染      |
| **Clark–Wilson**                | 完整性（Integrity）        | 分离职责 + 限制接口      | - 三元组(S/P/O)- TP/CDI/UDI/IVP            | 商业数据库系统，ERP/金融系统        |
| **Brewer–Nash**（Chinese Wall） | 动态访问控制               | 避免利益冲突             | 动态访问决策（基于历史行为）               | 顾问、法律、投资行业的合规控制      |
| **Goguen–Meseguer**             | 完整性 / 非干扰            | 域分离 / 自动机          | 固定行为集合 + 无交叉域干扰                | 基础理论，非干扰模型的起点          |
| **Sutherland**                  | 完整性 / 信息流            | 状态限制 + 禁止推理干扰  | 合法状态转换，控制隐蔽通道                 | 高完整性计算、推理阻断系统          |
| **Graham–Denning**              | 访问控制（Access Control） | 主体与对象的生命周期管理 | 8个操作规则：创建/删除/授权/转移等         | 安全管理系统，操作系统              |
| **Harrison–Ruzzo–Ullman (HRU)** | 动态访问控制               | 权限变化及可验证性       | 基于访问控制矩阵 + 原语操作规则            | 细粒度权限控制、权限继承与变化      |
| **Take–Grant**（有向图）        | 权限传递                   | 权限继承与复制           | Take / Grant / Create / Remove 四规则      | 授权系统，现代 ACL 权限结构建模     |
| **Access Control Matrix**       | 基础访问控制模型           | 主体-对象-操作 映射      | 行为矩阵：行=主体，列=对象                 | 系统权限表建模基础，操作系统        |
| **State Machine Model**         | 基础理论模型               | 状态 + 状态转换的安全性  | 安全状态定义与验证                         | 其他模型（如 Bell/Biba）的基础      |
| **Information Flow Model**      | 信息流控制                 | 控制信息流向、类型       | 阻止未授权流动 + 控制转换路径              | 多级系统、混合级别对象流            |
| **Noninterference**             | 信息流控制                 | 不可见性、无影响行为     | 高级别行为不影响低级别状态                 | 隐蔽通道/推理攻击防护               |
| **Galbraith Star Model**        | 非安全领域                 | 企业组织设计             | 战略/结构/人员等五元素                     | （非信息安全）组织战略管理          |
| **CSA STAR Program**            | 云安全框架                 | 审计 / 风险 / 信任验证   | 自评、认证、持续监控                       | 云服务供应商合规与透明认证          |

**术语解释：**

- **No Read Up / No Write Down**：高机密对象不能被低权限主体读取 / 不能将机密信息写到低等级；
- **CDI / UDI / TP / IVP**：Clark–Wilson 模型的元素（受限数据/非受限数据/转换过程/验证过程）；
- **三元组（Subject–Program–Object）**：一种确保操作受控的结构方式；
- **ACL（访问控制列表）**：以对象为中心，记录哪些主体拥有何种权限；
- **访问矩阵**：以二维矩阵形式记录主体对对象的操作权限；
- **隐蔽通道**：未授权的信息通道，如通过资源使用时间间接传递信息；
- **非干扰（Noninterference）**：系统中某级别行为不应影响另一级别可感知的状态；

## Select Controls Based on Systems Security Requirements 

Often trusted third parties are used to perform security evaluations; the most important result from such testing is their “seal of approval” that the system meets all essential criteria.

### 1. Common Criteria（CC）

**Common Criteria（ISO/IEC 15408）** 是一套 **国际公认的 IT 产品安全评估标准**，旨在为政府和企业提供产品安全性的信心依据。

#### 目标目的（熟记！）：

- 增强客户对产品安全的信心
- 避免重复评估（国际互认）
- 降低评估成本、提高效率
- 保证评估标准一致性
- 促进安全产品的开发与评估
- 明确评估范围：包括 **功能（Functionality）与保障（Assurance）**
- 评估对象称为 **TOE（Target of Evaluation）**

The Common Criteria (CC) defines various levels of testing and confirmation of systems’ security capabilities, and the number of the level indicates what kind of testing and confirmation has been performed. Nevertheless, it’s wise to observe that even the highest CC ratings do not equate to a guarantee that such systems are completely secure or that they are entirely devoid of vulnerabilities or susceptibilities to exploit. The Common Criteria was designed as a dynamic subjective product evaluation model and replaced previous static systems: 

- U.S. Department of Defense’s **Trusted Computer System Evaluation Criteria (TCSEC)** 

- EU’s **Information Technology Security Evaluation Criteria (ITSEC).**

A document titled “Arrangement on the Recognition of Common Criteria Certificates in the Field of IT Security” was signed by representatives from government organizations in Canada, France, Germany, the United Kingdom, and the United States in 1998, making the document an international standard. Since then, 23 additional countries have signed the arrangement. The original arrangement documentation has been formally adopted as a standard and published as ISO/IEC 15408-1, -2, and -3 and primarily labeled as “Information technology — Security techniques — Evaluation criteria for IT security.”

The objectives of the **CC guidelines** are as follows:

■✓ To add to buyers’ confidence in the security of evaluated, rated IT products

■✓ To eliminate duplicate evaluations (among other things, this means that if one country, agency, or validation organization follows the CC in rating specific systems and configurations, others elsewhere need not repeat this work)

■✓ To keep making security evaluations more cost-effective and efficient

■✓ To make sure evaluations of IT products adhere to high and consistent standards

■✓ To promote evaluation and increase availability of evaluated, rated IT products

■✓ To evaluate the functionality (in other words, what the system does) and assurance (in other words, how much can you trust the system) of the **target of evaluation (TOE)**

#### CC 核心机制：PP 与 ST

| 项目                         | 说明                                  |
| ---------------------------- | ------------------------------------- |
| **PP（Protection Profile）** | 安全需求 “我希望……” → 由用户/政府制定 |
| **ST（Security Target）**    | 安全实现 “我能做到……” → 由厂商提出    |
| **Package（安全功能包）**    | 可复用的安全功能模块组合              |

🧠 **记忆方式：PP 是需求方视角，ST 是实现方承诺**

The Common Criteria process is based on two key elements: 

1. protection profiles: **Protection profiles (PPs)** specify for a product that is to be evaluated (the TOE) the security requirements and protections, which are considered the security desires, or the “I want,” from a customer. 
2. security targets: **Security targets (STs)** specify the claims of security from the vendor that are built into a TOE. STs are considered the implemented security measures, or the “I will provide,” from the vendor. 

In addition to offering security targets, vendors may offer packages of additional security features. A package is an intermediate grouping of security requirement components that can be added to or removed from a TOE (like the option packages when purchasing a new vehicle). This system of the PP and ST allows for flexibility, subjectivity, and customization of an organization’s specific security functional and assurance requirements over time.

#### Evaluation assurance levels (EALs)

An organization’s PP is compared to various STs from the selected vendor’s TOEs. The closest or best match is what the client purchases. The client initially selects a vendor based on published or marketed evaluation assurance levels (EALs) for currently available systems. Using Common Criteria to choose a vendor allows clients to request exactly what they need for security rather than having to use static fixed security levels. It also allows vendors more flexibility on what they design and create. A well-defined set of Common Criteria supports subjectivity and versatility, and it automatically adapts to changing technology and threat conditions. Furthermore, the EALs provide a method for comparing vendor systems that is more standardized (like the old TCSEC).

##### 七个 Evaluation Assurance Levels（EAL）

用于衡量一个产品达到的保障等级，**越高越严格、越昂贵，但不是越高越好！**要 **根据应用场景选合适级别**（考试常考！）

| EAL  | 名称                                         | 适用场景 / 特点概括                                          |
| ---- | -------------------------------------------- | ------------------------------------------------------------ |
| EAL1 | Functionally Tested（功能性测试）            | 仅确认基本功能能运行，无重大威胁；入门级，适合公众产品       |
| EAL2 | Structurally Tested（结构性测试）            | 商业惯例下做的结构性测试，适合低/中风险应用、遗留系统        |
| EAL3 | Methodically Tested & Checked                | 从设计开始实施安全控制，适合中等风险系统                     |
| EAL4 | Methodically Designed, Tested, Reviewed      | 常见企业级评估级别；注重工程规范和第三方功能测试             |
| EAL5 | Semi-formally Designed and Tested            | 高保障等级，使用形式化方法部分验证，适用于高价值系统         |
| EAL6 | Semi-formally Verified, Designed, and Tested | 严格全流程安全工程、测试、验证，适用于**最高敏感场景**       |
| EAL7 | Formally Verified, Designed, and Tested      | 极端高安全需求系统（如军事、航天）；**形式化验证全过程、代价极高** |

**记忆建议：**

- **EAL1–EAL3：轻量级/一般性保障**（无形式化）
- **EAL4：工程最佳实践门槛**
- **EAL5–EAL7：半形式化 → 全形式化，高保障场景**

Common Criteria Evaluation Assurance Levels (EAL)

| Level | Assurance Level                              | Description                                                  |
| ----- | -------------------------------------------- | ------------------------------------------------------------ |
| EAL1  | Functionally tested                          | Applies when some confidence in correct operation is required but where threats to security are not serious. This is of value when independent assurance that due care has been exercised in protecting personal information is necessary. |
| EAL2  | Structurally tested                          | Applies when delivery of design information and test results are in keeping with good commercial practices. This is of value when developers or users require low to moderate levels of independently assured security. It is especially relevant when evaluating legacy systems. |
| EAL3  | Methodically tested and checked              | Applies when security engineering begins at the design stage and is carried through without substantial subsequent alteration. This is of value when developers or users require a moderate level of independently assured security, including thorough investigation of TOE and its development. |
| EAL4  | Methodically designed, tested, and reviewed  | Applies when rigorous, positive security engineering and good commercial development practices are used. This does not require substantial specialist knowledge, skills, or resources. It involves independent testing of all TOE security functions. |
| EAL5  | Semi-formally designed and tested            | Uses rigorous security engineering and commercial development practices, including specialist security engineering techniques, for semi-formal testing. This applies when developers or users require a high level of independently assured security in a planned development approach, followed by rigorous development. |
| EAL6  | Semi-formally verified, designed, and tested | Uses direct, rigorous security engineering techniques at all phases of design, development, and testing to produce a premium TOE. This applies when TOEs for high-risk situations are needed, where the value of protected assets justifies additional cost. Extensive testing reduces risks of penetration, probability of covert channels, and vulnerability to attack. |
| EAL7  | Formally verified, designed, and tested      | Used only for highest-risk situations or where high-value assets are involved. This is limited to TOEs where tightly focused security functionality is subject to extensive formal analysis and testing. |

As with other evaluation criteria, the CC guidelines do not include evaluation of security in situ—that is, they do not address controls related to personnel, organizational practices and procedures, or physical security. Likewise, controls over electromagnetic emissions are not addressed, nor are the criteria for rating the strength of cryptographic algorithms explicitly laid out. Nevertheless, the CC guidelines represent some of the best techniques whereby systems may be rated for security.

CC 只评估 TOE 内部的技术安全能力，**不评估物理、人事、运维等外围保障**！

**不包括**：

- 人员/管理/流程控制
- 物理安全措施
- 电磁泄漏防护（TEMPEST）
- 密码强度评级（算法安全）

##### 实用记忆口诀（EAL 区分）

「低三软管测对错，中级设计求稳妥，高阶形式不出错」

| 级别区间  | 口诀                            | 解释                                   |
| --------- | ------------------------------- | -------------------------------------- |
| EAL1–EAL3 | 软件测试管个错（功能性/结构性） | 只是确认功能存在，风险可接受           |
| EAL4      | 方法论指导做得妥                | 工程导向最佳实践                       |
| EAL5–EAL6 | 高风险必须验证多                | 半形式化验证，高价值、高代价           |
| EAL7      | 正式验证不容错                  | 全流程形式化验证，适合最高安全需求场景 |

### 2. Authorization to Operate（ATO）

**ATO（Authorization to Operate）** 是指由权威人员批准的信息系统可以投入实际运营的**官方授权决策**，表明该系统在特定的安全控制下，其风险已被降低到可接受的水平。

它是 NIST 提出的 **Risk Management Framework (RMF)** 的核心环节。

#### 谁签发 ATO？——AO 角色

**AO（Authorizing Official）授权官员**，也叫：

- DAA：Designated Approving Authority
- AA：Approving Authority
- SCA：Security Control Assessor（通常是审查者，不是真正的决策人）
- RO：Recommending Official

👉 AO 负责 **评估系统的风险并决定是否批准运营**。

For many environments, it is necessary to obtain an official approval to use secured equipment for operational objectives. This is often referred to as an Authorization to Operate (ATO). ATO is the current term for this concept as defined by the Risk Management Framework (RMF) (see Chapter 2,“Personnel Security and Risk Management Concepts”)

An ATO is an official authorization to use a specific collection of secured IT/IS systems to perform business tasks and accept the identified risk. The assessment and assignment of an ATO is performed by an Authorizing Official (AO). An AO is an authorized entity who can evaluate an IT/IS system, its operations, and its risks, and potentially issue an ATO. Other terms for AO include designated approving authority (DAA), Approving Authority (AA), Security Control Assessor (SCA), and Recommending Official (RO).

**典型 ATO 时效及重新评估触发条件**

| 属性               | 内容                                    |
| ------------------ | --------------------------------------- |
| 默认有效期         | **5 年**（可根据实际情况缩短/延长）     |
| 需要重新评估的情况 | - ATO过期 - 重大安全漏洞 - 重大系统变更 |

🧠 记忆技巧：只要发生**时间到、漏洞出、系统变**，都可能导致 ATO 失效！

A typical ATO is issued for 5 years (although assigned time frames vary and the AO can adjust the time frame even after issuing an ATO) and must be reobtained whenever one of the following conditions occurs:

1. The ATO time frame has expired.

2. The system experiences a significant security breach.
3. The system experiences a significant security change.

The AO has the discretion to determine which breaches or security changes result in a loss of ATO. Either a modest intrusion event or the application of a substantial security patch could cause the negation of an ATO.

#### 四类授权决定（考试常考！）

| 决定类型                             | 描述与适用场景                                               |
| ------------------------------------ | ------------------------------------------------------------ |
| ✅ **Authorization to Operate (ATO)** | 表示风险已降低至可接受范围，正式授权运行；**默认目标结果**   |
| ✅ **Common Control Authorization**   | 控制来自于他人或外部共享的服务（如云平台），此控制已被同一 AO 授权，并风险可接受 |
| ✅ **Authorization to Use (ATU)**     | 使用**第三方系统**或继承他人授权的服务，通常用于云服务 / 外包系统；**体现 ATO 的互认性（reciprocity）** |
| ❌ **Denial of Authorization**        | 表示风险不可接受，**禁止上线运营**，必须整改或增强控制后重新评估 |

🧠 记忆建议：三种“授权”（ATO / CC / ATU）都表示“可以用”，唯有 “**Denial**” 直接 **禁止运行**。

An AO can issue **four types of authorization decisions**:

1. **Authorization to Operate** This decision is issued when risk is managed to an acceptable level.

2. **Common Control Authorization** This decision is issued when a security control is inherited from another provider and when the risk associated with the common control is at an acceptable level and already has a ATO from the same AO.
3. **Authorization to Use** This decision is issued when a third-party provider (such as a cloud service) provides IT/IS servers that are deemed to have risk at an acceptable level; it is also used to allow for reciprocity in accepting another AO’s ATO.
4. **Denial of Authorization** This decision is issued when risk is unacceptable.

Please see NIST SP 800-37r2 for more on the Risk Management Framework and authorization.

#### RMF 生命周期中 ATO 所在阶段（NIST SP 800-37r2）

| RMF 阶段                | ATO 所在位置            |
| ----------------------- | ----------------------- |
| Step 1: Categorize      | 分类信息系统            |
| Step 2: Select          | 选择适当的安全控制      |
| Step 3: Implement       | 实施这些安全控制        |
| Step 4: Assess          | 评估这些安全控制效果    |
| **✅ Step 5: Authorize** | **由 AO 做出 ATO 决策** |
| Step 6: Monitor         | 持续监控风险            |

**快速考点小结（表格版）**

| 考点              | 快速记忆点                           |
| ----------------- | ------------------------------------ |
| ATO 定义          | AO 批准信息系统运营，风险已可接受    |
| 签发人 AO         | 安全授权负责人，可被称为 DAA、AA、RO |
| 有效期            | 默认 5 年；过期/漏洞/变更须重新评估  |
| 四类授权结果      | ✅ATO、✅CC、✅ATU、❌Denial             |
| 常用法规来源      | NIST SP 800-37r2《RMF 指南》         |
| ATO 所在 RMF 步骤 | Step 5：Authorize                    |
| 授权后仍需        | Step 6：Monitor 持续监控             |

## Understand Security Capabilities of Information Systems

The security capabilities of information systems include memory protection, virtualization, Trusted Platform Module (TPM), encryption/decryption, interfaces, and fault tolerance. It is important to carefully assess each aspect of the infrastructure to ensure that it sufficiently supports security. Without an understanding of the security capabilities of information systems, it is impossible to evaluate them, nor is it possible to implement them properly.

### 1. Memory Protection（内存保护）

**目标**：防止一个进程访问未分配的内存区域。

- 避免：
  - 数据泄露（Confidentiality）
  - 进程间干扰（Integrity）
  - 崩溃与拒绝服务（Availability）

**实现机制**：

- 操作系统通过**内存边界检查**、**页表映射**等方式强制限制进程访问范围。

Memory protection is a core security component that must be designed and implemented into an operating system. It must be enforced regardless of the programs executing in the system. Otherwise instability, violation of integrity, denial of service, and disclosure are likely results. Memory protection is used to prevent an active process from interacting with an area of memory that was not specifically assigned or allocated to it.

#### Meltdown and Spectre

**知名攻击案例**：

- **Meltdown**：用户进程可读取**内核内存**内容。
- **Spectre**：窃取其他进程的**内存数据**。

🧠 **考点提醒**：补丁可以缓解，但会影响性能！

**Meltdown** is an exploitation that can allow for the reading of private kernel memory contents by a nonprivileged process. Spectre can enable the wholesale theft of memory contents from other running applications. An astoundingly wide range of processors are vulnerable to one or both of these exploits. Although two different issues, they were discovered nearly concurrently and made public at the same time. Patches are widely available to address these issues in existing hardware, and future processors should have native mechanisms to prevent such exploitations. But such patches often cause a reduction in performance, so application of the patch should be considered carefully.

### 2. Virtualization（虚拟化）

**核心概念**：在物理硬件上运行多个虚拟主机或操作系统（如使用 VMware、Hyper-V、KVM）。

**安全价值**：

- 沙箱环境：测试恶意软件
- OS 隔离：将风险分区
- 提高资源利用率
- 辅助灾备（DR）

**关联考点**：可结合隔离、快照恢复、高可用性（HA）策略使用。

Virtualization technology is used to host one or more operating systems within the memory of a single host computer or to run applications that are not compatible with the host OS. Virtualization can be a tool to isolate OSs, test suspicious software, or implement other security protections. See Chapter 9 for more information about virtualization.

### 3. Trusted Platform Module (TPM)

**TPM 是什么？**

- 一种**硬件安全模块（HSM）**
- 安装在主板上的安全芯片
- 用于 **密钥管理、存储、加解密**

**主要用途**：

- 驻主板硬件芯片（vs. 外接 HSM）
- 加密本地存储设备（如支持 BitLocker）
- 支持平台完整性度量（如启动检测）

**扩展知识**：

- HSM 类型：主板芯片、USB 外设、网络设备模块
- **具备防篡改机制**

🧠 TPM 和 HSM 是常见选择题中需要区分的两个重点！

The Trusted Platform Module (TPM) is both a specification for a cryptoprocessor chip on a mainboard and the general name for implementation of the specification. A TPM can be used to implement a broad range of cryptography-based security protection mechanisms.

A TPM chip is often used to store and process cryptographic keys for a hardware-supported or OS-implemented local storage device encryption system. A TPM is an example of a hardware security module (HSM). An HSM is a cryptoprocessor used to manage and store digital encryption keys, accelerate crypto operations, support faster digital signatures, and improve authentication. An HSM can be a chip on a motherboard, an external peripheral, a network-attached device, or an extension card (which is inserted into a device, such as a router, firewall, or rack-mounted server blade). HSMs include tamper protection to prevent their misuse even if an attacker gains physical access.

### 4. Interfaces（受限接口）

**定义**：根据用户权限控制功能可见性与可操作性。

**实现方式**：

- 权限低的用户无法看到按钮/菜单
- 或者命令呈灰色禁用状态

**目的**：

- 限制未经授权用户的功能访问
- 限制误操作的可能性
- 落实**最小权限原则**

📌 **模型关联**：与 **Clark–Wilson 模型**直接相关（通过“受限接口 + 转换程序”实现访问控制）。

A constrained or restricted interface is implemented within an application to restrict what users can do or see based on their privileges. Users with full privileges have access to all the capabilities of the application. Users with restricted privileges have limited access.

Applications constrain the interface using different methods. A common method is to hide the capability if the user doesn’t have permissions to use it. Commands might be available to administrators via a menu or by right-clicking an item, but if a regular user doesn’t have permissions, the command does not appear. Other times, the command is shown but is dimmed or disabled. The regular user can see it but will not be able to use it.

The purpose of a constrained interface is to limit or restrict the actions of both authorized and unauthorized users. The use of such an interface is a practical implementation of the Clark–Wilson model of security.

### 5. Fault Tolerance （容错）

**定义**：系统在发生局部故障时仍可继续运行。

**实现方式**：

- RAID：磁盘冗余
- 集群：主备自动切换
- 热备：设备实时镜像同步

**关联安全属性**：

- 可用性（Availability）
- 消除单点故障（Single Point Of Failure）

Fault tolerance is the ability of a system to suffer a fault but continue to operate. Fault tolerance is achieved by adding redundant components such as additional disks within a redundant array of inexpensive disks (RAID) array, or additional servers within a failover clustered configuration. Fault tolerance is an essential element of security design. It is also considered part of avoiding single points of failure and the implementation of redundancy. For more details on fault tolerance, redundant servers, RAID, and failover solutions, see Chapter 18, “Disaster Recovery Planning.”

### 6. Encryption/Decryption（加解密）

**功能**：

- 加密（Encryption）：将明文变为密文（机密性）
- 解密（Decryption）：还原密文（可用性）

**支持安全目标**：

- 机密性（Confidentiality）
- 完整性（Integrity）【结合哈希使用】
- 身份验证 + 不可否认性（必须是非对称加密）

Encryption is the process of converting plaintext to ciphertext, whereas decryption reverses that process. Symmetric and asymmetric methods of encryption and decryption can be used to support a wide range of security solutions to protect confidentiality and integrity. Please see the full coverage of cryptography in Chapters 6 and 7.

#### Security Capabilities of Information Systems 快速回忆表

| 能力模块              | 目标                 | 实现技术/机制              | 关联安全模型 / 考点              |
| --------------------- | -------------------- | -------------------------- | -------------------------------- |
| Memory Protection     | 防止非法访问内存     | 虚拟地址空间、边界检查     | 防泄露、防崩溃，Meltdown/Spectre |
| Virtualization        | 隔离风险，提高利用率 | Hypervisor、虚拟机         | 沙箱、备份、灾难恢复             |
| TPM / HSM             | 密钥保护、硬件加解密 | 芯片存储密钥、硬件加速模块 | 支持磁盘加密、防物理入侵         |
| Constrained Interface | 限制权限功能         | 隐藏/禁用控件、菜单        | Clark–Wilson 模型                |
| Fault Tolerance       | 保证服务不中断       | RAID、Cluster、热备        | Availability、防SPOF             |
| Encryption            | 保密性、完整性       | 对称/非对称加密，数字签名  | 详见第6–7章                      |

## Summary

Secure systems are not just assembled; they are designed to support security. Systems that must be secure are judged for their ability to support and enforce the security policy. Programmers should strive to build security into every application they develop, with greater levels of security provided to critical applications and those that process sensitive information.

There are numerous issues related to the establishment and integration of security into a product, including managing subjects and objects and their relationships, using open or closed systems, managing secure defaults, designing a system to fail securely, abiding by the “keep it simple” postulate, implementing zero trust (instead of trust but verify), and incorporating privacy by design. CIA can be protected using confinement, bounds, and isolation. Controls are used to implement security protections.

Proper security concepts, controls, and mechanisms must be integrated before and during the design and architectural period in order to produce a reliably secure product. A trusted system is one in which all protection mechanisms work together to process sensitive data for many types of users while maintaining a stable and secure computing environment. In other words, trust is the presence of a security mechanism or capability. Assurance is the degree of confidence in satisfaction of security needs. In other words, assurance is how reliable the security mechanisms are at providing security.

When security systems are designed, it is often helpful to derive security mechanisms from standard security models. Some of the security models that should be recognized include the trusted computing base, state machine model, information flow model, noninterference model, take-grant model, access control matrix, Bell–LaPadula model, Biba model, Clark–Wilson model, Brewer and Nash model, Goguen–Meseguer model, Sutherland model, Graham–Denning model, and Harrison–Ruzzo–Ullman model.

Several security criteria exist for evaluating computer security systems. The Common Criteria uses a subjective system to meet security needs and a standard Evaluation Assurance Level **(EAL) to evaluate reliability.**

The NIST Risk Management Framework (RMF) establishes an Authorization to Operate (ATO) issued by an Authorizing Official (AO) in order to ensure that only systems with acceptable risk levels are used to perform IT operations.

It is important to carefully assess each aspect of the infrastructure to ensure that it sufficiently supports security. Without an understanding of the security capabilities of information systems, it is impossible to evaluate them, nor is it possible to implement them properly. The security capabilities of information systems include **memory protection, virtualization, Trusted Platform Module (TPM), encryption/decryption, interfaces, and fault tolerance.**

## Exam Essentials

- **Be able to define object and subject in terms of access.** The subject is the user or process that makes a request to access a resource. The object is the resource a user or process wants to access.
- **Be able to describe open and closed systems.** Open systems are designed using industry standards and are usually easy to integrate with other open systems. Closed systems are generally proprietary hardware and/or software. Their specifications are not normally published, and they are usually harder to integrate with other systems.
- **Understand open and closed source.** An open source solution is one where the source code, and other internal logic, is exposed to the public. A closed source solution is one where the source code and other internal logic is hidden from the public.
- **Know about secure defaults.** Never assume the default settings of any product are secure. It is always up to the system’s administrator and/or company security staff to alter a product’s settings to comply with the organization’s security policies.
- **Understand the concept of fail securely.** Failure management includes programmatic error handling (aka exception handling) and input sanitization; secure failure is integrated into the system (fail-safe vs. fail-secure).
- **Know about the principle of “keep it simple.”** “Keep it simple” is the encouragement to avoid overcomplicating the environment, organization, or product design. The more complex a system, the more difficult it is to secure.
- **Understand zero trust.** Zero trust is a security concept where nothing inside the organization is automatically trusted. Each request for activity or access is assumed to be from an unknown and untrusted location until otherwise verified. The concept is “never trust, always verify.” The zero trust model is based around “assume breach” and microsegmentation.
- **Know about Privacy by Design**. Privacy by Design (PbD) is a guideline to integrate privacy protections into products during the early design phase rather than attempting to tack them on at the end of development. The PbD framework is based on seven foundational principles.
- **Understand “trust but verify.”** “Trust but verify” is a traditional security approach of trusting subjects and devices within the company’s security perimeter automatically. This type of security approach leaves an organization vulnerable to insider attacks and grants intruders the ability to easily perform lateral movement among internal systems.
- **Know what confinement, bounds, and isolation are.** Confinement restricts a process to reading from and writing to certain memory locations. Bounds are the limits of memory a process cannot exceed when reading or writing. Isolation is the mode a process runs in when it is confined through the use of memory bounds.
- **Know how security controls work and what they do.** Security controls use access rules to limit the access by a subject to an object.
- **Understand trust and assurance.** A trusted system is one in which all protection mechanisms work together to process sensitive data for many types of users while maintaining a stable and secure computing environment. In other words, trust is the presence of a security mechanism or capability. Assurance is the degree of confidence in satisfaction of security needs. In other words, assurance is how reliable the security mechanisms are at providing security.
- **Define a trusted computing base (TCB).** A TCB is the combination of hardware, software, and controls that form a trusted base that enforces the security policy.
- **Be able to explain what a security perimeter is.** A security perimeter is the imaginary boundary that separates the TCB from the rest of the system. TCB components communicate with non-TCB components using trusted paths.
- **Know what the reference monitor and the security kernel are.** The reference monitor is the logical part of the TCB that confirms whether a subject has the right to use a resource prior to granting access. The security kernel is the collection of the TCB components that implement the functionality of the reference monitor.
- **Know details about each of the security models.** Know the security models and their functions:
  - **The state machine model** ensures that all instances of subjects accessing objects are secure.
  - **The information flow model** is designed to prevent unauthorized, insecure, or restricted information flow.
  - **The noninterference model** prevents the actions of one subject from affecting the system state or actions of another subject.
  - **The take-grant model** dictates how rights can be passed from one subject to another or from a subject to an object.
  - **An access control matrix** is a table of subjects and objects that indicates the actions or functions that each subject can perform on each object.
  - **Bell–LaPadula** subjects have a clearance level that allows them to access only those objects with the corresponding classification levels, which protects confidentiality.
  - **Biba** prevents subjects with lower security levels from writing to objects at higher security levels.
  - **Clark–Wilson** is an integrity model that relies on the access control triplet (i.e., subject/program/object).
  - **Goguen–Meseguer** and **Sutherland** models focus on integrity.
  - **Graham–Denning** focuses on the secure creation and deletion of both subjects and objects.
  - **The Harrison–Ruzzo–Ullman (HRU) model** focuses on the assignment of object access rights to subjects as well as the integrity (or resilience) of those assigned rights.
  - **The Common Criteria** (ISO/IEC 15408) is a subjective security function evaluation tool that uses protection profiles (PPs) and security targets (STs) and assigns an Evaluation Assurance Level (EAL).
  - **Authorization to Operate (ATO)** (from the RMF) is a formal approval to operate IT/IS based on an acceptable risk level based on the implementation of an agreed-on set of security and privacy controls.

**Understand the security capabilities of information systems.** Common security capabilities include memory protection, virtualization, Trusted Platform Module (TPM), encryption/ decryption, interfaces, and fault tolerance.

