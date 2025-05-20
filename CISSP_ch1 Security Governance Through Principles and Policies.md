## Chapter 1 Security Governance Through Principles and Policies

**Domain 1 Security and Risk Management**

Security is the business management tool that ensures the reliable and protected operation of IT/IS. Security exists to support the objectives, mission, and goals of the organization.

3 common types of security evaluation: risk assessment, vulnerability assessment and penetration testing.

- **Risk assessment**: a process of identifying assets, threats, and vulnerabilities, and then using that information to calculate risk. Once risk is understood, it is used to guide the improvement of the existing security infrastructure.

- **Vulnerability assessment**: uses automated tools to locate known security weaknesses, which can be addressed by adding in more defenses or adjusting the existing protections.

- **Penetration testing** uses trusted individuals to stress-test the security infrastructure to find issues that may not be discovered by the prior 2 means, with the goal of finding those concerns before an adversary takes advantage of them.

Security should be cost-effective. Select security controls that provide the greatest protection for the lowest resource cost.

#### Understand and Apply Security Concepts

Confidentiality, integrity and availability (CIA) are the primary goals and obj of a security infrastructure.

Security controls are typicaly evaluated on how well they address these 3 core information security tenets. Vulnerabilities and risks are also evaluated based on the threat they pose against one or more of the CIA triad principles.

1. **Confidentiality**

Confidentiality is the concept of the measures used to ensure the protection of the secrecy of data, objects, or resources. The goal of confidentiality protection is to prevent or minimize unauthorized  access to data. Confidentiality protections prevent disclosure  while protecting authorized access.

- sensitivity: quality of information, could cause harm or damage if disclosed
- discretion: 自由裁量权, is an act of decision where an operator can influence or control disclosure(信息披露) in order to minimize the harm or damage
- Criticality: the level to which information is mission critical is its measure of criticality. The higher level of criticality , the more likely the need to maintain the confidentiality of the information.
- Concealment(隐藏): is the act of hiding or preventing disclosure. Often concealment is viewed as a mean of cover, obfuscation, or distraction. A realated concept to concealment is security through obscurity.
- Secrecy: the act of keeping sth a secret or preventing the disclosure of information.
- Privacy: keeping informatin confidential that is personally identifiable or that might cause harm, embarrassment, or disgrace to sb if revealed.
- seclusion: involves storing somthing in an out-of-the-way location, likely with strict access controls.
- isolation: the act of keeping sth separated from others.

2. **Integrity**

protecting the reliablity and correctness of data. Integrity protection prevents unauthorized alterations of data. Properly implemented integrity protection provides a means for authorized changes while protecting against intended and malicious unauthorized activities(such as viruses and intrusions) as well as mistakes made by authorized users(such as accidents or oversights)

Integrity can be examined from 3 perspectives:

- preventing unauthorized subjects from making modifications
- Prevent authorized subjects from making unauthorized  modifications, such as mistakes
- maintaining the internal and external consistency of objects os taht their data is a correct and true reflection of the real world and any relationship with any other object is valid, consistency, and verfifiable.

For integrity to be maintained on a system, controls must be in place to restrict access to data, objects and resources. Maintaining and validating object integrity across storage, transport, and processing requires numerous variations of controls and oversight.

Attacks focus on the violation of integrity including viruses, logic bombs, unauthorized access, errors in coding and applications, malicious modification, intentional replacement, and sys backdoors.

Human error, oversight, or ineptitude accounts for many instances of unauthorized alteration of sensitive information. They can also occur because of an oversight in a security policy or a misconfigured security control.

Numerous countermeasures(对策) can ensure integrity against possible threats. include: strict access control, rigorous authentication procedures, intrusion detection system, object/data encryption, hash verification, interface restrictions, input/function checks, and extensive personnel training.

Confidentiality and integrity depend on each other. Without obejct integrity, confidentiality cannot be maintained.

Integrity is dependent on confidentiality and access control. 

- Accuracy: being correct and precise
- Truthfulness: being a true reflection of reality
- Validity: being factually or logically sound
- Accountability: being responsible or obligated for actions and results
- Responsibility: being in charge or having control over sth or someone
- Completeness: having all necessary components or parts
- Comprehensiveness: being complete in scope; full inclusion of all needed elements

#### Availability

authorized subjects are granted timely and uninterrupted  access to objects. Availability protection controls support sufficient bandwidth and timeliness of processing as deemed necessary by the org or situation. Availability includes: efficient uninterrupted  access to objects and prevention of denial of service attacks. Availability also implies that the supporting infra-including network services, communications, and access control mechanisms is functional and allows authorized users to gain authorized access. 

Ensure authorized access and an acceptable level of performance, to quickly handle interruptions, provide for redundancy, maintain reliable backups, and prevent data loss or destruction.

Threats to availability: 

device failure, software errors, environmental issues(heat, static electricity, flooding, power loss)

some attach focus on the violation of availability, including DOS attacks, object destruction and communication interruptions.

Many availability breaches(违反) are caused by human error(人为错误), oversight(疏忽), or ineptitude(无能/能力不足). They can also occur because of an oversight in a security policy or a misconfigured security control.

Numerous countermeasures(对策) can ensure availability against possible threats. Include:

Design intermediary delivery systems properly, use access control effectively, monitor performance  and network traffic, use firewalls and routers to prevent DOS attacks, implementing redundancy for critical systems, and maintaining  and testing backup systems.

Most security policies, as well as business continuity planning(BCP) focus on the use of fault tolerance features at the various levels of access/storage/security with the goal of eliminating single point of failure  to maintain availablity of critical systems.

Availability depends on both integrity and confidentiality. 

- Usability: the state of being easy to use or learn or being able to be understood and controlled by a subject
- Accessibility: the assurance that the widest range of subjects can interact with a resource regardless of their capabilities or limitations 
- Timeliness: being prompt, on time within a reasonable time frame, or providing low latency response.

#### DAD, Overprotection, Authenticity, Non-repudiation, and AAA Services

in addtion to the CIA triad, you need to consider a plethora of other security-related concepts and principles when designing a security policy and deploying a security solution. 

Include:

- DAD Triad, 
- the risks of overprotection, 
- authenticity, 
- nonrepudiation,
- AAA services.

DAD Triad: Disclosure, alteration and destruction. It represents the failures of security protection in the CIA Triad. It may be useful to recoginize what to look for when a security mechanism fails. 

- Disclosure occurs when sensitive or confidential material is accessed by unauthorized  entities, it is a violation of confidentiality. 
- Alteration occurs when data is either maliciously or accidentally changed, it is a violation of integrity.
- Destruction occurs when a resource is damaged or made inaccessible  to authroized users. It is a violationof availability.

Overprotection  confidentiality can result in a restriction of availability. Overprotection integrity can result in a restriction of availability. Overprotection  availability can result in a loss of confidentiality and integrity.

**Authenticity** is the security concept that data is authentic or genuine and originates from its alleged source. This is related to integrity, but its more closely related to verifying that it is from a claimed origin. When data has authenticity, the recipient can have a high level of confidence that the data is from whom it claims to be from and that it did not change in transit(or storage).

**Non-repudiation** ensures that the subject of an activity or who caused an event can not deny that the event occured. Nonrepudiation prevents a subject from claiming not to have sent a message, not to have performed an action, or not to have benn the cause of an event. It is made possible  through identification, authentication, authorization, accountability, and auditing. nonrepudiation can be established using digital certificats, session identifiers, transaction logs, and numerous other transactional and access control mechanisms.

A sys built without proper enforcement of non-repudiation dose not provide verification that a specific entity performed a certain action. Nonrepudiation is essential part of accountability. A suspect can not be held accountable if they can repudiate the claim against them.

**AAA Services** is a core security mechanism of all security environment. 

- Authentication
- Authorization
- Accounting(Auditing)

These 5 elements represent the following processes of security:

![image-20250504144143335](/Users/TODO/Library/Application Support/typora-user-images/image-20250504144143335.png)

- **Identification**: is claiming to be an identity when attempting to access a secured area or system.
- **Authentication**: is providing that you are that claimed identity.
- **Authorization**: is defining that the permissions of a resource and object access for a specific identity or subject.
- **Auditing**: is recording a log of the events and activities related to the sys and subjects.
- **Accounting**: aka accountability. is reviewing log files to chekc for compliance and violations in order to hold subjects accountable for their actions, especially violations of organizational security policy.

Missing any of these 5 elements can result in an incomplete security mechanism. 

| 元素           | 定义                                                         |
| -------------- | ------------------------------------------------------------ |
| **Auditing**   | **记录**事件、活动、访问等信息（日志记录过程）               |
| **Accounting** | **审核、分析日志记录**，检查是否符合政策、是否有违规，进而追责 |

👉 **Auditing = 记录过程**
👉 **Accounting = 分析和追责过程**

它们是一个“前后顺序”的关系：✅ **先 Auditing → 再 Accounting**

在安全领域，accounting强调的是：**基于已记录的日志，去检查合规性、识别违规、追责（Accountability）**， 而 **Auditing** 仅指“把事件写进日志”，并不涉及“去分析、去检查”。

**Auditing = logging**, **Accounting = accountability（审查日志、确认违规、追责）**

### **Identification**

a subject must perform identifacation to start the process of authentication, authroization, and accoutability. Prividing an identity can involve typing a username, swiping a finger for a camera or scanning device. speaking a phrase, or positioning your face, hand, or finger for a camera or scanning device. Without an identity, a system has no way to correlate an authentication factor with the subject.

Once a subject has been identified, the identity is accoutable for any further actions by that subject. IT systems track activity by identities, not by the subjects themselves. A computer doesn;t know one individual from another, but it does know that your user account is different from all other user accounts. Simply claiming an identity does not imply access or authority. The identity must be proven before use. That process is authentication.

### Authentication

 The process of verifying wherther a claimed identity is valid is authentication. Authentication requires the subject to provide additional information that corresponds to  the identity they are claiming. The most. common form of authentication is using a password. Authentication verifies the identity of the subject by compaing one or more factors against the database of valid identities. The capability of the subject and system to maintain the secrecy of the authentication factors for identities directly reflects the level of security of that system.

Identification and authentication are often used together as a single 2-step process.
Providing an identity is the first step, and providing the authentication factors is the second step. Without both, a subject can not gain the access to a system- neither element alone is useful in terms of security. In some systems, it may semm as if you are providing only one element but gain access, such as when keying in an ID code or a PIN. However, in these cases either the identification is handled by another means, such as physical locations, or authentication is assumed by your ability to access the system physically. Both identification and authentication take place, but you might not be as aware of them as when you manually type in both a name and a password.

Each authentication technique or factor has its unique benefits and drawbacks. Thus, it is important to evaluate each mechanism in light of the environment in which it will be deployed to determine viability. 

### Authorization

Once subject is authenticated, access must be be authorized. The process of authorization ensures that the requested activity or acces to an object is possible given the rights and privileges assigned to the authenticated identity. In most cases, the system evaluates the subject, the object, and assigned permissions related to the intended activity. If the specific action is allowed, the subject is authorized. If the specific action is not allowed, the subject is not authroized.

Identification and authentication are all-or-nothing aspects of access control. Authroization has a vide rage of variation between all or nothing for each object within the environment. A user may be able to read a file but not delete it, print a document but not alter the print queue, or log on to a system but not access any resources. 

### Auditing

Auditing is the programmatic means by which a subject's actions are tracked and recorded for the purpose of holding the subject accountable  for their actions while authenticated on a system through the documentation or recording of subject activity. It is also the process by which unauthorized or abnormal activities are detected on a sys. Auditing is recording activities of a subject and its objects as well as recording the activities of application and sys functions. Log files provide an audit trail for recreating the hsitory of an event, intrusion, or sys failure.

Auditing is needed to detect malicious actions by subjects, attempted intrusions, and system failures and to reconstruct events, provide evidence for prosecution(起诉), and produce problem reports and analysis. Auditing is usually a native feature of operating sys and most applications and services. Thus, configuring the system to record information about specific types of events is fairly straightforward.

### Accountability

An org's security policy can be properly enforced only if accountability is maintained. you can maintain security only if subjects are held accountable for their actions. Effective accountability relies on the capability to prove a subject's identity and track their activities. Accoutability is established  by linking an individual to the activities of an online identity through the security services and mechanisms  of auditing, authorization, authentication, and identification. Thus, individual accountability is ultimately dependent on the strengh of these processes.

Without a strong authentication process, there is doubt that the person assiciated with a specific user account was the actual entity controlling that user account when the undersided action took place.

To have viable accoutability, you mush be able to support your security decisions and their implementation in a court of law. If you are unable to legally support your security efforts, then you will be unlikely to be able to hold an indivitual accountablefor actions linked to a user account. With only a password as authentication, there is significant room for doubt. Pwd are the least secure form of authentication, with dozens of different methods avaible to compromise them. With multi factor authentication, such as a password, smartcard, and fingerprint scan in combination, there is very little possibllity that any other individual could have **compromised**(被攻破、被入侵、被破解、被泄露; 强调某个系统、账号、数据、认证流程，遭到了未经授权的访问或控制) the authentication process in order to **impersonate**(冒充某人、伪装成另一个人、冒名顶替) the person responsible for the user account.

### Protection Mechanisms

1. **Defense in Depth(Layering)**

the use of multiple controls in a series. No one control can protect against all possible threats. Using a multilayered solution allows for numerous different controls to guard against whatever come to pass. When security solutions are designed in layers, a single failed control should not result in exposure of systems or data.

Using layers in a series rather than in parallel is important. Performing security restrictions in a series means to perform one after the other in a linear fashion. Only through a series configuration will each attack be scanned, evaluated, or mitigated by every security control. 

2. **Abstraction**

Abstraction is used for efficiency. Similar elements are put into groups, classes, or roles that are assigned security controls, restrictions, or permissions as a collective. Abstraction simplifies security by enabling you to assign security controls to a group of objects collected by type or function. Thus, the concept of abstraction is used when classifying objects or assigning roles to subject.

Another way in which abstraction applies to security is the introduction of object groups, sometimes called classes, where access controls and operation rights are assigned to groups of objects rather than on a per-object basis. 

3. **Data hiding**

Data hiding is exactly what it sounds like: preventing data from being discovered or accessed by a subject by positioning the data in a logical storage compartment  that is not accessible or seen by the subject. Forms of data hiding include keeping a database fom being accessed by unauthorized visitors and restricting a subject at a lower classification level from accessing data at a higher level classification level. **Steganography**(隐写术) is an example of data hiding.

Data hiding is am important charateristic in multilevel secure systems. It ensures that data existing at one level of security is not visible to processes running at different security levels. From a security perspective, data hiding relies on placing objects in security containers that are different from those that subjects occupy to hide object details from those with no need to know about them or means to access them.

Note: In **security through obscurity** the subject could access the data if they find it. It is digital hide and seek. Security through obscurity does not actually implement any form of protection. It is instead an attempt to hope something important is not discovered by keeping knowledge of it a secret. An example of security though obscurity is when a programmer is aware of a flaw in their software code, but they release the product anyway hoping that no one discovers the issue and exploits it.

4. **Encryption**

Encryption is the science of hiding the meaning or intent of a communication from unintended recipients. Encryption can take many forms and should be applied to every type of electronic communication and storage. 

### Security boundaries

Security boundary is the line of intersection between any 2 areas, subnets, or environment  that have different security requirements or needs. A security boundaries exists between a hig-security area and a low-security one, such as between a LAN and the internet. it is important to recognize the security boundary  both on your network and in the physical world. Once you identify a security boundary, you must deploy mechanisms to control the flow of information across that boundary.

👉 **physical environment = 实体世界（建筑、机房、设备）
👉 logical environment = 数字世界（网络、系统、数据）**

environment and security boundary separately. Simply deduce what available security mechanisms would provide the most reasonable, cost-effective, and efficient solution for a specific environment and situation. However, all security mechanisms must be weighed against the value of the objects they are to protect. Deploying countermeasures that cost more than the value of the protected objects is unwarranted.

### Evaluate and Apply Security Governance Principles 

Security governance is the collection of practices related to supporting, evaluating, defining and directing the security efforts  of an org. Security governance seeks to compare the security processes and infrastructure used within the organization with knowledge and insight obtained from external sources.

Security governance principles are often closely related to and often intertwined with corporate and IT governance. The goals of these three governance agendas are often the same or interrelated, such as maintaining business processes while striving toward growth and resiliency.

Some aspects of governance are imposed on organizations due to legislative and regulatory compliance needs, whereas others are imposed by industry guidelines or license requirements. 

All forms of governance, including security governance, must be assessed and verified from time to time.

Various requirements for auditing and validation may be present due to government regulations or industry best practices. This is especially problematic when laws in different countries differ or in fact conflict. The organization as a whole should be given the direction, guidance, and tools to provide sufficient oversight and management to address threats and risks, with a focus on eliminating downtime and keeping potential loss or damage to a minimum.

Security is a business operations issue. Security is an organizational process, not just something the IT geeks do behind the scenes. Using the term security governance is an attempt to emphasize this point by indicating that security needs to be managed and governed throughout the organization, not just in the IT department.

There are numerous security frameworks and governance guidelines, including National Institute of Standards and Technology (NIST) SP 800-53 and NIST SP 800-100. Although  the NIST guidance is focused on government and military use, it can be adopted and adapted by other types of organization as well.

### Third-Party Governance

Third-party governance is the system of external entity oversight that may be mandated by law, regulation, industry standards, contractual obligation, or licensing requirements. The actual method of governance may vary, but it generally involves an outside investigator or auditor. These auditors might be designated by a governing body or might be consultants hired by the target organization.

In the auditing and assessment process, both the target and the governing body should participate in full and open document exchange and review. An organization needs to know the full details of all requirements it must comply with. The organization should submit security policy and self-assessment reports back to the governing body. This open document exchange ensures that all parties involved are in agreement about all the issues of concern. It reduces the chances of unknown requirements or unrealistic expectations. Document exchange does not end with the transmission of paperwork or electronic files. Instead, it leads into the process of documentation review.

### Documentation Review

Documentation review is the process of reading the exchanged materials and verifying them **against** standards and expectations.

- **check results against requirements** → **根据需求检查结果**
- **validate code against specifications** → **根据规范验证代码**
- **measure performance against benchmarks** → **以基准衡量性能**

👉 都是“用…做参照物”的意思。

In many situations, especially related to government or military agencies or contractors, failing to provide sufficient documentation to meet requirements of third-party governance can result in a loss of or a voiding of authorization to operate (ATO). Complete and sufficient documentation can often maintain existing ATO or provide a temporary ATO (TATO). However, once an ATO is lost or revoked, a complete documentation review and on-site review showing full compliance is usually necessary to reestablish the ATO.

### Manage the Security Function

The security function is the aspect of operating a business that focus on the task of evaluating and improving security over time.  To manage the security function, an org must implement proper and sufficient security governance.

The act of performing a risk assessment to drive the security policy is the clearest and most direct example of management of the security function. 

Security must be measurable. Measurable security means that the various aspects of the security mechanisms function, provide a clear benefit, and have one or more metrics that can be recorded and analyzed. Similar to performance metrics, security metrics are measurements of performance, function, operation, action and so on as related to the operation of a security feature.

The act of measuring and evaluating security metrics is the practice of assessing the completeness and effectiveness of the security program. This should also include measuring it against common security guidelines and tracking the success of its controls. Tracking and assessing security metrics is part of effective security governance.

Managing the security function includes the development and implementation of information security strategies. Most of the content of the CISSP exam, and hence this book, addresses the various aspects of development and implementation of information security strategies.

### Alignment of Security Function to Business Strategy, Goals, Mission, and Objectives

Security management planning ensures proper creation, implementation, and enforcement of a security policy.

Security management planning aligns the security functions to the strategy, goals, mission, and objectives of the organization. This includes designing and implementing security based on business cases, budget restrictions, or scarcity of resources. A business case is usually a documented argument or stated position in order to define a need to make a decision or take some form of action.

One of the most effective ways to tackle security management planning is to use a **top-down approach**. Upper, or senior, management is responsible for initiating and defining policies for the organization. Security policies provide direction for all levels of the organization’s hierarchy. It is the responsibility of middle management to flesh out the security policy into standards, baselines, guidelines, and procedures. The operational managers or security professionals must then implement the configurations prescribed in the security management documentation. Finally, the end users must comply with all the security policies of the organization.

**Note:** The opposite of the top-down approach is the **bottom-up approach**. In a bottom-up approach environment, the IT staff makes security decisions directly without input from senior management. The bottom-up approach is rarely used in organizations and is considered problematic in the IT industry.

Note: The chief information officer (CIO) focuses on ensuring information is used effectively to accomplish business objectives. The chief technical officer (CTO) focuses on ensuring that equipment and software work properly to support the business functions.

Elements of security management planning include defining security roles; prescribing how security will be managed, who will be responsible for security, and how security will be tested for effectiveness; developing security policies; performing risk analysis; and requiring security education for employees. These efforts are guided through the development of management plans.

The best security plan is useless without one key factor: approval by senior management. Without senior management’s approval of and commitment to the security policy, the policy will not succeed.

![image-20250504221452854](/Users/TODO/Library/Application Support/typora-user-images/image-20250504221452854.png)



**Strategic Plan**: Long-term goals and visions for the future are discussed in a strategic plan. A strategic plan should include a risk assessment.

**Tactical Plan**: a midterm plan developed to provide more details on accomplishing the goals set forth in the strategic plan, or can be crafted ad hoc based on unpredicted events. A tactical plan is typically useful for about a year and often prescribes and schedules the tasks necessary to accomplish organizational goals. Some examples of tactical plans are project plans, acquisition plans, hiring plans, budget plans, maintenance plans, support plans, and system development plans.

**Operational Plan:** a short-term, highly detailed plan based on the strategic and tactical plans. It is valid or useful only for a short time. Operational plans must be updated often (such as monthly or quarterly) to retain compliance with tactical plans. Operational plans spell out how to accomplish the various goals of the organization. They include resource allotments, budgetary requirements, staffing assignments, scheduling, and step-by-step or implementation procedures. Operational plans include details on how the implementation processes are in compliance with the organization’s security policy. Examples of operational plans are training plans, system deployment plans, and product design plans.

Security is a continuous process. Thus the activitity of security management planning may have a definitive initiation point. But its tasks and work are never fully accompulished or complete. Effective security plans focus attention on specific and achievable objectives, anticipate change and potential problems, and serve as a basis for decision making for the entire organization. Security documentation should be concrete, well-defined, and clearly stated. For a security plan to be effective, it must be developed, maintained, and actually used.

### Organizational Processes (**组织流程**)

Security governance should address every aspect of an org, including the organizational processes of acquisitions, diverstitures, and governance committees. M&A place an org at an increased level of risk. Such risks include inappropriate information disclosure, data loss, downtime, or failure to achieve sufficient return on investment.

In addition to all the typical business and financial aspects of mergers and aquisitions, a healthy dose of security oversight, and increased **scrutiny**(审查) is often essential to reduce the likelihood of losses during such a period of transformation.

Similarly, a **divestiture**(资产剥离) or any form of asset or **employee reduction**(裁员) is another time period of increased risk and thus increased need for focused security governance. Assets need to be **sanitized**(数据擦除/净化/清理) to prevent data leakage. **Storage media**(存储介质) should be removed and destroyed, because media sanitization techniques do not guarantee against data remnant recovery. Employees released from duty need to be **debriefed**(离职面谈 / 离职安全交接). The process is often called an **exit interview**. The process usually involves reviewing any **nondisclosure agreements**(**NDAs**) (保密协议) as well as any other binding contracts or agreements that will continue after employment has ceased.

👉 **divestiture = 出售公司部分资产/业务/子公司（资产剥离）**

🧠 **CISSP 考试提示：**

- 考“data remanence”（数据残留） → 要求“物理销毁”
- 考“exit interview” → 包含“资产回收、权限关闭、保密协议确认”
- 考“divestiture” → 资产转移时数据要“sanitization”

Thus, when considering the cost of a merger/acquisition, it is important to consider the total cost of ownership over the life of the product’s deployment rather than just initial purchase and implementation.

When engaging third-party assessment and monitoring services, keep in mind that the external entity needs to show security-mindedness in their business operations. If an external organization is unable to manage their own internal operations on a secure basis, how can they provide reliable security management functions for yours?

When evaluating a third party for your security integration, consider the following processes:

- **On-Site Assessment**: visit the site of the org to interview personnel and observe their operating habits.
- **Document Exchange and Review**: investigate the means by which datasets and documentation are exchanged as well as the formal processes by whci hthey perform assessments and reviews.
- **Process/Policy Review**: Request copies of their security policies, processes/procedures, and documentation of incidents and responses for review.
- **Third-Party Audit**: have an independent  3rd-party auditor, as defined by the American institute of Certified public accountants(AICPA), can provide an unbiased review of an entity's security infrastructure, based on Service Organization Control(SOC) reports.

### Organizational Roles and Responsibilities 

The following are the common security roles present in a typical secured environment:

**Senior Manager**: The senior manager must sign off on all security policy issues. There is no effective security policy if the senior management does not authorize and support it. The senior manager is the person who will be held liable for the overall success or failure of a security solution and is responsible for exercising due diligence and due care in establishing security for an organization. Even though senior managers are ultimately responsible for security, they rarely implement security solutions. In most cases, that responsibility is delegated to security professionals within the organization.

**Security Professional**: The security professional has the functional responsibility for security, including writing the security policy and implementing it. The role of security professional may be labeled as an IS/IT role, but its focus is on protection more than function.

The security professional role is often filled by a team that is responsible for designing and implementing security solutions based on the approved security policy. Security professionals are not decision makers; they are implementers. All decisions must be left to the senior manager.

**Asset Owner**: The role is assigned to the person who is responsible for classifying information for placement and protection within the security solution. The asset owner is typically  a high-level manager who is ultimately responsible for asset protection. However, the asset owner usually delegates the responsibility of the actual data management tasks to a custodian.

**Custodian:** responsible for the tasks of implementing the prescribed protection defined by the security policy and senior managemtn. The custodian performs all activities necessary to provede adequate protection for the CIA triad of data and to fulfill the requirements and responsibilities delegated from upper management. Activities include:

- Performing and testing backups,
- Validating data integrity
- Deploying security solutions
- Managing data storage based on classification.

| 项目                       | Security Professional                                        | Custodian（保管人）                        |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------ |
| **职责重点**               | 设计与实施安全策略和控制机制                                 | 执行具体的数据保护与操作任务               |
| **关注点**                 | 安全整体架构与策略实施，偏“规划与执行”                       | 数据日常管理与技术运维，偏“操作与维护”     |
| **权限**                   | 无决策权，仅根据管理层批准方案执行                           | 同样无决策权，执行被分配的数据保护任务     |
| **主要任务**               | 编写安全策略、部署防火墙、设计访问控制方案、制定加密机制     | 做备份、验证数据完整性、配置权限、保管数据 |
| **知识技能**               | 信息安全体系、风险管理、网络安全、合规                       | IT运维、数据管理、系统操作、备份恢复       |
| **典型角色（大公司示例）** | 安全架构师（Security Architect）安全工程师（Security Engineer） | 系统管理员（SysAdmin）数据库管理员（DBA）  |

安全专业人员 = 设计/制定“怎么保护”
Custodian = 实际“执行怎么保护”的人

| 项目                       | Senior Manager（高级管理者）                       | Asset Owner（资产所有者）                        |
| -------------------------- | -------------------------------------------------- | ------------------------------------------------ |
| **职责重点**               | 为整个组织的信息安全**负责与担责**                 | 为**特定资产**的安全负责和决策                   |
| **安全职责级别**           | 组织战略级（治理层），负责授权和批准安全策略       | 战术/操作级，决定资产的分类、访问级别、保密等级  |
| **典型职责**               | 审批安全政策、承担法律责任、制定预算、任命安全人员 | 决定一份文件是“机密”还是“内部使用”、谁能访问系统 |
| **决策权限**               | 决定安全目标与方向，授权安全投资                   | 决定资产如何分类、保护与使用                     |
| **常见身份（大公司示例）** | CEO、CFO、CIO、信息安全主管（CISO）                | 部门主管、业务负责人、数据拥有部门的副总裁/总监  |

Senior Manager → 组织级战略责任 → 批准安全方向、授权、担责  
Security Professional → 设计与实施方案 → 安全架构、控制策略  
Asset Owner → 拥有特定数据资产的人 → 负责数据分类与访问控制决策  
Custodian → 保护数据的人 → 操作备份、权限、数据完整性

**User**: The user (end user or operator) role is assigned to any person who has access to the secured system. A user’s access is tied to their work tasks and is limited so that they have only enough access to perform the tasks necessary for their job position (the principle of least privilege). Users are responsible for understanding and upholding the security policy of an organization by following prescribed operational procedures and operating within defined security parameters.

**Auditor**: An auditor is responsible for reviewing and verifying that the security policy is properly implemented and the derived security solutions are adequate. The auditor produces compliance and effectiveness reports that are reviewed by the senior manager. Issues discovered through these reports are transformed into new directives assigned by the senior manager to security professionals or custodians.

All of these roles serve an important function within a secured environment. They are useful for identifying **liability** and **responsibility** as well as for identifying the hierarchical management and delegation scheme.

### Security Control Framework

Control Objectives for Information and Related Technology (COBIT): a documented set of best IT security practices crafted by the Information Systems Audit and Control Association (ISACA). It prescribes goals and requirements for security controls and encourages the mapping of IT security ideals to business objectives. 6 principles for governance and management of enterprise IT:

- Provide Stakeholder Value：关注利益相关方利益
- Holistic Approach：整体性方法，考虑人员、流程、技术等多个维度
- Dynamic Governance System：治理系统需要不断更新适应变化
- Governance Distinct from Management：区分“治理”与“管理”
- Tailored to Enterprise Needs：按需定制
- End-to-End Governance System：全生命周期治理

**CISSP考点：**

- 理解 COBIT 是“IT治理”与“业务目标对齐”的工具，不是技术控制框架。
- 它强调 **治理责任的划分、流程控制与审计支持**。

Other Standards and guidelines for IT security:

1. **NIST- SP 800**: contains US government-source general recommendations for organizational security

2. **CIS**: OS, application and hardware security configuration guides
3. **NIST RMF**: risk management framework, establishes mandatory requirements for federal agencies. Including 6 phases: **Categorize, Select, Implement, Assess, Authorize, and Monitor.**
4. **NIST CSF**: Cybersecurity Framework, designed for critical infrastructure and commercial organizations, and consists of 5 functions: **Identity, Protect, Detect, Respond, and Recover.** It is a prescription of operational activities that are to be performed on an ongoing basis for the support and improvement of security overtime.
5. **ISO/IEC 27000 family group**: an international standard that can be the basis of implementing organizational security and related management practices.
6. **ITIL**: Information technology infrastructure library, initially crafted by the british goverment, a set of recommended best practices for optimization of IT services to support business growth, transformation, and change.

| 框架/标准      | 考点总结                                                     |
| -------------- | ------------------------------------------------------------ |
| **COBIT**      | 强调 IT治理，服务于“业务目标”，6大治理原则要理解清楚         |
| **NIST 800系** | 安全控制通用指南，800-53控制、800-37风险管理、800-171保护CUI |
| **NIST RMF**   | 6阶段：Categorize → Select → Implement → Assess → Authorize → Monitor |
| **NIST CSF**   | 五大功能：Identify, Protect, Detect, Respond, Recover        |
| **ISO 27001**  | 国际ISMS标准、可认证、管理性导向，27002为控制建议            |
| **ITIL**       | IT服务管理最佳实践，重点是事件、变更、问题、持续改进         |

CISSP备考指南

- 把这几个框架**按功能分类、记忆关键词和顺序**
- 出现“治理”、“管理责任划分” → COBIT
- 出现“安全生命周期、风险管理” → NIST RMF / 800
- 出现“服务改进、事件处理” → ITIL
- 出现“国际认证、ISMS” → ISO 27001
- 考“事件响应流程”的顺序 → NIST CSF 五大功能！

#### Due Diligence(尽职调查) and Due Care(应尽义务)

**Operational security** is the ongoing maintenance of continued due diligence and due care by all responsible parties within an organization. **Due diligence** is knowing what should be done and planning for it; **due care** is doing the right action at the right time.

**例子1：网络安全策略制定与实施**

Due diligence 

- 公司制定信息安全政策（Security Policy）
- 规定密码强度、访问控制策略、日志保留时间
- 审核员工岗位是否符合最小权限原则

Due Care

- 安全管理员实际配置密码复杂度控制
- 设置日志自动归档和加密
- 对不合规的访问行为进行告警或阻止

**例子2：数据备份**

Due diligence 

- 管理层规定“关键系统每日自动备份，保留30天”

- 成立数据灾难恢复小组并制定恢复计划

Due Care

- 系统管理员每天执行/验证备份是否成功

- 定期测试恢复流程，确保灾难恢复能用

| 概念              | 中文解释            | 定义                                                         |
| ----------------- | ------------------- | ------------------------------------------------------------ |
| **Due Diligence** | 尽职调查 / 尽责筹划 | **事前规划**：制定策略、识别风险、形成规范的安全计划，体现组织管理层在安全上的“认知和准备”。 |
| **Due Care**      | 应尽义务 / 尽责执行 | **事中/事后行动**：实际执行安全控制、落实安全计划，体现“你确实采取了合理措施”。 |

Due Diligence = “你是否知道你该做什么”→ 战略与计划层面
Due Care = “你是否真的去做了这些事”→ 行动与执行层面

**计划 + 策略 + 规范制定 → Due Diligence**

**执行 + 行动 + 操作落地 → Due Care**

Senior management must show due care and due diligence to reduce their culpability and liability when a loss occurs.

### Security Policy, Standards, Procedures and Guidelines

#### Security Policies

A security policy is a doc that defines the scope of security needed by the org and discusses the assets that require protection and the extent to which security solutions should go to provide the necessary protection. 

Security policy is an overview or generalizaton of an org's security needs. It defines the strategic security objectives, vision, and goals and outlines the security framework of an org. The security policy is used to assign responsibility, define roles, specify audit requirements, outline enforcement processes, indicae compliance requirements, and define acceptable risk levels. This doc is offensive used as the proof that senior management has exercised due diligence in protecting itself against intrusion, attack, and disaster. Security policies are compulsory.

Policies are broad overviews, whereas standards, baselines, guidelines, and procedures include more specific, detailed information on the actual security solution. Standards are the next level below security policies.

**Acceptable Use Policy(AUP)** is a commonly produced document that exists as part of the overall security documentation infrastructure. AUP defines a level of acceptable performance and expectation of behavior and activity. Failure to comply with the policy may result in job action warnings, penalties, or termination.

#### Security Standards, Baselines, and Guidelines

- **Standards** define compulsory requirements for the homogenous use of hardware, software, technology, and security controls. They provide a course of action by which technology and procedures are uniformly implemented throughout an organization.

- **Baseline** defines a minimum level of security that every system throughout the organization must meet. A baseline is a more operationally focused form of a standard. All systems not complying with the baseline should be taken out of production until they can be brought up to the baseline. The baseline establishes a common foundational secure state on which all additional and more stringent security measures can be built. Baselines are usually system specific and often refer to an industry or government standard.
- **Guidelines** are the next element of the formalized security policy structure. A guideline offers recommendations on how standards and baselines are implemented and serves as an operational guide for both security professionals and users. Guidelines are flexible, so they can be customized for each unique system or condition and can be used in the creation of new procedures. They state which security mechanisms should be deployed instead of prescribing a specific product or control and detailing configuration settings. They outline methodologies, include suggested actions, and are not compulsory.

### Security Procedures

Procedures are final element of the formalized security policy structure. A procedure or standard operationg produce(SOP) is a detailed, step-by-step how-to documet that describes the exact actions necessary to implement a specific security mechanism, control, or solution. A procedure could discuss the entire system deployment operation or focus on a single product or aspect. They must be updated as the hardware and software of a system evolve. The purpose of a procedure is to ensure the integrity of business processes through standardization and consistency of results.

Keeping these documents as separate entities provides these benefits:

- Not all users need to know the security standards, baselines, guidelines, and procedures for all security classification levels.

- When changes occur, it is easier to update and redistribute only the affected material rather than updating a monolithic policy and redistributing it throughout the organization.

Once the security policy documentation is reasonably complete, it can be used to guide decisions, train new users, respond to problems, and predict trends for future expansion.

## Threat Modeling

Threat modeling is the security process where potential threats are identified, categorized, and analyzed. Threat modeling can be performed as a **proactive approach** during design and development or as a reactive measure once a product has been deployed. In either case, the process identifies the potential harm, the probability of occurrence, the priority of concern, and the means to eradicate or reduce the threat. 

Threat modeling isn't meant to be a single event. Instead, it's meant to be initiated early in the design process of a system and continue throughout its lifecycle. SDLC with the motto of "secure by design, secure by default, secure in deployment and communication. It has 2 goals in mind with this process:

- To reduce the number of security related design and coding defects

- To reduce the severity of any remaining defects

A **defensive approach** to threat modeling takes place during the early stages of system development, specifically during initial design and specifications establishment. This method is based on predicting threats and designing in specific defense during the ocing and crafting process. In most cases, integrated security solutions are more cost-effective and more successful than those shoehorned in later. While not a formal term, this concept could be considered a proactive approach to threat management.

Not all threats can be predicted during the design phase, so a **reactive approach** to threat management is still needed to address unforeseen issues. This is often called **threat hunting** or referred to as an **adversarial approach**. The technique of threat hunting is the core concept behind ethical hacking, penetration testing, source code review, and fuzz testing. Although these processes are often useful in finding flaws and threats, they unfortunately result in additional efforts in coding to add in new countermeasures, typically released as patches. This results in less effective security improvements  over defensive threat modeling at the cost of potentially reducing functionality and user-friendliness.

#### Identifying Threats

There's an almost infinite possibility of threats, so it's important to use a structured approach to accurately identify relevant threats. 

- **Focused on Assets** - This method uses asset valuation results and attempts to identify threats to the valuable assets.
- **Focused on Attackers** - Some org are able to identify potential attackers and can identify the threats they represent based on the attacker's motications, goals, or tactics, techniques, and procedures(TTPs)
- **Focused on Software** - If an org develops software, it can consider potential threats against the software.

An ultimate goal of threat modeling is to prioritize the potential threats against an organization’s valuable assets.

When attempting to inventory and categorize threats, it is often helpful to use a guide or reference. 

#### **STRIDE threat model**

- **Spoofing** identity(身份伪造): An attack with the goal of gaining access to a target system through the use of a falsified identity. When an attacker spoofs their identity as a valid or authroized entity, they are often able to bypass filters and blockades against unauthorized access.
- **Tampering** with data(数据篡改): Any action resulting in unauthorized changes or manipulation of data, whether in transit or in storage.
- **Repudiation**(抵赖行为/不可否认性攻击): The ability of a user or attacker to deny having performed an action or activity by maintaining plausible deniability. Repudiation attacks can also result in innocent thrid party being blamed for security violations.
- **Information disclosure**(信息泄露): The revelation or distribution of private, confidential, or controlled information to external or unauthorized entities.
- **Denial of Service(DOS)**: An attack that atttempts to prevent authroized use of a resource. This can be done through flaw exploitation, connection overloading, or traffic flooding.
- **Evaluation of privilege**(权限提升): An attack where a limited user account is transformed into an account with greater privileges, powers, and access.

| 威胁类型 | 英文全称                   | 中文解释                | 目标违反的安全属性                     | 举例                                                         |
| -------- | -------------------------- | ----------------------- | -------------------------------------- | ------------------------------------------------------------ |
| **S**    | **Spoofing**identity       | 身份伪造                | 违反 **Authentication（认证）**        | 攻击者伪造合法用户身份登录系统，如用盗来的Cookie冒充用户；用钓鱼网站骗取用户名密码；伪造IP地址绕过身份验证 |
| **T**    | **Tampering**with data     | 数据篡改                | 违反 **Integrity（完整性）**           | 篡改数据库中的记录、篡改软件安装包、MITM攻击中修改数据       |
| **R**    | **Repudiation**            | 抵赖行为/不可否认性攻击 | 违反 **Non-repudiation（不可否认性）** | 用户删除日志、攻击者删除访问记录、否认执行过某操作，或嫁祸于他人 |
| **I**    | **Information Disclosure** | 信息泄露                | 违反 **Confidentiality（保密性）**     | 敏感数据未加密暴露，日志中打印密码，URL参数泄露内部逻辑；未授权用户看到数据库记录 |
| **D**    | **Denial of Service**(DoS) | 拒绝服务攻击            | 违反 **Availability（可用性）**        | 攻击者发大量请求使服务崩溃，或利用系统缺陷令服务挂掉，如SYN Flood、Ping of Death |
| **E**    | **Elevation of Privilege** | 权限提升                | 违反 **Authorization（授权）**         | 普通用户提权成管理员、Web应用绕过权限检查访问后台接口、系统服务错误配置被利用 |

##### STRIDE 的使用场景

STRIDE 一般用于以下阶段：

- 软件设计：识别架构图中每个组件的潜在威胁
- 系统分析：对关键组件（数据库、API、身份系统）进行威胁分类
- 安全审查：配合 DFD（数据流图）使用，系统化检查每个元素可能受哪些威胁

🔧 **开发流程举例：**

1. 画出系统的数据流图（DFD）
2. 标出每个信任边界（Trust Boundaries）
3. 对每个元素用 STRIDE 检查 6 类威胁
4. 为每种威胁设计控制措施（如认证机制、日志记录、加密等）

假设你在建一个 **在线银行应用系统**，不同威胁可能长这样：

| 威胁类型                   | 应用场景举例                                  |
| -------------------------- | --------------------------------------------- |
| **Spoofing**               | 攻击者伪造合法用户的session token登录银行系统 |
| **Tampering**              | 攻击者拦截并修改银行转账金额字段              |
| **Repudiation**            | 用户转账后删除日志，否认进行过交易            |
| **Information Disclosure** | 系统返回API错误时泄露数据库表结构             |
| **Denial of Service**      | 攻击者用Botnet让银行网站挂掉、瘫痪            |
| **Elevation of Privilege** | 普通员工通过漏洞访问到财务总管后台权限        |

#### Process for Attack Simulation and Threat Analysis (PASTA)

区别：

- PASTA = 流程化模拟 + 风险量化；

- STRIDE = 分类识别技术威胁;

PASTA is a 7-stage threat modeling methodology. PASTA is a risk-centric(风险驱动) approach that aims at selecting or developing countermeasures in relation to the value of the assets to be protected. 

1. Stage I: Definition of the Objectives (DO) for the Analysis of Risks
2. Stage II: Definition of the Technical Scope (DTS)
3. Stage III: Application Decomposition and Analysis (ADA)
4. Stage IV: Threat Analysis (TA)
5. Stage V: Weakness and Vulnerability Analysis (WVA)
6. Stage VI: Attack Modeling & Simulation (AMS)
7. Stage VII: Risk Analysis & Management (RAM)

##### 实战备考建议（快速记忆口诀）

> **"DO The ADA To Win All Rounds"**
> ✅ DO – Objectives
> ✅ The – Technical Scope
> ✅ ADA – Application Decomposition & Analysis
> ✅ To – Threat Analysis
> ✅ Win – Weakness & Vulnerability
> ✅ All – Attack Simulation
> ✅ Rounds – Risk Management

| 阶段    | 名称                                             | 目的                                      | CISSP提示                                                   |
| ------- | ------------------------------------------------ | ----------------------------------------- | ----------------------------------------------------------- |
| **I**   | **Definition of Objectives (DO)**                | 明确分析范围、安全目标、业务目标          | 是“战略方向”的起点，体现安全与业务对齐思想（CISSP治理理念） |
| **II**  | **Definition of the Technical Scope (DTS)**      | 明确技术环境（资产、系统、接口）          | 类似 DFD 图、网络拓扑识别，常见于技术评估任务               |
| **III** | **Application Decomposition and Analysis (ADA)** | 组件拆解，数据流、交互分析                | 强调**清晰理解应用行为和信任边界**，和 STRIDE 初期类似      |
| **IV**  | **Threat Analysis (TA)**                         | 收集已知威胁、行业威胁情报                | 这里可用 STRIDE、CAPEC、MITRE ATT&CK 等作为输入模型         |
| **V**   | **Weakness and Vulnerability Analysis (WVA)**    | 查找弱点、缺陷，对照漏洞库（如 CVE、CWE） | CISSP风险管理里强调：威胁 × 脆弱性 → 风险。此步识别漏洞     |
| **VI**  | **Attack Modeling & Simulation (AMS)**           | 构建攻击路径、模拟攻击者行为（工具+战术） | 是 PASTA 的独特价值 —— 用“**攻击者视角模拟攻击流程**”       |
| **VII** | **Risk Analysis & Management (RAM)**             | 量化风险、评估影响、推荐缓解措施          | 输出对管理层友好的风险评估结果 + 控制建议（重点！）         |

| 模型       | 类型                    | 关注点                           | 适用场景                           |
| ---------- | ----------------------- | -------------------------------- | ---------------------------------- |
| **STRIDE** | **威胁分类**            | 识别具体技术威胁类型（6类）      | 软件架构早期、开发团队识别风险     |
| **PASTA**  | **攻击建模 + 风险评估** | 建模攻击过程、评估资产受损后果   | 中大型系统、业务-安全-架构协同分析 |
| **OCTAVE** | 组织级风险评估          | 从管理层视角识别资产与威胁       | 战略规划、安全治理                 |
| **DREAD**  | 风险评分工具            | 评估威胁可能性与影响程度（打分） | STRIDE补充评分，不再推荐           |

##### VAST - “敏捷友好、可视化、协作式”的现代方法

Visual, Agile, and Simple Threat (VAST) is a threat modeling concept that integrates threat and risk management into an Agile programming environment on a scalable basis

> 是由安全公司 **ThreatModeler** 提出的框架，设计目的是：

- 让 **威胁建模更贴合现实开发流程**
- 跨团队（开发、运维、安全）都能参与
- 适用于大企业、大系统、快速交付模式

VAST 模型的三大核心理念

| 名称       | 中文解释 | 含义说明                                                     |
| ---------- | -------- | ------------------------------------------------------------ |
| **Visual** | 可视化   | 使用图形化、图表方式建模，便于非技术人员理解系统结构和威胁关系 |
| **Agile**  | 敏捷协同 | 与敏捷开发流程无缝结合，适应快速迭代、持续集成（CI/CD）场景  |
| **Simple** | 简单易用 | 降低技术门槛，支持自动化、模板化建模，简化分析过程           |

VAST 与传统威胁建模方法的比较（CISSP视角）

| 特点            | STRIDE               | PASTA                      | **VAST**                                 |
| --------------- | -------------------- | -------------------------- | ---------------------------------------- |
| 模型类型        | 威胁分类型           | 风险驱动型、攻击模拟型     | 业务和技术协同建模（模型驱动）           |
| 重点关注        | 技术威胁分类         | 模拟攻击过程，评估业务风险 | 大规模协作建模、适配敏捷开发、工具自动化 |
| 适合的角色/环境 | 安全架构师、开发团队 | 安全分析师、风险管理人员   | 整个敏捷团队（Dev + Sec + Ops）          |
| 输出结果        | 威胁列表             | 风险评估报告，模拟路径     | 动态可视化威胁图，自动生成控制措施建议   |

| 考点类别                 | 具体内容与提示                                               |
| ------------------------ | ------------------------------------------------------------ |
| **VAST 的目的？**        | 简化威胁建模、支持敏捷开发、增强协作能力                     |
| **适合什么环境？**       | **DevOps、CI/CD、敏捷开发流程**中的持续安全需求建模          |
| **与STRIDE/PASTA对比？** | STRIDE = 分类威胁；PASTA = 风险分析+攻击模拟；VAST = **敏捷支持、协作友好、自动化建模** |
| **关键词记忆**           | Visual + Agile + Simple（CISSP喜欢考缩写的含义）             |
| **工具支持？**           | VAST 往往配合自动化工具，如 ThreatModeler、IriusRisk，强调“可执行的模型” |

Potential threats to your business are broad and varied. A company faces threats from nature, technology, and people. Always consider the best and worst possible outcomes of your organization’s activities, decisions, and interactions. Identifying threats is the first step toward designing defenses to help reduce or eliminate downtime, compromise, and loss.

#### Determing and Diagramming Potential Attacks

The next step in threat modeling is to determine the potential attack concepts that could be realized. This is often accomplished through the creation of a diagram of the elements involved in a transaction along with indications of data flow and privilege boundaries

![image-20250511134345082](/Users/TODO/Library/Application Support/typora-user-images/image-20250511134345082.png)

Once a diagram has been crafted, identify all of the technologies involved. Next, identify attacks that could be targeted at each element of the diagram. Keep in mind that all forms of attacks should be considered, including logical/technical, physical, and social. This process will quickly lead you into the next phase of threat modeling: reduction analysis.

##### Performing Reduction Analysis

The next step in threat modeling is to perform reduction analysis. Reduction analysis is also known as decomposing the application, system, or environment. The purpose of this task is to gain a greater understanding of the logic of the product, its internal components, as well as its interactions with external elements.

Whether an application, a system, or an entire environment, it needs to be divided into smaller containers or compartments.

Each identified element should be evaluated in order to understand inputs, processing, security, data management, storage, and outputs.

In the decomposition process, you must identify five key concepts:

1. **Trust Boundaries :** Any location where the level of trust or security changes
2. **Dataflow Paths :** The movement of data between locations 
3. **Input Points :** Locations where external input is received
4. **Privileged Operations :** Any activity that requires greater privileges than of a standard user account or process, typically required to make system changes or alter security
5. **Details about Security Stance and Approach :** The declaration of the security policy, security foundations, and security assumptions

Once threats are identified, they should be fully documented by defining the means, target, and consequences of a threat. Consider including the techniques required to implement an exploitation as well as list potential countermeasures and safeguards.

#### Prioritization and Response

After documentiation, the next step is to rank or rate the threats. This can be accomplished using a wide range of techqueniues, such as 

- Prob * Damange ranking, 
- high/medium/low rating (1/2/3 or green/yellow/red)
  - <img src="/Users/TODO/Library/Application Support/typora-user-images/image-20250511193242510.png" alt="image-20250511193242510" style="zoom:50%;" />
- the DREAD system.
  - **Damage** Potential How severe is the damage likely to be if the threat is realized?
  - **Reproducibility** How complicated is it for attackers to reproduce the exploit?
  - **Exploitability** How hard is it to perform the attack?
  - **Affected Users** percentage)?How many users are likely to be affected by the attack as a %
  - **Discoverability** How hard is it for an attacker to discover the weakness?

Once threat priorities are set, responses to those threats need to be determined. Tech and processes to remidiate threats should be considered and weighted according to their cost and effectiveness. Response options should include making adjustments to **software architecture**, altering **operations** and **processes**, and implementing **defensive and detective components.**

##### 定义区别：Process vs Operations

“安全控制如何持续有效执行？”-》 Process 提供标准，Operations 负责执行

**Process 是制定和优化“做什么”的流程标准**（如补丁审批流程、用户注册流程）

**Operations 是在日常中“怎么做”的实际动作和运维任务**（如部署补丁、监控系统、配置ACL）

**两者相辅相成：流程指导操作，操作验证流程有效性**

**Process = 设计好了的“标准流程”**
**Operation = 实际做事的“日常运维”**

| 维度          | **Processes（流程）**                                        | **Operations（操作/运维）**                     |
| ------------- | ------------------------------------------------------------ | ----------------------------------------------- |
| 定义          | 一组可重复执行的步骤，达成某个业务或技术目标的**标准化流程** | 实际运行系统、服务或产品的**日常活动/运维行为** |
| 抽象程度      | 比较**高层次**，偏向文档化、标准化的设计                     | **执行层面**的具体工作                          |
| 侧重点        | 规章制度、SOP（标准作业流程）、角色职责                      | 工具、技术平台、系统管理、监控操作              |
| 举例          | 补丁管理流程、用户注册审批流程、入职离职流程                 | 每周更新服务器、部署应用、配置系统日志          |
| CISSP对应领域 | 安全治理、策略、制度化管理                                   | 安全运营（Security Operations）                 |

### Supply Chain Risk Management

**Supply chain risk management (SCRM)** is the means to ensure that all of the vendors or links in the supply chain are reliable, trustworthy, reputable organizations that disclose their practices and security requirements to their business partners (although not necessarily to the public).

Each link in the chain should be responsible and accountable to the next link in the chain. Each handoff is properly organized, documented, managed, and audited. The goal of a secure supply chain is to ensure that the finished product is of sufficient quality, meets performance and operational goals, and provides stated security mechanisms, and that at no point in the process was any element counterfeited or subjected to unauthorized or malicious manipulation or sabotage.

In many cases, ongoing security monitoring, management, and assessment may be required. This could be an industry best practice or a regulation. Such assessment and monitoring of a supply chain may be performed by the primary or end-of-chain organization or may require the use of external auditors. When engaging third-party assessment and monitoring services, keep in mind that each element of the supply chain entity needs to show security-mindedness in their business operations.

When possible, establish minimum security requirements for each entity in a supply chain. The security requirements for new hardware, software, or services should always meet or exceed the security expected in the final product. This often requires a detailed review of SLAs, contracts, and actual performance. 

This is to ensure that security is a prescribed component of the contracted services. When a supply chain component provider is crafting software or providing a service (such as a cloud provider), then a service-level requirement (SLR) may need to be defined. An SLR is a statement of the expectations of service and performance from the product or service of a vendor. Often, an SLR is provided by the customer/client prior to the establishment of the SLA (which should incorporate the elements of the SLR if the vendor expects the customer to sign the agreement).

**SCRM 的目标是确保整个供应链链条中的各方（供应商、制造商、分销商等）都是**：

- **可靠（reliable）**
- **值得信赖（trustworthy）**
- **有信誉（reputable）**

这样才能避免供应链中出现“恶意元件”、“后门硬件”、“被篡改组件”等安全隐患。

| 核心点                   | 含义                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 信任链（chain of trust） | 每一环节都应建立在上游的可验证性和责任基础上                 |
| 验证供应链真实性         | 应用“硬件签名验证”、“组件溯源”、“SBOM（软件物料清单）”等方法 |
| 功能≠安全                | 功能验证不能替代安全检查（功能完好≠无恶意）                  |
| 风险来源可能在最上游     | 原材料商、分包商等早期阶段不可信也可能带来最终产品安全风险   |

### Summary

Security governance, management concepts, and principles are inherent elements in a security policy and in solution deployment. They define the basic parameters needed for a secure environment. They also define the goals and objectives that both policy designers and system implementers must achieve in order to create a secure solution.

The primary goals and objectives of security are contained within the CIA Triad: confidentiality, integrity, and availability. Confidentiality is the principle that objects are not disclosed to unauthorized subjects. Integrity is the principle that objects retain their veracity and are intentionally modified only by authorized subjects. Availability is the principle that authorized subjects are granted timely and uninterrupted access to objects.

Other security-related concepts and principles that should be considered and addressed when designing a security policy and deploying a security solution are identification, authentication, authorization, auditing, nonrepudiation, defense in depth, abstraction, data hiding, and encryption.

Security roles determine who is responsible for the security of an organization’s assets. Common roles include senior management, security professionals, asset owner, custodian, user, and auditor.

A formalized security policy structure consists of policies, standards, baselines, guidelines, and procedures. These individual documents are elements essential to the design and implementation of security in any environment. To be effective, the approach to security management must be a top-down approach.

Threat modeling is the security process where potential threats are identified, categorized, and analyzed. Threat modeling can be performed as a proactive measure during design and development or as a reactive measure once a product has been deployed. In either case, the process identifies the potential harm, the probability of occurrence, the priority of concern, and the means to eradicate or reduce the threat.

Integrating cybersecurity risk management with supply chain, acquisition strategies, and business practices is a means to ensure a more robust and successful security strategy in organizations of all sizes. When purchases are made without security considerations, the risks inherent in those products remain throughout their deployment life span.

## Exam Essentials

- **Understand the CIA Triad elements of confidentiality, integrity, and availability.** Confidentiality is the principle that objects are not disclosed to unauthorized subjects. Integrity is the principle that objects retain their veracity and are intentionally modified only by authorized subjects. Availability is the principle that authorized subjects are granted timely and uninterrupted access to objects.
- **Know the elements of AAA services.** AAA is composed of identification, authentication, authorization, auditing, and accountability.
- **Be able to explain how identification works.** Identification is the process by which a subject professes an identity and accountability is initiated. A subject must provide an identity to a system to start the process of authentication, authorization, and accountability.
- **Understand the process of authentication.** Authentication is the process of verifying or testing that a claimed identity is valid. Authentication requires information from the subject that must exactly correspond to the identity indicated.
- **Know how authorization fits into a security plan.** Once a subject is authenticated, its access must be authorized. The process of authorization ensures that the requested activity or object access is possible given the rights and privileges assigned to the authenticated identity.
- **Be able to explain the auditing process.** Auditing is the programmatic means by which subjects are held accountable for their actions while authenticated on a system through the documentation or recording of subject activities.
- **Understand the importance of accountability.** Security can be maintained only if subjects are held accountable for their actions. Effective accountability relies on the capability to prove a subject’s identity and track their activities.
- **Be able to explain nonrepudiation.** Nonrepudiation ensures that the subject of an activity or event cannot deny that the event occurred. It prevents a subject from claiming not to have sent a message, not to have performed an action, or not to have been the cause of an event.
- **Know about defense in depth.** Defense in depth, also known as layering, is simply the use of multiple controls in a series. Using a multilayered solution allows for numerous different controls to guard against whatever threats come to pass.
- **Be able to explain the concept of abstraction.** Abstraction is used to collect similar elements into groups, classes, or roles that are assigned security controls, restrictions, or permissions as a collective. It adds efficiency to carrying out a security plan.
- **Understand data hiding.** Data hiding is exactly what it sounds like: preventing data from being discovered or accessed by a subject. It is often a key element in security controls as well as in programming.
- **Know about security boundaries.** A security boundary is the line of intersection between any two areas, subnets, or environments that have different security requirements or needs.
- **Understand security governance.** Security governance is the collection of practices related to supporting, defining, and directing the security efforts of an organization.
- **Know about third-party governance.** Third-party governance is the system of external entity oversight that may be mandated by law, regulation, industry standards, contractual obligation, or licensing requirements. The actual method of governance may vary, but it generally involves an outside investigator or auditor.
- **Understand documentation review.** Documentation review is the process of reading the exchanged materials and verifying them against standards and expectations. In many situations, especially related to government or military agencies or contractors, failing to provide sufficient documentation to meet requirements of third-party governance can result in a loss of or a voiding of authorization to operate (ATO).
- **Understand alignment of security function to business strategy, goals, mission, and objectives.** Security management planning ensures proper creation, implementation, and enforcement of a security policy. Security management planning aligns the security functions to the strategy, goals, mission, and objectives of the organization. This includes designing and implementing security based on business cases, budget restrictions, or scarcity of resources.
- **Know what a business case is.** A business case is usually a documented argument or stated position in order to define a need to make a decision or take some form of action. To make a business case is to demonstrate a business-specific need to alter an existing process or choose an approach to a business task. A business case is often made to justify the start of a new project, especially a project related to security.
- **Understand security management planning.** Security management is based on three types of plans: strategic, tactical, and operational. A strategic plan is a long-term plan that is fairly stable. It defines the organization’s goals, mission, and objectives. The tactical plan is a midterm plan developed to provide more details on accomplishing the goals set forth in the strategic plan. Operational plans are short-term and highly detailed plans based on the strategic and tactical plans.
- **Know the elements of a formalized security policy structure.** To create a comprehensive security plan, you need the following items in place: security policy, standards, baselines, guidelines, and procedures.
- **Understand organizational process.** Security governance needs to address every aspect of an organization. This includes the organizational processes of acquisitions, divestitures, and governance committees.
- **Understand key security roles.** The 6 primary security roles are senior manager, security professional, asset owner, custodian, user, and auditor.
- **Know the basics of COBIT.** Control Objectives for Information and Related Technology (COBIT) is a security concept infrastructure used to organize the complex security solutions of companies.
- **Understand due diligence and due care.** Due diligence is establishing a plan, policy, and process to protect the interests of an organization. Due care is practicing the individual activities that maintain the due diligence effort. Due diligence is knowing what should be done and planning for it; due care is doing the right action at the right time.
- **Know the basics of threat modeling.** Threat modeling is the security process where potential threats are identified, categorized, and analyzed. Threat modeling can be performed as a proactive measure during design and development or as a reactive measure once a product has been deployed. Key concepts include assets/attackers/software, STRIDE, PASTA, VAST, diagramming, reduction/decomposing, and DREAD.
- **Understand supply chain risk management (SCRM) concepts.** SCRM is a means to ensure that all the vendors or links in the supply chain are reliable, trustworthy, reputable organizations that disclose their practices and security requirements to their business partners. SCRM includes evaluating risks associated with hardware, software, and services; performing third-party assessment and monitoring; establishing minimum security requirements; and enforcing service-level requirements.













