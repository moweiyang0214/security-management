# Laws, Regulations, and Compliance

- Domain 1.0: Security and Risk Management

### Categories of Laws

##### 总结：

**Criminal Law 惩恶，Civil Law 解纷，Administrative Law 管制执行**——三者共同构成信息安全领域的法律基础。

- Criminal Law
- Civil Law
- Administrative Law

这些法律框架是理解**信息安全合规（compliance）**、**事件应对（incident response）**、**法律责任（liability）**、以及调查与举证流程的**基础结构**。

#### 1.Criminial Law（刑法）

##### 核心目的：惩罚违法，维护社会秩序

| 内容要点                 | 示例                                                 |
| ------------------------ | ---------------------------------------------------- |
| 📌 包括严重信息犯罪       | 计算机欺诈（CFAA）、隐私窃取（ECPA）、身份盗用       |
| 📌 起诉人是国家           | 政府执法部门 + 检察官代表国家出面                    |
| 📌 判决形式有监禁、罚款等 | 重大黑客案、勒索攻击操作者、国家级APT入侵行为        |
| 📌 CISSP重点：            | 了解关键信息安全犯罪立法 + 法律适用范围（美国/国际） |

Criminal law contains prohibitions against acts such as murder, assault, robbery, and arson. Penalties for violating criminal statutes fall in a range that includes mandatory hours of community service, monetary penalties in the form of fines (small and large), and deprivation of civil liberties in the form of prison sentences.

protect society against computer crime: such as the Computer Fraud and Abuse Act, the Electronic Communications Privacy Act, and the Identity Theft and Assumption Deterrence Act (among others), provide criminal penalties for serious cases of computer crime.

**Technically savvy**  (精通技术) **prosecutors**(检察官) teamed with concerned law enforcement agencies have dealt serious blows to the “hacking underground” by using the court system to slap lengthy prison terms on offenders guilty of what used to be considered harmless **pranks** (恶作剧).

All federal and state laws must comply with the ultimate authority that dictates how the U.S. system of government works—the **U.S. Constitution (美国宪法).**

All laws are subject to **judicial**(裁判的) review by **regional courts(地区法院)** with the right of appeal all the way to the **Supreme Court (最高法院)** of the United States. If a court finds that a law is unconstitutional, it has the power to strike it down and render it invalid.

Keep in mind that criminal law is a serious matter. If you find yourself involved—as a witness, defendant, or victim—in a matter where criminal authorities become involved, you’d be well advised to seek advice from an attorney familiar with the criminal justice system and specifically with matters of computer crime. It’s not wise to “go it alone” in such a complex system.

**常考法案举例：**

- CFAA（Computer Fraud and Abuse Act）
- ECPA（Electronic Communications Privacy Act）
- Identity Theft and Assumption Deterrence Act

#### 2.Civil Law（民法）

##### 核心目的：解决个人/组织间的权利与义务纠纷

| 内容要点                 | 示例                                                 |
| ------------------------ | ---------------------------------------------------- |
| 📌 被侵犯方主动提起诉讼   | 雇员因资料被泄露向公司索赔                           |
| 📌 仅追究“赔偿”而非“监禁” | 赔偿损失、合同罚款、禁令                             |
| 📌 安全场景常见           | 数据泄露、IP侵权、合同违约、员工滥用系统             |
| 📌 CISSP重点：            | 学会识别民事责任、责任界定和举证责任（谁举证谁负责） |

Civil laws form the bulk of the U.S. body of laws. They are designed to provide for an orderly society and govern matters that are not crimes but that require an **impartial(公正的)** **arbiter(仲裁者)** to settle between individuals and organizations.

Examples of the types of matters that may be judged under civil law include contract disputes, real estate transactions, employment matters, and estate/probate procedures. Civil laws also are used to create the framework of government that the executive branch uses to carry out its responsibilities. These laws provide budgets for governmental activities and lay out the authority granted to the executive branch to create administrative laws.

In a criminal **prosecution(起诉)**, the government, through law enforcement investigators and prosecutors, brings action against a person accused of a crime.

In civil matters, it is incumbent upon the person who thinks they have been wronged to obtain **legal** **counsel (法律顾问)** and file a **civil** **lawsuit(民事诉讼)** against the person they think is responsible for their **grievance (不满).** 

The government (unless it is the **plaintiff(原告)** or **defendant(被告)**) does not take sides in the **dispute(争端)** or argue one position or the other. The only role of the government in civil matters is to provide the **judges(法官)**, **juries(陪审团)**, and court facilities used to hear civil cases and to play an administrative role in managing the **judicial system (司法系统)** in accordance with the law. 

Although civil law does not impose the threat of **imprisonment (监禁)**, the losing party may face severe financial penalties.

**例子：**

- 某 SaaS 公司未加密客户数据 → 客户起诉要求损害赔偿
- 公司未尽安全义务，导致前员工信息泄露 → 员工提民事索赔

#### 3. Administrative Law（行政法）

##### 核心目的：指导政府部门内部执行、合规、审查等操作

| 内容要点                         | 示例                                            |
| -------------------------------- | ----------------------------------------------- |
| 📌 由各政府机构执行               | 如FDA、FBI、FTC、移民局、IRS、NIST等            |
| 📌 涉及认证、执照、行政命令、处罚 | GDPR 合规审查，HIPAA 遵守情况，SEC 财报控制义务 |
| 📌 安全领域应用                   | 合规评估、监管上报、强制措施（例如封禁、取证）  |
| 📌 CISSP重点：                    | 识别行政法规对信息系统的影响 + 合规责任所在     |

Administrative law covers topics as mundane as the procedures to be used within a federal agency to obtain a desk telephone to more substantial issues such as the immigration policies that will be used to enforce the laws passed by Congress. Administrative law is published in the Code of Federal Regulations (CFR).

To understand compliance requirements and procedures, you must be fully versed in the complexities of the law. From administrative law to civil law to criminal law (and, in some countries, even religious law), navigating the regulatory environment is a daunting task. The CISSP exam focuses on the generalities of law, regulations, investigations, and compliance as they affect organizational security efforts. Specifically, you will need to

- Understand legal and regulatory issues that pertain to information security in a holistic concept.
- Determine compliance and other requirements that apply to your organization.

**行政法典参考：**

- Code of Federal Regulations (CFR) 是美国行政法规的官方汇编

**例子：**

- 企业未遵守SOX法案的数据保留要求 → 被SEC处以行政罚款
- 医疗系统未遵循HIPAA隐私规定 → 被HHS要求整改并签订CAP（Corrective Action Plan）

##### 三大法律类别总览对比表

| 法律类别               | 中文名称 | 目标对象                             | 谁起诉谁？           | 结果可能包括                     | 安全领域示例                      |
| ---------------------- | -------- | ------------------------------------ | -------------------- | -------------------------------- | --------------------------------- |
| **Criminal Law**       | 刑法     | 社会整体 vs 违法个人（国家为原告）   | 政府起诉个人/组织    | **监禁、罚款、社区服务**         | 黑客入侵、数据盗窃、拒服从监管    |
| **Civil Law**          | 民法     | 个人或组织之间的纠纷                 | 一方当事人诉另一方   | **金钱赔偿、禁令、合同约束**     | 合同违约、泄密索赔、知识产权侵犯  |
| **Administrative Law** | 行政法   | 公共行政执行规则（组织 vs 政府部门） | 行政机构执法、审批等 | **合规惩罚、吊销资质、审查调整** | 未遵守HIPAA/GDPR审查、ISO认证审核 |

##### 信息安全专业人员如何应对三类法律问题？

| 法律类别   | 安全应对职责                                       |
| ---------- | -------------------------------------------------- |
| **刑法**   | 识别违法行为、保留证据、配合执法机关、避免触法     |
| **民法**   | 理解合同义务、数据责任归属、做好保密和免责策略     |
| **行政法** | 熟悉行业监管要求、跟进合规评估与整改、参与审计准备 |

##### CISSP 考试/实战提醒

| 常考题型                              | 回答关键点                               |
| ------------------------------------- | ---------------------------------------- |
| 计算机黑客是否属刑事犯罪？            | ✅ 是刑法，依据CFAA等                     |
| 客户因隐私泄露起诉公司属于？          | ✅ 民事纠纷（Civil Suit）                 |
| 企业未按HIPAA处理患者数据会被追责吗？ | ✅ 会，由行政机构处罚（HHS）              |
| 行政法是否能处罚企业？                | ✅ 可，方式为审计、禁令、罚款等非刑事形式 |
| 民事案件中，是否由政府出面？          | ❌ 不涉及执法机关，除非政府是当事人一方   |

## Laws

Every information security professional should have a basic understanding of the law as it relates to information technology. However, the most important lesson to be learned is knowing when it’s necessary to call in an attorney. If you think you’re in a legal “gray area,” it’s best to seek professional advice.

#### Computer Crime

The U.S. laws discussed in this chapter are federal laws. But keep in mind that almost every state in the union has also **enacted(制定)** some form of legislation regarding computer security issues. Because of the global reach of the internet, most computer crimes cross state lines and, therefore, fall under federal **jurisdiction(管辖范围内)** and are prosecuted in the federal court system. However, in some circumstances, state laws can be more restrictive than federal laws and **impose（强制执行）** harsher penalties.

#### Computer Fraud and Abuse Act（CFAA）

**✅总结：CCCA 是“总则”，CFAA 是“专章”**——CFAA在CCCA的基础上建立了**专门应对计算机犯罪的刑法机制**，并成为联邦信息安全执法的基石之一。

The first major piece of cybercrime-specific legislation in the United States, as part of the **Comprehensive Crime Control Act (CCCA).** 

| 法律名称 | 全称                            | 成立时间               | 核心内容                                       |
| -------- | ------------------------------- | ---------------------- | ---------------------------------------------- |
| **CCCA** | Comprehensive Crime Control Act | 1984年                 | 涵盖全面犯罪控制，包括计算机犯罪的初步内容     |
| **CFAA** | Computer Fraud and Abuse Act    | 1986年（基于CCCA补充） | 专门聚焦跨州或联邦计算机犯罪，设定明确刑事责任 |

##### CCCA vs CFAA

| 方面           | CCCA                       | CFAA                                                         |
| -------------- | -------------------------- | ------------------------------------------------------------ |
| 🎯 **目的**     | 控制“所有犯罪”的一揽子立法 | 解决**计算机相关犯罪**特别是**跨州**的联邦犯罪问题           |
| ⚖️ **适用范围** | 包括计算机犯罪，但范围模糊 | 精准聚焦**未经授权访问、数据篡改、密码买卖、网络欺诈等行为** |
| 🌐 **跨州管辖** | 覆盖不清晰，可能侵犯州权利 | 专门设计为跨州管辖的联邦法案，**避免与州法冲突**             |
| 🔐 **细化行为** | 模糊列举                   | 明确列出以下六种违法行为（见下）                             |

##### CFAA 明确规定的6种犯罪行为

| 违法行为                                                     | 描述                               |
| ------------------------------------------------------------ | ---------------------------------- |
| 1️⃣ Access classified information or financial information in a federal system without authorization or in excess of authorized privileges <br/>未授权访问联邦系统中的**机密信息或财务数据** | 超越权限进入敏感系统属违法         |
| 2️⃣ Access classified information or financial information in a federal system without authorization or in excess of authorized privileges<br/>未经授权访问**联邦专用计算机** | 即使未造成损害，访问本身就违法     |
| 3️⃣ Use a federal computer to perpetrate a fraud (unless the only object of the fraud was to gain use of the computer itself)<br>使用联邦计算机实施欺诈 | 除非欺诈仅为获取该计算机本身使用权 |
| 4️⃣ Cause malicious damage to a federal computer system in excess of $1,000<br>**恶意破坏**联邦计算机系统，造成超\$1,000损失 | 包括物理和逻辑破坏                 |
| 5️⃣ Modify medical records in a computer when doing so impairs or may impair the examination, diagnosis, treatment, or medical care of an individual<br>**篡改医疗记录**，影响诊疗判断 | 数据被改，患者可能被误诊           |
| 6️⃣ Traffic in computer passwords if the trafficking affects interstate commerce or involves a federal computer system<br>**密码贩运**，若涉及州际商业或联邦系统 | 比如买卖企业VPN账户的行为          |

##### 从CCCA到CFAA的演进意义

| 价值                     | 解释                                                         |
| ------------------------ | ------------------------------------------------------------ |
| ✅ **聚焦计算机安全立法** | 从“大而杂”的CCCA中抽出独立条款，专门保护联邦与关键IT系统     |
| ✅ **避免宪法争议**       | CFAA聚焦跨州行为，绕开宪法上“州权优先”的敏感区               |
| ✅ **强化执法实践**       | 提供清晰法律依据，让技术型检察官和警察有据可依，追诉网络犯罪 |
| ✅ **回应技术时代**       | 从恶作剧（pranks）到重罪（felonies），法律适应新时代安全威胁 |

#### CFAA 的1986修订

**立法目的**：扩大执法范围，使其涵盖更多现实中可能被攻击的系统，尤其是与金融、政府相关系统。

**✅总结：CFAA 的修订扩大了法律适用范围：只要是“影响到联邦利益”的系统，不论所有权归属，哪怕是跨州作案，皆可适用。**

| 修订前                               | 修订后                                                   |
| ------------------------------------ | -------------------------------------------------------- |
| 仅保护 **“处理敏感信息的联邦计算机”** | 扩展到所有具有“**联邦利益（federal interest）**”的计算机 |
| 损害赔偿门槛为 **\$1,000**           | 上调为 **\$5,000**                                       |

##### “Federal Interest Computers” 的含义与范围

下列系统/情形即构成“federal interest”，也就是 CFAA 可适用的对象：

**重点理解**：**即使不是“政府拥有”，但只要“对政府系统造成妨碍”，就属联邦利益计算机**

| 类型                                                         | 描述                                              | 信息安全场景举例                      |
| ------------------------------------------------------------ | ------------------------------------------------- | ------------------------------------- |
| ✅ **专供联邦政府使用的计算机**：Any computer used exclusively by the U.S. government | 例如政府内网、国防系统、国税局系统                | 攻击国税局网站或FBI数据库             |
| ✅ **专供金融机构使用的计算机**： Any computer used exclusively by a financial institution | 银行内部系统、ATM主机、证券交易引擎               | 非法入侵银行交易主机或盗刷平台        |
| ✅ **对政府/金融机构造成干扰的攻击行为**：Any computer used by the government or a financial institution when the offense impedes the ability of the government or institution to use that system | 即使计算机为商业用途，但攻击导致政府/银行无法运作 | 攻击承包商网络导致国防系统宕机        |
| ✅ **跨州使用的多台计算机用于犯罪**： Any combination of computers used to commit an offense when they are not all located in the same state | 多地设备组合进行的攻击行为                        | 例如利用不同州的VPN跳板发起分布式攻击 |

##### CFAA  1986 适用范围扩大后的影响

| 影响类别            | 实际含义                                       |
| ------------------- | ---------------------------------------------- |
| ⚖️ 法律适用更广      | 企业/承包商系统也可能被纳入CFAA保护            |
| 👮‍♂️ 执法能力增强     | 联邦机构可介入更多网络攻击案件                 |
| 🧑‍💻 安全合规要求提升 | 涉及政府/金融业务的组织需遵守更高安全要求      |
| 🌐 跨州/多地犯罪受限 | 使用多地计算机发起攻击也会被追责（防止DDoS等） |

##### CISSP备考要点

| 问题                                                      | 正确理解方式                                                 |
| --------------------------------------------------------- | ------------------------------------------------------------ |
| 什么是“federal interest computer”？                       | 不仅是政府电脑，还包括金融系统 + 与政府/银行相关系统         |
| 如果攻击某承包商的服务器但影响了政府业务，是否触犯 CFAA？ | ✅ 是的，属于“妨碍联邦机构使用”的情形                         |
| 多州设备联动攻击算不算 CFAA 范围？                        | ✅ 是的，跨州攻击是 CFAA 明确覆盖范围                         |
| $5,000损害门槛代表什么？                                  | ✅ 只有在**损失金额超过5千美元**时才能刑事起诉（但民事可另说） |

#### CFAA 1994年修订（Computer Abuse Amendments Act Amendments）

原因：应对网络犯罪形式变化、非“联邦系统”的更广泛犯罪行为

| 变更项                                                       | 说明                                                         | 实际含义                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------ |
| 🦠 禁止制造“恶意代码”：Outlawed the creation of any type of malicious code that might cause damage to a computer system | 即使未传播，**创造病毒、蠕虫、逻辑炸弹等**已属违法           | 编写勒索病毒者也可定罪               |
| 🌐 扩展到“州际商业”计算机：Modified the CFAA to cover any computer used in interstate commerce rather than just “federal interest” computer systems | 不再只限“federal interest”系统，**任何参与州际通信的计算机**均涵盖 | 几乎所有联网计算机都受保护           |
| 🚔 无意造成损害也可入狱：Allowed for the imprisonment of offenders, regardless of whether they actually intended to cause damage | 删除“故意造成损害”作为前提，仅行为本身即可定罪               | 进一步扩大了适用范围                 |
| ⚖️ 增加民事诉讼权利：Provided legal authority for the victims of computer crime to pursue civil action to gain injunctive relief and compensation for damages | 受害人可以发起**民事诉讼**要求禁令与赔偿                     | 企业可直接控告攻击者，无需等政府介入 |

**积极意义：**

| 优势              | 说明                                       |
| ----------------- | ------------------------------------------ |
| 📈 提高威慑力      | 编写恶意代码也属犯罪，不必等其“生效”       |
| 🔒 覆盖更广        | 几乎所有联网商业系统都受保护               |
| 🧑‍⚖️ 民事补救更可行 | 企业可以自主起诉，无需完全依赖政府起诉流程 |

**严重争议点**：

| 问题                   | 说明                                                         | 后果                         |
| ---------------------- | ------------------------------------------------------------ | ---------------------------- |
| ❗ 定义过于宽泛         | “超出授权访问”含义模糊，甚至可能包括违反网站**用户协议**     | 平凡违规操作可能被定罪       |
| 🧑‍💻 **Aaron Swartz 案** | 黑客/开源活动者因下载学术论文被起诉，后来自杀                | 激起舆论对CFAA滥用的反对浪潮 |
| ⚖️ Aaron’s Law 草案     | 旨在将“违反服务条款”行为排除在 CFAA 刑法范围外，但**未通过国会表决** | 立法改革受阻                 |

##### CFAA 修订与争议的阶段性总结

| 阶段       | 时间                                  | 关键词                             | 法律特征                 |
| ---------- | ------------------------------------- | ---------------------------------- | ------------------------ |
| 初始版本   | 1986                                  | 联邦系统                           | 限于政府/关键设施计算机  |
| 第一次大修 | 1994                                  | 州际商业 + 恶意代码 + 民事补救     | **适用面爆炸式扩大**     |
| 持续修订   | 1996(NIIPA of 1996), 2001, 2002, 2008 | 加入恐怖主义、间谍、电信等领域内容 | 与《爱国者法案》叠加应用 |
| 批评与判例 | 2010s-至今                            | Aaron Swartz 案、Van Buren 案      | 正在逐步“收敛”解释范围   |

**CFAA 从“联邦计算机保护法”演进为“广泛的网络安全刑法”**，虽然增强了安全防御力度，但也因为适用范围过宽而引发争议与司法限制。

#### National Information Infrastructure Protection Act of 1996 (NIIPA of 1996)

**✅总结：NII Act 是 CFAA 的“物理世界延伸”版本，它让信息安全责任从“数据中心”扩展到了“国家命脉设施”。**

这项立法是对 CFAA 的进一步扩展，**从“州际”走向“国际”**，它是 **CFAA 的增强版**，进一步扩大了对信息系统和国家关键基础设施的保护范围。

| 法案名称 | National Information Infrastructure Protection Act           |
| -------- | ------------------------------------------------------------ |
| 核心作用 | **扩展 CFAA 的适用范围**，纳入更广泛的国家基础设施和国际领域 |

##### 三大关键扩展点总结

1. **从“州际”扩展到“国际”商业系统**

变化前 : 仅涵盖“**interstate commerce**”（州与州之间）相关计算机系统 
变化后 : 包含“**international commerce**”（国际商业）中使用的系统 

📌 **影响：** 大大增强了 CFAA 对跨国公司的适用性 —— 如全球云服务商、国际交易平台、外企在美服务器等。

2. **保护范围扩大到“非计算机”关键基础设施**

原本 CFAA 只覆盖“计算机系统”，但 NII 扩展到了：

| 新增保护对象 | 示例                           |
| ------------ | ------------------------------ |
| 🚄 铁路系统   | 铁路控制系统、信号调度系统     |
| ⛽ 天然气管网 | 自动控制阀门系统、输送监控系统 |
| ⚡ 电网系统   | SCADA系统、电力配电监控系统    |
| 📞 电信线路   | 光纤主干、电信交换平台         |

**关键词：Critical Infrastructure（关键基础设施）** 这也是日后政府定义 CIKR（Critical Infrastructure and Key Resources）体系的基础。

3. **恶意攻击关键基础设施 = 升级为“重罪”（Felony）**

| 新增处罚逻辑                                 | 说明                                                 |
| -------------------------------------------- | ---------------------------------------------------- |
| **故意或“鲁莽”（reckless）破坏**关键基础设施 | 即使没有明确犯罪动机，只要行为导致严重后果，也可定罪 |
| **不再需要证明意图**                         | 只要行为“有破坏力”，即可定为犯罪                     |

例子：

- 黑客攻击电网，误操作导致区域性停电 → 属于 felony
- 想做压力测试但未授权，导致铁路调度混乱 → 也可能被追责

##### NII Amendments（1996）对比CFAA（1994）

| 项目     | CFAA（1994）         | NII Amendments（1996）                       |
| -------- | -------------------- | -------------------------------------------- |
| 商业范围 | 州际（Interstate）   | 增加国际（International）                    |
| 对象范围 | 计算机系统           | 增加国家级基础设施（铁路、管网、电网、通信） |
| 犯罪门槛 | 必须有“故意破坏”行为 | 增加“鲁莽破坏”也定罪，**降低门槛**           |
| 安全影响 | 主要保护数据系统     | 转向**数据+物理系统双重保护**                |

##### 信息安全人员的任务

| 安全职责                         | 应对策略                                   |
| -------------------------------- | ------------------------------------------ |
| 🧩 识别本组织是否涉及国际商业系统 | 云平台、海外数据中心、国际支付系统         |
| 🛠️ 确保关键基础设施具备防护措施   | 与OT安全部门协作、加固SCADA等系统          |
| 📄 熟悉相关法规以支持合规         | 特别是政府承包商、能源、制造、医疗等行业   |
| ⚠️ 演练错误造成物理破坏风险       | 降低测试行为不当带来的“reckless liability” |

##### CISSP 考点提示

| 考题方向                               | 正确答案示例                             |
| -------------------------------------- | ---------------------------------------- |
| 哪项立法扩展了CFAA以覆盖关键基础设施？ | ✅ NII Protection Act                     |
| 该法案适用于哪些系统？                 | ✅ 铁路、电网、管道、通信线路             |
| 行为造成无意但严重破坏是否违法？       | ✅ 是的，“reckless acts”也属 felony       |
| 云系统涉国际交易是否受保护？           | ✅ 是的，属于 international commerce 范畴 |

#### Federal Sentencing(判罚) Guidelines 1991

**✅总结：Federal Sentencing Guidelines 为信息安全管理注入了法律责任和治理标准，要求高管“不能装不知道，必须做到明知、尽责、监督”。**

| 项目             | 内容                                                     |
| ---------------- | -------------------------------------------------------- |
| 📅 发布年份       | 1991年，由美国联邦量刑委员会提出                         |
| 🎯 核心目标       | 为联邦法官提供在裁定“企业犯罪或失责”时的**判罚参考标准** |
| 🛡️ 对信息安全影响 | 明确了高管在安全领域的法律责任，推动企业建立合规安全体系 |

Three major provisions of these guidelines have had a lasting impact on the information security community:

■✓ The guidelines formalized the prudent person rule, which requires senior executives to take personal responsibility for ensuring the due care that ordinary, prudent individuals would exercise in the same situation. This rule, developed in the realm of fiscal responsibility, now applies to information security as well.

■✓ The guidelines allowed organizations and executives to minimize punishment for infractions by demonstrating that they used due diligence in the conduct of their information security duties.

■✓ The guidelines outlined three burdens of proof for negligence: First, the person accused of negligence must have a legally recognized obligation. Second, the person must have failed to comply with recognized standards. Finally, there must be a causal relationship between the act of negligence and subsequent damages.

##### 三大核心影响点解析

1. **Prudent Person Rule（审慎人规则）**

要求高层管理人员以“一个理性、负责任的人”应有的方式对待安全管理。

| 内容               | 含义                                                         |
| ------------------ | ------------------------------------------------------------ |
| ✅ 源于财务合规制度 | 原用于公司财务、审计责任                                     |
| ✅ 延伸至信息安全   | 高层管理者必须为信息安全治理“亲自担责”                       |
| ✅ 实际体现         | 不能忽视安全问题，也不能推给技术部门，必须**有监督、有投入、有制度** |

📌在 CISSP 中体现为：“Due Care” 的法律化落地

2. **通过“Due Diligence”可减轻惩罚**

如果企业能证明在信息安全上 **有制度、有培训、有投入、有响应机制**，即使出事，也可减轻处罚。

| 对象         | 法官考虑要素                                                 |
| ------------ | ------------------------------------------------------------ |
| ✅ 组织/企业  | 是否建立了安全政策、是否进行风险评估与定期审查、是否有处理流程 |
| ✅ 管理层个人 | 是否履行监督职责、是否授权安全预算、是否参与安全决策         |

📌 实际意义：企业“不是零风险”，但只要**展示了合规意图与行为**，可降低法律处罚

3. **三点构成“过失（Negligence）”的判定标准**

如果被控“信息安全疏忽”，法官会看是否满足以下三点：

| 条件             | 说明                                                        |
| ---------------- | ----------------------------------------------------------- |
| ① 有法律责任存在 | 被告有义务保障某方面的安全（如数据保护、访问控制）          |
| ② 未遵守行业标准 | 没有采取业内通行或法规要求的保护措施                        |
| ③ 存在因果关系   | 漏洞/疏忽与事故结果之间存在直接联系（如数据泄露、客户损失） |

📌 举例：

- 公司未启用最基本的密码策略 → 员工账号被攻破 → 客户数据泄露
  → 满足**三要件**，可被认定为“过失”（negligence）

##### 和信息安全核心概念的联系

| 法律术语                      | 安全管理术语                       | 含义                                 |
| ----------------------------- | ---------------------------------- | ------------------------------------ |
| **Prudent Person Rule**       | → **Due Care（应尽注意义务）**     | 管理层应具备基本的安全意识和控制意识 |
| **Due Diligence（尽职调查）** | → 安全架构、风险评估、治理流程     | 管理者/团队主动评估和控制风险        |
| **Negligence（疏忽）**        | → 安全事件中常见的法律责任归因方式 | 未尽“合理人的责任”即构成过失         |

##### **CISSP 考点速查**

| 问题                                   | 答案                                         |
| -------------------------------------- | -------------------------------------------- |
| 什么是“Prudent Person Rule”？          | ✅ 要求管理层对信息安全承担法律级别的注意义务 |
| 如果企业尽职尽责但仍被黑，是否会被罚？ | ❌ 可酌情减轻甚至免除处罚（根据指南）         |
| Negligence 的三个判断要素？            | ✅ 法律义务、违反标准、因果关系               |
| Guidelines 是强制法条吗？              | ❌ 不是法律本身，而是判案时的“判罚指导依据”   |

#### Federal Information Security Management Act (FISMA 2002)

✅**总结：FISMA 是联邦机构与承包商的安全合规底线，NIST 提供执行方法，组织必须用“文档 + 证据 +周期”证明自己安全。**

| 项目       | 内容                                                         |
| ---------- | ------------------------------------------------------------ |
| 📅 通过时间 | 2002年，由美国国会通过                                       |
| 🧩 替代法规 | 取代了 1987 年的《计算机安全法》与 2000 年的《信息安全改革法》 |
| 🎯 立法目的 | 强制联邦政府实施全面的信息安全计划<br/>将政府承包商纳入信息安全责任体系<br/>建立标准化的安全评估与治理框架 |
| 🏛️ 管理机构 | National Institute of Standards and Technology - NIST（标准制定） + OMB（预算监督） |

FISMA 指出，联邦机构与其承包商(Contractors)必须建立一整套**基于风险的信息安全管理体系**，主要包括以下 8 大模块：

1. **风险评估（Risk Assessment）**

■✓ Periodic assessments of risk, including the magnitude of harm that could result from the unauthorized access, use, disclosure, disruption, modification, or destruction of information and information systems that support the operations and assets of the organization

周期性识别信息系统面临的威胁与影响

| 要求       | 说明                                         |
| ---------- | -------------------------------------------- |
| 🧠 风险类型 | 未授权访问、破坏、篡改、泄露、拒绝服务等     |
| 📊 评估内容 | 威胁来源、漏洞、潜在损害等级                 |
| 📅 频率     | 应定期执行，根据系统关键性定制（不少于年度） |

2. **安全政策与标准（Policies & Procedures）**

■✓ Policies and procedures that are based on risk assessments, cost-effectively reducing information security risks to an acceptable level and ensuring that information security is addressed throughout the lifecycle of each organizational information system

建立覆盖系统全生命周期的安全策略

- 要求 : 包括所有系统设计、开发、部署、运维阶段的控制要求
- 目标 : **成本效益合理地控制风险至可接受水平** 

3. **子系统级安全计划（Subordinate Plans）**

■✓ Subordinate plans for providing adequate information security for networks, facilities, information systems, or groups of information systems, as appropriate

针对具体子系统或网络制定独立的安全措施计划

**应用场景 :** 云平台、分布式系统、供应链通信等关键组件 

4. **安全意识培训（Awareness Training）**

■✓ Security awareness training to inform personnel (including contractors and other users of information systems that support the operations and assets of the organization) of the information security risks associated with their activities and their responsibilities in complying with organizational policies and procedures designed to reduce these risks

针对所有用户（内部员工 + 外包/承包商）

- 目的 :让用户理解安全威胁，**知责于心，守责于行**
- 形式 : 培训课程、模拟演练、考试 

5. **控制效果测试（Testing & Evaluation）**

■✓ Periodic testing and evaluation of the effectiveness of information security policies, procedures, practices, and security controls to be performed with a frequency depending on risk, but no less than annually

**至少每年一次**对政策、控制措施的有效性进行审查

内容：

- 是否部署了安全措施？
- 是否真的在发挥作用？
- 是否有人在跟进维护？ 

6. **整改机制（Remedial Actions）**

■✓ A process for planning, implementing, evaluating, and documenting remedial actions to address any deficiencies in the information security policies, procedures, and practices of the organization

针对发现的问题，要有整改流程并**留痕记录**。 包括 ： 计划 → 执行 → 验证 → 文档化 

7. **事件响应机制（Incident Response）**

■✓ Procedures for detecting, reporting, and responding to security incidents

安排报告、溯源、隔离、修复、通报等流程。要求 ： 需建立 **标准操作流程（SOP）** 与通报机制，联动US-CERT等单位 

8. **业务连续性（Continuity of Operations）**

■✓ Plans and procedures to ensure continuity of operations for information systems that support the operations and assets of the organization

信息系统需具备在灾难下的恢复与持续能力。对标 ： BCP/DRP 实施要求：RPO、RTO、演练、站点切换等

##### FISMA 对组织（特别是政府承包商）的影响

FISMA places a significant burden on federal agencies and government contractors, who must develop and maintain substantial documentation of their FISMA compliance activities.

| 类别         | 实际负担与要求                                               |
| ------------ | ------------------------------------------------------------ |
| 📚 文档负担   | **需要大量的安全政策、计划、培训与整改记录**                 |
| 📋 审计要求   | 需接受联邦审计，如GAO或机构IG                                |
| 🤝 供应链控制 | 承包商和第三方供应商也需满足相应的FISMA要求                  |
| 🧩 工具使用   | 多使用 NIST SP 800 系列（如 800-53, 800-37, 800-171）进行合规建模 |

##### FISMA 与 NIST RMF 的关系（CISSP 常考）

FISMA 作为法律，**定义“必须做什么”**
NIST RMF（Risk Management Framework）提供 **“怎么做”** 的方法

| NIST RMF 步骤       | 对应 FISMA 要求        |
| ------------------- | ---------------------- |
| Categorize 系统分类 | 风险评估起点           |
| Select 控制选择     | 策略/子系统控制        |
| Implement 控制部署  | 安全政策落地           |
| Assess 控制评估     | 控制测试与验证         |
| Authorize 认证批准  | 安全官/高层签署        |
| Monitor 持续监控    | 保持动态调整、整改追踪 |

#### Federal Cybersecurity Laws of 2014

**✅总结：2014 三大网络安全法案确立了联邦安全治理新模式：DHS 统筹 → NIST 定标 → NCCIC 共享，全链路覆盖技术、管理与战略协作。**

| 法律名称                                                     | 主要目的                               | 执行机构                     | 简要说明                                       |
| ------------------------------------------------------------ | -------------------------------------- | ---------------------------- | ---------------------------------------------- |
| 🔹 **FISMA 2014**（信息系统现代化法案）Federal Information Systems Modernization Act | 中央化联邦网络安全责任                 | DHS（国土安全部）            | 修改 2002 年 FISMA，强调**协调统一管理**       |
| 🔹 **Cybersecurity Enhancement Act**（网络安全增强法）        | 赋予 NIST 制定全国网络安全标准的主导权 | NIST（国家标准与技术研究院） | 重点推动 SP 800 系列与 Cybersecurity Framework |
| 🔹 **National Cybersecurity Protection Act**（国家网络安全保护法） | 建立跨部门共享平台                     | DHS 下属 NCCIC               | 强化政府与民间组织的信息共享与协同防御能力     |

1. **Federal Information Systems Modernization Act (FISMA 2014)**

| 项目        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| 🎯 目的      | 对 2002 年版 FISMA 进行修订，更明确权责体系                  |
| 📌 变化      | 将联邦网络安全责任从各机构转移至 **DHS（国土安全部）**        |
| ❗ 例外      | 国防相关 → 由 **国防部长（DoD）** 负责<br/>情报相关 → 由 **国家情报总监（DNI）** 负责 |
| 🧑‍⚖️ 实务重点 | 中央统一防护、跨部门协调、联邦承包商也需纳入                 |

2. **Cybersecurity Enhancement Act**

| 项目        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| 📌 主导单位  | **NIST**（国家标准与技术研究院）                             |
| 🎯 任务      | 推动开发**自愿性、可操作、基于风险**的全国网络安全标准       |
| 📘 重点产出  | NIST SP 800-53：政府系统安全控制清单（信息安全业界标杆）<br/>NIST SP 800-171：保护 **非联邦系统中 CUI（受控非机密信息）** 的控制标准<br/>NIST CSF：自愿框架，五大功能：识别（Identify）→ 保护（Protect）→ 检测（Detect）→ 响应（Respond）→ 恢复（Recover） |
| 🧑‍💼 实务影响 | 政府承包商在合同中往往会要求 SP 800-171 合规<br/>NIST 标准也被业界作为 通用安全参考模型 |

3. **National Cybersecurity Protection Act**

This law charged the **Department of Homeland Security（DHS）** with establishing a **national cybersecurity and communications integration center（NCCIC）**. The role of this center is to serve as the interface between federal agencies and civilian organizations for sharing cybersecurity risks, incidents, analysis, and warnings.

| 项目       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 📌 机构     | 成立 **NCCIC（National Cybersecurity and Communications Integration Center）** |
| 🧠 职责     | 联邦各机构与私营组织之间的网络威胁共享中枢<br/>提供预警、分析、响应建议 |
| 🎯 目的     | 建立“国家级威胁共享机制”，打破情报孤岛                       |
| 🔧 实务能力 | 与 **CISA（Cybersecurity and Infrastructure Security Agency）  美国网络安全与基础设施安全局**一起构建现代联邦网络防护能力 |

##### CISSP 应试与实务知识点

| 考点类型                             | 重点记忆内容                                                 |
| ------------------------------------ | ------------------------------------------------------------ |
| ✅ 谁主导联邦网络安全协调？           | **DHS（FISMA 2014）**                                        |
| ✅ 哪个机构制定政府安全控制标准？     | **NIST（Cybersecurity Enhancement Act）**                    |
| ✅ 哪个框架用于商业安全策略自评？     | **NIST CSF（Identify → Protect → Detect → Respond → Recover）** |
| ✅ SP 800-53 vs SP 800-171 有何区别？ | 53 用于政府内部系统，171 用于 **联邦承包商**                 |
| ✅ 哪个机构负责网络威胁共享？         | **NCCIC / DHS（National Cybersecurity Protection Act）**     |

#### CISA：Cybersecurity and Infrastructure Security Agency 美国**网络安全与基础设施安全局**

成立时间2018 年，由《CISA Act》签署通过（前身为 NCCIC），隶属于DHS（Department of Homeland Security，美国国土安全部），服务对象：联邦机构，州/地方政府，私营企业（尤其是关键基础设施行业），slogan：“Defend Today, Secure Tomorrow”

✅总结：CISA 是美国网络安全“第一响应者”与战略协调者，负责整合政府与民间力量，共同守护国家关键基础设施与信息系统的安全。

##### CISA 的核心职责

| 职责模块                      | 内容说明                                                     |
| ----------------------------- | ------------------------------------------------------------ |
| 🔐 **网络安全协调**            | 统筹国家层面的防护、监测与响应机制                           |
| 📢 **情报信息共享**            | 与私营企业、州政府、联邦部门、外国伙伴共享威胁信息           |
| 🧪 **漏洞通告与补救建议**      | 发布漏洞（CVE）、补丁建议、安全配置指南                      |
| 💡 **事件响应支持**            | 提供现场调查、取证、恢复建议等应急服务                       |
| 🏭 **关键基础设施保护**        | 包括能源、电网、水利、交通、金融、电信、医疗等16个行业       |
| 📘 **制定指导标准**            | 推出如《CISA Incident Response Guide》、《MS-ISAC Alerts》等实用文档 |
| 🧑‍🏫 **网络安全培训与意识提升** | 为中小企业、州政府、承包商提供安全培训资源                   |

##### CISA 与 NIST、NSA、FBI 的区别

| 机构                      | 职责侧重                         | 所属部门          |
| ------------------------- | -------------------------------- | ----------------- |
| **CISA**                  | 战略协调、应急响应、基础设施安全 | DHS（国土安全部） |
| **NIST**                  | 标准制定、指导手册、合规模型     | 商务部            |
| **NSA**                   | 国家安全、网络情报、防御工具     | 国防部            |
| **FBI（Cyber Division）** | 网络犯罪调查、执法取证           | 司法部            |

##### CISA 实际工作成果示例

| 类别       | 示例                                                         |
| ---------- | ------------------------------------------------------------ |
| 🧠 通告     | 每周发布安全漏洞通报（如 CISA Known Exploited Vulnerabilities Catalog） |
| ⚠️ 危机响应 | 2021年SolarWinds攻击后牵头协调事件响应                       |
| 🛡️ 工具提供 | 推出免费工具如 CISA Cyber Hygiene Services、ScubaScan、CSET 工具等 |
| 📘 指南发布 | 《Incident Response Playbook》《Zero Trust Maturity Model》等 |

##### CISSP 考点提示

| 问题                    | 答案                                     |
| ----------------------- | ---------------------------------------- |
| CISA 是什么机构？       | ✅ DHS下属的国家网络安全协调机构          |
| CISA 的主要工作是什么？ | ✅ 国家基础设施保护、事件响应、威胁共享   |
| 是否负责执法？          | ❌ 不执法（执法由 FBI 负责）              |
| 是否制定法律或标准？    | ❌ 不制定强制标准（制定标准由 NIST 负责） |

**Lawyer = 法律专业人士（泛称）**，
**Attorney = 拥有执业资格、可代表客户出庭的律师（特指）**

### Intellectual Property (IP) （知识产权）

We’ll explore the laws surrounding the **four major types of intellectual property（知识产权）** : **copyrights, trademarks, patents, and trade secrets**. We’ll also discuss how these concepts specifically concern information security professionals. Many countries protect (or fail to protect) these rights in different ways, but the basic concepts ring true throughout the world.

#### **1. Copyright（版权)** & DMCA

✅**总结**：版权保护的是“创作表达”不是“创意本身”，而 DMCA 则是“数字时代版权的防护盾”，强化了加密防护、ISP豁免与在线内容合规边界

Copyright law guarantees the creators of “original works of authorship” protection against the unauthorized duplication of their work. Eight broad categories of works qualify for copyright protection:

- Literary works（包括软件代码）
- Musical works
- Dramatic works
- Choreographic/pantomime
- Visual art（图画、雕塑）
- Audio-visual content（电影、视频）
- Sound recordings（音乐文件）
- Architectural works

It’s important to note that copyright law protects only the expression inherent in computer software—that is, the actual source code. It does not protect the ideas or process behind the software.

##### 版权的归属与有效期

| 项目        | 内容                                                       |
| ----------- | ---------------------------------------------------------- |
| 🎯 定义      | 保护**原创作品的表达方式**不被他人未经授权复制、传播、改编 |
| 📦 保护对象  | 文字、音乐、图像、视频、建筑、软件代码等                   |
| 💡 不保护    | **创意本身、算法逻辑、思想或方法**                         |
| 🧑‍💻 软件场景 | 只保护**源码本身**，不保护“思路”或“流程设计”               |

There is a formal procedure to obtain a copyright that involves sending copies of the protected work along with an appropriate registration fee to the U.S. Copyright Office. However, officially registering a copyright is not a prerequisite for copyright enforcement. Indeed, the law states that the creator of a work has an automatic copyright from the instant the work is created. If you can prove in court that you were the creator of a work (perhaps by publishing it), you will be protected under copyright law. Official registration merely provides the government’s acknowledgment that they received your work on a specific date.

| 情况                        | 描述                                             |
| --------------------------- | ------------------------------------------------ |
| 🧑‍🎨 默认归属                 | **作品自动归属于创作者**（无须注册即可生效）     |
| 🏢 雇佣创作（Work for hire） | **雇主拥有版权**，如公司内部工作或合同指定作品   |
| 🕰️ 个人作品保护期            | 作者死后 **70年**                                |
| 🏢 公司/匿名作品             | 自发表日起 **95年** 或创作日起 **120年**（取短） |

Copyright ownership always defaults to the creator of a work. The exceptions to this policy are works for hire. A work is considered “for hire” when it is made for an employer during the normal course of an employee’s workday. For example, when an employee in a company’s public relations department writes a press release, the press release is considered a work for hire. A work may also be considered a work for hire when it is made as part of a written contract declaring it as such.

Current copyright law provides for a lengthy period of protection. Works by one or more authors are protected until 70 years after the death of the last surviving author. Works for hire and anonymous works are provided protection for 95 years from the date of first publication or 120 years from the date of creation, whichever is shorter.

#### **Digital Millennium Copyright Act (DMCA) 数字版权千年法案**

**DMCA 是 1998 年为适应数字化环境制定的版权法修正案**

核心目的：

- 配合 WIPO（世界知识产权组织）国际协议
- 保护数字作品的版权机制
- 平衡用户、创作者与服务提供商的法律责任

The DMCA also serves to bring U.S. copyright law into compliance with terms of two World Intellectual Property Organization (WIPO) treaties.

##### DMCA 的主要条款

| 类别                   | 内容                                           | 安全相关说明                   |
| ---------------------- | ---------------------------------------------- | ------------------------------ |
| 🛑 禁止破解版权保护机制 | 禁止绕过 DRM（数字版权管理）系统               | 如破解 DVD 加密、软件激活限制  |
| 💰 最高处罚             | 最高 **$1,000,000 罚款 + 10 年监禁（重复者）** | 严惩商业盗版、黑客破解         |
| 🧑‍🏫 教育机构豁免        | 图书馆、非营利教育使用者在合理范围内免责       | 符合“合理使用（fair use）”原则 |
| ✅ 允许创建合法备份     | 软件许可使用者可为维护、测试等用途制作备份     | 仅限授权机器、需及时删除       |

The first major provision of the DMCA is the prohibition of attempts to circumvent copyright protection mechanisms placed on a protected work by the copyright holder. This clause was designed to protect copy-prevention mechanisms placed on digital media such as compact discs (CDs) and digital video discs (DVDs). The DMCA provides for penalties of up to $1 million and 10 years in prison for repeat offenders. Nonprofit institutions such as libraries and schools are exempted from this provision.

##### DMCA 对 ISP 的免责保护（Safe Harbor 条款）

The DMCA also limits the liability of internet service providers (ISPs) when their circuits are used by criminals violating the copyright law. The DMCA recognizes that ISPs have a legal status similar to the “common carrier” status of telephone companies and does not hold them liable for the “transitory activities” of their users. To qualify for this exemption, the service provider’s activities must meet the following requirements (quoted directly from the Digital Millennium Copyright Act of 1998, U.S. Copyright Office Summary, December 1998):

- The transmission must be initiated by a person other than the provider.
- The transmission, routing, provision of connections, or copying must be carried out by an automated technical process without selection of material by the service provider.
- The service provider must not determine the recipients of the material.
- Any intermediate copies must not ordinarily be accessible to anyone other than anticipated recipients and must not be retained for longer than reasonably necessary.
- The material must be transmitted with no modification to its content.

**为避免 ISP 被牵连承担盗版行为责任，DMCA 设定以下免责条件：**

| 条件                     | 说明                       |
| ------------------------ | -------------------------- |
| 🔁 传输是由用户发起       | ISP 不主动发起请求         |
| 🤖 传输过程为自动技术过程 | 无人工干预内容选择         |
| 🎯 不选择接收人           | ISP 不能决定内容接收方     |
| 💽 缓存副本必须临时化     | 中间副本不可长期存储       |
| ✉️ 内容不被修改           | 仅传递原始内容，无变更行为 |

📌 此机制也适用于 **搜索引擎缓存、用户上传内容平台**（如 YouTube、百度网盘）

The DMCA also exempts activities of service providers related to system caching, search engines, and the storage of information on a network by individual users. However, in those cases, the service provider must take prompt action to remove copyrighted materials upon notification of the **infringement(侵权)**.

Congress also included provisions in the DMCA that allow the creation of backup copies of computer software and any maintenance, testing, or routine usage activities that require software duplication. These provisions apply only if the software is licensed for use on a particular computer, the usage is in compliance with the license agreement, and any such copies are immediately deleted when no longer required for a permitted activity.

**DMCA 通知与删除机制（Notice & Takedown）**

当服务商收到版权方通知某内容侵权后，必须：

1. **及时下架内容**
2. 通知上传者
3. 接受反通知（counter notice）并进行合法复核

Finally, the DMCA spells out the application of copyright law principles to the streaming of audio and/or video content over the internet. The DMCA states that these uses are to be treated as “eligible nonsubscription transmissions.”

##### CISSP 应试重点与实战启示

| 问题                        | 正确答案/说明                              |
| --------------------------- | ------------------------------------------ |
| DMCA 是否允许个人破解加密？ | ❌ 不允许，即使仅用于“学习目的”也属违法     |
| 软件创作的版权归谁？        | 默认归创作者，但若为雇佣创作则归公司       |
| DMCA 对 ISP 有何影响？      | 提供合理中立传输即可获得“安全港豁免”       |
| DMCA 是否允许备份？         | ✅ 只要符号授权用途，可创建临时备份副本     |
| DMCA 主要保护什么？         | 数字内容的复制、防破解机制、流媒体传输版权 |

#### 2.Trademarks (**商标**)

商标是指**用于识别产品或服务来源的文字、图形、口号、标识**等符号。

✅**总结**：商标保护的是品牌身份而非创意内容。即使未注册也有法律效力，但注册后才能真正用®符号、获得完整诉讼权与市场独占权。

Copyright laws are used to protect creative works; there is also protection for trademarks, which are words, slogans, and logos used to identify a company and its products or services.

| 保护对象       | 示例                            |
| -------------- | ------------------------------- |
| 企业名称       | Apple、Microsoft、Wyze          |
| 产品名         | iPhone、Photoshop、Nest         |
| 口号（Slogan） | "Think Different"、"Just Do It" |
| 图形标识       | Logo、品牌图形                  |

📌 商标保护的**核心目标**：避免市场混淆 + 保护品牌权益

That same business might also seek to obtain trademark protection for its company name and the names of specific products and services that it offers to its clients.

##### ™ vs ®：两个符号的区别

| 符号  | 含义                         | 是否官方注册 | 适用场景                                     |
| ----- | ---------------------------- | ------------ | -------------------------------------------- |
| **™** | **未注册商标**（正在使用中） | ❌ 否         | 表示你主张商标权，但尚未获得官方注册         |
| **®** | **注册商标**（通过 USPTO）   | ✅ 是         | 表示该商标已获得联邦法律保护，可用于诉讼维权 |

📌 即使没有注册，也拥有“普通法商标”保护权（common law rights），**只要你在市场上实际使用了该标识**。

The main objective of trademark protection is to avoid confusion in the marketplace while protecting the intellectual property rights of people and organizations. As with copyright protection, trademarks do not need to be officially registered to gain protection under the law. If you use a trademark in the course of your public activities, you are automatically protected under any relevant trademark law and can use the ™ symbol to show that you intend to protect words or slogans as trademarks. If you want official recognition of your trademark, you can register it with the **United States Patent and Trademark Office (USPTO)**.

##### 商标注册（美国）

| 步骤               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| 1️⃣ 搜索现有商标     | 通常由律师完成“**冲突检索（clearance search）**”             |
| 2️⃣ 提交注册申请     | 可注册**已在使用**的商标，或使用“**Intent to Use（ITU）**”方式注册计划中的商标 |
| 3️⃣ USPTO 审查       | 审核两点：不混淆 + 不描述性                                  |
| 4️⃣ 公示 & 异议期    | 允许他人对商标提出异议（如存在品牌冲突）                     |
| 5️⃣ 审核通过后发证书 | 可使用®标识                                                  |

📌 ITU 提交后，商标**保护日期可追溯到提交日**，但你必须在一定时间内开始商用。

This process generally requires an attorney to perform a due diligence comprehensive search for existing trademarks that might **preclude(排除)** your registration. The entire registration process can take more than a year from start to finish. Once you’ve received your registration certificate from the USPTO, you can denote your mark as a registered trademark with the ® symbol.

One major advantage of trademark registration is that you may register a trademark that you intend to use but are not necessarily already using. This type of application is called an intent to use application and conveys trademark protection as of the date of filing provided that you actually use the trademark in commerce within a certain time period. If you opt not to register your trademark with the PTO, your protection begins only when you first use the trademark.

The acceptance of a trademark application in the United States depends on these two main requirements:

- The trademark must not be confusingly similar to another trademark—you should determine this during your attorney’s due diligence search. There will be an open opposition period during which other companies may dispute your trademark application.

- The trademark should not be descriptive of the goods and services that you will offer. For example, “Mike’s Software Company” would not be a good trademark candidate because it describes the product produced by the company. The USPTO may reject an application if it considers the trademark descriptive.

**商标申请必须满足的两个条件**

| 审核标准         | 说明                   | 示例                                          |
| ---------------- | ---------------------- | --------------------------------------------- |
| 1️⃣ 不得混淆相似   | 与已有商标不能构成混淆 | 不能注册“Microsaft”来卖操作系统               |
| 2️⃣ 不得描述性命名 | 不可直接描述商品/服务  | “Mike’s Software Company” → ❌太直接，可能被拒 |

In the United States, trademarks are granted for an initial period of 10 years and can be renewed for unlimited successive 10-year periods.

**商标的保护期限**

| 初始保护 | 续期机制                   |
| -------- | -------------------------- |
| 10 年    | 可无限续期，每次续期 10 年 |

📌 前提是你仍在**积极使用商标**于商业活动中。

##### CISSP 和实务中的商标相关问题

| 场景                | 信息安全影响                                            |
| ------------------- | ------------------------------------------------------- |
| 🧑‍💼 钓鱼邮件伪造商标 | 仿冒品牌Logo/名称 → 商标侵权 + 安全威胁（需与法务联动） |
| 🌐 域名争议          | 公司商标被抢注为域名 → 可用 UDRP 仲裁保护               |
| 🛠️ 软件命名          | 开源项目、内部工具命名应避免与现有商标冲突              |
| 📃 合同审查          | SaaS 合同中常要求不得使用其商标用于宣传等               |
| 🧑‍⚖️ 商标滥用追责     | 企业可通过注册商标提起侵权诉讼，保护品牌形象            |

##### CISSP考点 & 实战总结

| 考点类型                         | 内容                                    |
| -------------------------------- | --------------------------------------- |
| 商标 vs 版权                     | 商标：用于区分品牌/产品                 |
| 版权：用于保护创作表达（如代码） |                                         |
| 是否必须注册？                   | ❌ 否，但注册可使用 ® 并享有更强法律效力 |
| “Intent to Use” 是什么？         | ✅ 允许你注册还未使用但计划使用的商标    |
| 商标是否可永久保护？             | ✅ 只要持续使用 + 按期续展               |

#### 3. Patents（**专利）**

**✅总结：专利保护的是“技术实现的独特方式”，尤其是新颖、实用、难以模仿的发明。而专利流氓的滥用提醒我们，安全和创新不能脱离合规。**

Utility patents protect the intellectual property rights of inventors. They provide a period of 20 years from the time of the invention (from the date of initial application) during which the inventor is granted exclusive rights to use the invention (whether directly or via licensing agreements). At the end of the patent exclusivity period, the invention is in the public domain available for anyone to use.

**专利是一种授予发明人或设计人**在一定时期内对其**发明创造**享有**独占使用权利**的制度。

##### 专利的两种类型

| 类型                           | 描述                     | 有效期               | 保护内容                       |
| ------------------------------ | ------------------------ | -------------------- | ------------------------------ |
| **Utility Patent（实用专利）** | 保护“**功能/方法/工艺**” | 20年（从申请日算起） | 如何工作的原理、用途、系统结构 |
| **Design Patent（外观专利）**  | 保护“**外观设计**”       | 15年（自授权日起）   | 产品的形状、图案、视觉设计     |

📌 注意：期满后，发明自动进入**公有领域（Public Domain）**，任何人都可以使用。

📌 **CISSP重点关注实用专利**，因为它们涉及系统、方法、算法、安全流程等。

Patents have three main requirements:

1. The invention must be new. Inventions are patentable only if they are original ideas.
2. The invention must be useful. It must actually work and accomplish some sort of task.
3. The invention must not be obvious. You could not, for example, obtain a patent for your idea to use a drinking cup to collect rainwater. This is an obvious solution. You might, however, be able to patent a specially designed cup that optimizes the amount of rainwater collected while minimizing evaporation.

##### 申请专利必须满足的三个条件

| 条件                                  | 说明                     | 举例                             |
| ------------------------------------- | ------------------------ | -------------------------------- |
| 1️⃣ **新颖性（Novelty）**               | 从未公开/发布/申请过     | 不能专利一个已有的防火墙算法     |
| 2️⃣ **实用性（Utility）**               | 发明能真实工作并解决问题 | 虚构概念、不可实现的模型会被驳回 |
| 3️⃣ **非显而易见性（Non-obviousness）** | 普通人“想不到”的技术突破 | 把杯子放窗外收雨水 → ❌太显然     |

In the technology field, patents have long been used to protect hardware devices and manufacturing processes. There is plenty of precedent on the side of inventors in those areas. Recent patents have also been issued covering software programs and similar mechanisms, but these patents have become somewhat controversial because many of them are viewed by the technical community as overly broad. The issuance of these broad patents led to the evolution of businesses that exist solely as patent holding companies that derive their revenue by engaging in legal action against companies that they feel infringe upon the patents held in their portfolio. These companies are known by many in the technology community under the **derogatory（贬义的）** name “**patent trolls（专利流氓）.”**

##### 专利在科技行业的应用与争议

| 应用场景          | 内容                                                         |
| ----------------- | ------------------------------------------------------------ |
| ✅ 正向用途        | 公司研发新硬件、新算法、新网络协议后可申请专利，获得独占商业权 |
| ⚠️ 争议点          | 许多**软件类专利被认为过于宽泛/模糊**，导致技术创新被阻碍    |
| 🧨 “Patent Trolls” | 指**不做产品、只靠持有专利起诉他人赚钱**的公司，被称为“专利流氓” |

##### 与信息安全的关系（实务场景）

| 场景                   | 安全管理视角                                                |
| ---------------------- | ----------------------------------------------------------- |
| 开发新加密算法         | 可申请专利以防他人抄袭、商用                                |
| 与供应商合作           | 要注意是否使用了他人的专利 → **合同中须检查授权范围**       |
| 开源项目使用第三方库   | 需确认其不含专利陷阱，否则存在法律风险                      |
| 公司部署新身份认证流程 | 若该流程含某公司专利 → 可能被追责侵权（尤其是在SaaS服务中） |

##### CISSP 考试重点

| 考点                           | 答案                                 |
| ------------------------------ | ------------------------------------ |
| 专利保护的是“表达”还是“功能”？ | ✅ 功能和结构（与版权区别）           |
| 专利是否自动生效？             | ❌ 不会，必须通过正式申请审查流程     |
| 专利到期后归谁？               | ✅ 进入公有领域，任何人可自由使用     |
| Patent Troll 是什么？          | ✅ 利用专利授权进行滥诉的非生产性公司 |
| 专利的最基本三个条件？         | ✅ 新颖性、实用性、非显而易见性       |

#### 4. Trade Secrets (商业机密)

**✅总结**：商业秘密靠你“保密”才有保护力，失了控就永远失去了。而《经济间谍法》是你最后的维权利剑，但你得证明自己值得保护。

商业秘密指的是：**没有公开、具有商业价值、被企业有意保密的知识或信息**。

Many companies have intellectual property that is absolutely critical to their business, and significant damage would result if it were disclosed to competitors and/or the publicin other words, trade secrets.

| 类型     | 示例                          |
| -------- | ----------------------------- |
| 源代码   | 微软 Windows 内核、数据库算法 |
| 工艺流程 | 可口可乐的配方、芯片制程技术  |
| 客户数据 | CRM数据库、销售报价模型       |
| 商业策略 | 投资计划、定价模型、渠道规划  |

📌 核心关键词：**保密性 + 商业价值 + 没有注册**

##### 商业秘密 vs 其他知识产权的区别

| 类型         | 是否需注册？     | 有效期                 | 保护对象                     | 失效条件                |
| ------------ | ---------------- | ---------------------- | ---------------------------- | ----------------------- |
| **商业秘密** | ❌ 无需注册       | 无限期（只要保密有效） | 保密技术、算法、资料、配方等 | **一旦泄露 → 永久失效** |
| **专利**     | ✅ 必须注册       | 20年                   | 发明的“功能和原理”           | 到期或无效判决          |
| **版权**     | ❌ 自动生效       | 作者寿命+70年          | 表达形式（如代码文本）       | 到期                    |
| **商标**     | ✅ 可注册也可使用 | 每10年可续展           | 品牌标识                     | 不再使用或无续展        |

There actually is an official process regarding trade secrets. By their nature you don’t register them with anyone; you keep them to yourself. To preserve trade secret status, you must implement adequate controls within your organization to ensure that only authorized personnel with a need to know the secrets have access to them. You must also ensure that anyone who does have this type of access is bound by a nondisclosure agreement (NDA) that prohibits them from sharing the information with others and provides penalties for violating the agreement. Consult an attorney to ensure that the agreement lasts for the maximum period permitted by law. In addition, you must take steps to demonstrate that you value and protect your intellectual property. Failure to do so may result in the loss of trade secret protection.

##### 如何保护商业秘密？

商业秘密**不是靠政府注册保护，而是靠企业“自己保护”**。

你必须采取**合理保密措施**，包括：

| 措施                      | 说明                                       |
| ------------------------- | ------------------------------------------ |
| 🔐 **最小权限访问控制**    | 仅“需要知道”的员工可访问                   |
| 📃 **签署保密协议（NDA）** | 涉及员工、第三方、供应商等                 |
| 🧩 **信息分类分级制度**    | 将核心资产标记为“保密”/“内部”并落实制度    |
| 📂 **物理/逻辑隔离措施**   | 内网隔离、加密存储、管控审计日志           |
| ⚠️ **培训与退出审查**      | 教育员工不得泄密，离职时审查设备与资料交接 |
| 📚 **文档化保护措施**      | 用于日后如遭侵权时证明“你确实有意保护了它” |

📌 如果企业未能证明其有“合理的保护行为”，即使数据被盗也可能**无法主张商业秘密权利**！

Trade secret protection is one of the best ways to protect computer software. As discussed in the previous section, patent law does not provide adequate protection for computer software products. Copyright law protects only the actual text of the source code and doesn’t prohibit others from rewriting your code in a different form and accomplishing the same objective. If you treat your source code as a trade secret, it keeps it out of the hands of your competitors in the first place. This is the technique used by large software development companies such as Microsoft to protect their core base of intellectual property.

##### Economic Espionage Act of 1996 - 《经济间谍法》EEA

美国专门立法保护商业秘密，尤其针对**国家级窃密与间谍行为**

Trade secrets are often the crown jewels of major corporations, and the U.S. government recognized the importance of protecting this type of intellectual property when Congress enacted the Economic Espionage Act of 1996. This law has these two major provisions:

- Anyone found guilty of stealing trade secrets from a U.S. corporation with the intention of benefiting a foreign government or agent may be fined up to $500,000 and imprisoned for up to 15 years.
- Anyone found guilty of stealing trade secrets under other circumstances may be fined up to $250,000 and imprisoned for up to 10 years.

| 情形                                 | 刑罚                                        |
| ------------------------------------ | ------------------------------------------- |
| 🕵️‍♂️ 为**外国政府/代理人**盗取商业秘密 | ✅ 最高罚款 **$500,000** + 最高 **15年监禁** |
| 💼 一般商业盗取行为                   | ✅ 最高罚款 **$250,000** + 最高 **10年监禁** |

The terms of the Economic Espionage Act give true teeth to the intellectual property rights of trade secret owners. Enforcing this law requires that companies take adequate steps to ensure that their trade secrets are well protected and not accidentally placed into the public domain.

##### 与信息安全实务的结合点（CISSP 应用场景）

| 场景              | 安全控制要求                                                 |
| ----------------- | ------------------------------------------------------------ |
| 公司核心代码/算法 | 物理隔离 + 源码权限管理 + 签署 NDA                           |
| 离职员工管理      | 访问撤销、笔记本检查、机密文件清除记录                       |
| 供应商合同审查    | 明确责任归属、泄密追责、第三方审计机制                       |
| 内部文档分类      | 建立“机密/内部/公开”等标签，并技术上强制应用                 |
| 打官司维权        | 企业必须提供充分证据证明**这不是你自己泄的**、你确实在“保密” |

##### CISSP 考点总结

| 考点                         | 正确理解                                        |
| ---------------------------- | ----------------------------------------------- |
| 商业秘密是否需注册？         | ❌ 不需注册，依靠内部保密措施                    |
| 商业秘密的保护有效期？       | ✅ 只要能保密，就可以**无限期保护**              |
| 是否能保护软件？             | ✅ 能，且比专利/版权更有效（只要别人没拿到源码） |
| 商业秘密一旦泄露还能保护吗？ | ❌ 不能，**一旦进入公共领域，即永久失效**        |
| EEA 是否适用商业秘密？       | ✅ 是，美国用它打击商业窃密和间谍行为            |

### Licensing Agreement（软件许可协议）

✅**总结**：理解软件授权条款有助于避免企业误触侵权或绑定不合理义务，而识别进出口控制则是信息安全合规防火墙中不可缺失的一环，尤其在数据出境与跨境产品部署中。

Security professionals should also be familiar with the legal issues surrounding software licensing agreements. 

软件授权的方式，决定了使用者与软件提供方之间的**权责边界**，不同类型有不同的法律效力和风险。

Four common types of license agreements are in use today:

- **Contractual license agreements** use a written contract between the software vendor and the customer, outlining the responsibilities of each. These agreements are commonly found for high-priced and/or highly specialized software packages.
- **Shrink-wrap license agreements** are written on the outside of the software packaging. They commonly include a clause stating that you acknowledge agreement to the terms of the contract simply by breaking the shrink-wrap seal on the package.
- **Click-through (also known as browser wrap) license agreement**s are becoming more commonplace than shrink-wrap agreements. In this type of agreement, the contract terms are either written on the software box or included in the software documentation. During the installation process, you are required to click a button indicating that you have read the terms of the agreement and agree to abide by them. This adds an active consent to the process, ensuring that the individual is aware of the agreement’s existence prior to installation.
- **Cloud services license agreements** take click-through agreements to the extreme. Most cloud services do not require any form of written agreement and simply flash legal terms on the screen for review. In some cases, they may provide a link to legal terms and a check box for users to confirm that they read and agree to the terms. Most users, in their excitement to access a new service, simply click their way through the agreement without reading it and may unwittingly bind their entire organization to onerous terms and conditions.

| 类型                           | 形式               | 用户是否主动同意？ | 特点/场景                                                |
| ------------------------------ | ------------------ | ------------------ | -------------------------------------------------------- |
| **Contractual License**        | 正式签署的合同     | ✅ 是               | 适用于大额企业级软件，如SAP、Oracle等                    |
| **Shrink-Wrap License**        | 包装封条文字       | ❌ 默认同意         | 老派盒装软件，如光盘软件（已较少见）                     |
| **Click-Through（Clickwrap）** | 安装时点击“我同意” | ✅ 是               | 最常见的软件安装协议方式，具有较强法律效力               |
| **Cloud Service License**      | 网页服务+快速同意  | ⚠️ 弱同意（常忽略） | 云产品（如SaaS）使用者常跳过阅读，可能无意间接受苛刻条款 |

📌 **安全关注点**：

- “Click = 签字”，**点击确认具有法律约束力**
- 云服务条款常授予服务商**广泛访问/数据处理权**
- 企业用户往往**无意识绑定整个组织的法律义务**

### Import/Export Controls（技术进出口管制）

美国政府对涉及国家安全和军事用途的技术产品设有出口管制，信息安全产品也在监管范围内，尤其涉及加密、监控、系统控制等领域。

The federal government recognizes that the very same computers and encryption technologies that drive the internet and ecommerce can be extremely powerful tools in the hands of a military force. For this reason, during the Cold War, the government developed a complex set of regulations governing the export of sensitive hardware and software products to other nations. The regulations include the management of transborder data flow of new technologies, intellectual property, and personally identifying information.

Until recently, it was difficult to export high-powered computers outside the United States, except to a select handful of allied nations. The controls on exporting encryption software were even more severe, rendering it virtually impossible to export any encryption technology outside the country. Recent changes in federal policy have relaxed these restrictions and provided for more open commerce.

##### 主要监管框架

| 法规                         | 管理范围                                           | 执行机构                 | 相关清单            |
| ---------------------------- | -------------------------------------------------- | ------------------------ | ------------------- |
| **ITAR**（国际武器贸易条例） | 军事用途产品及其技术信息                           | 国务院                   | USML（军需品清单）  |
| **EAR**（出口管理条例）      | 商业用途但具有潜在军用价值的技术，包括信息安全产品 | **商务部 BIS（工业安全局）** | CCL（商业控制清单） |

Two sets of federal regulations governing imports and exports are of particular interest to cybersecurity professionals:

- **International Traffic in Arms Regulations (ITAR)** controls the export of items that are specifically designated as military and defense items, including technical information related to those items. The items covered under ITAR appear on a list called the United States Munitions List (USML), maintained in 22 CFR 121.
- **Export Administration Regulations (EAR)** cover a broader set of items that are designed for commercial use but may have military applications. Items covered by EAR appear on the Commerce Control List (CCL) maintained by the U.S. Department of Commerce. Notably, EAR includes an entire category covering information security products.

📌 **信息安全类产品如加密软件、VPN、审计工具、访问控制系统等都在 EAR 下进行监管。**

#### Countries of Concern（出口国家限制）

Currently, U.S. firms can export high-performance computing systems to virtually any country without receiving prior approval from the government. There are exceptions to this rule for countries designated by the Department of Commerce’s **Bureau of Industry and Security (BIS)** as countries of concern based on the fact that they pose a threat of nuclear proliferation, they are classified as state sponsors of terrorism, or other concerns. These countries include North Korea, Sudan, and Syria.

- 被 BIS 指定为高风险国家，不可自由出口
- 原因可能包括：核扩散、恐怖主义支持、恶意国家行为等
- 常见国家：**朝鲜（North Korea）、苏丹、叙利亚** 等

#### Encryption Export Controls（加密产品出口控制）

The Department of Commerce’s **Bureau of Industry and Security (BIS)** sets forth regulations on the export of encryption products outside the United States. Under previous regulations, it was virtually impossible to export even relatively low-grade encryption technology outside the United States. This placed U.S. software manufacturers at a great competitive disadvantage to foreign firms that faced no similar regulations. After a lengthy lobbying campaign by the software industry, the president directed the Commerce Department to revise its regulations to foster the growth of the American security software industry.

| 历史                                       | 当前规定                                                     |
| ------------------------------------------ | ------------------------------------------------------------ |
| 曾严禁任何加密技术出口，连40-bit加密都不行 | 现在划分为“**零售/大众市场产品**”类别，可在提交30天审查后自由出口 |
| 美国软件公司曾处于国际竞争劣势             | 政策已放宽，但**流程复杂，审批仍可能延误**                   |

📌 **如出口含有加密功能的软件，应申报分类、审查、获得许可再出口。**

Note：If you’re thinking to yourself, “These regulations are confusing and overlapping,” you’re not alone! Export controls are a highly specialized area of the law that require expert legal advice if you encounter them in your work.

Current regulations now designate the categories of retail and mass market security software. The rules now permit firms to submit these products for review by the Commerce Department, but the review is supposed take no longer than 30 days. After successful completion of this review, companies may freely export these products. However, government agencies often exceed legislated deadlines and companies must either wait until the review is complete or take the matter to court in an attempt to force a decision.

##### 安全/合规专家的注意事项

| 场景                 | 风险与建议                                                   |
| -------------------- | ------------------------------------------------------------ |
| 🌍 软件出海           | 若含有加密、信息收集、网络监控等模块 → 必须审查是否需报备 EAR |
| 🧑‍💻 团队使用国外 SaaS | 云服务使用需核查其出口合规政策，避免将数据传输至受限国家或触犯当地数据出境规定 |
| 📦 采购海外技术产品   | 是否为 ITAR 管制产品？是否涉及受限进口清单？是否可安全集成？ |
| 📝 需设立出口合规团队 | 制定“出口合规政策 + 产品分类识别机制 + 出口许可证管理流程”   |

##### CISSP 考点小结

| 考题方向                              | 关键点                                                       |
| ------------------------------------- | ------------------------------------------------------------ |
| Shrink-wrap 和 Click-through 的区别？ | Click-through 要求用户**主动点击同意**，具更强法律效力       |
| 什么是 EAR？                          | **Export Administration Regulations**，涵盖包括信息安全产品的商业技术出口监管法规 |
| 哪类法规适用于加密技术？              | EAR（BIS管理），已设立大众市场产品审批机制                   |
| ITAR vs EAR 区别？                    | ITAR 监管“军事用途产品”，EAR 则为“民用转军用风险产品”        |
| Cloud 服务协议是否需要特别注意？      | ✅ 是的，条款中可能包含**敏感访问权限、数据处理权利、纠纷管辖权**等高风险条款 |

## Privacy

The right to privacy has for years been a hotly contested issue in the United States. The main source of this contention is that the Constitution’s Bill of Rights does not explicitly provide for a right to privacy. However, this right has been upheld by numerous courts and is vigorously pursued by organizations such as the **American Civil Liberties Union (ACLU).**

Europeans have also long been concerned with their privacy. Indeed, countries such as Switzerland are world renowned for their ability to keep financial secrets. 

### U.S. Privacy Law

Although there is no explicit constitutional guarantee of privacy, a myriad of federal laws (many enacted in recent years) are designed to protect the private information the government maintains about citizens as well as key portions of the private sector such as financial, educational, and healthcare institutions. In the following sections, we’ll examine a number of these federal laws.

#### **Fourth Amendment** 

**美国宪法第四修正案（Fourth Amendment）** 是美国整个隐私权体系的核心基石，它限制政府在没有正当理由和令状的前提下搜查或获取公民的数据、通信与财产，是数字隐私与信息保护的重要起点。很多隐私和数据保护法规（如FISA、ECPA、GDPR中的国际互认讨论）都可追溯到它。

The basis for privacy rights is in the **Fourth Amendment** to the **U.S. Constitution**. It reads as follows:

**解读：**

>  The right of the people to be secure in their persons, houses, papers, and effects, 

**人民有权保障自己的人身、住所、文件和财产的安全** 这部分是**隐私权的核心表述**：政府不得随意侵入你的身体、家、纸质文件或个人物品。

>  against unreasonable searches and seizures, shall not be violated, 

**不应遭受无理搜查与扣押**
关键词是：**Unreasonable（无理/不当）**。
这意味着：**政府在没有合法理由的情况下，不能搜你家、看你文件、没收你的电脑或数据。**

>  and no warrants shall issue, but upon probable cause, 

**除非有合理理由（Probable Cause），否则不得签发搜查令**

搜索必须基于**事实性依据**（而非臆测），如：

- 有线索证明你涉嫌某犯罪
- 有证人指认
- 有调查得到的证据

> supported by oath or affirmation, and particularly describing the place to be searched, and the persons or things to be seized.

**搜索令必须由宣誓支持，明确指出要搜索的地点与目标**

这是对 **“范围和对象的限制”** 的要求：

- 搜查范围不能“笼统”或“随意扩大”

- 不能借“找毒品”为由乱查你的邮件/云数据

The direct interpretation of this amendment prohibits government agents from searching private property without a warrant and probable cause. The courts have expanded their interpretation of the Fourth Amendment to include protections against wiretapping and other invasions of privacy.

##### 这与现代信息安全/隐私有什么关系？

| 关联点                                 | 安全/隐私实务影响                                            |
| -------------------------------------- | ------------------------------------------------------------ |
| 📱 手机、云端是否受保护？               | 是的，很多案例（如 **Riley v. California** ）确认 **数字设备也属个人财产** ，受第四修正案保护 |
| 🕵️‍♂️ 国家监控（如 PRISM 项目）是否合法？ | 若无法院令状或超出授权 → ⚠️ 可能侵犯第四修正案                |
| 🔍 公司是否可以搜索员工资料？           | 公私领域有别 → 政府限制更严，私营组织需根据合同、隐私政策与合理期望决定边界 |
| 🛡️ 法律授权是否足够？                   | 数据访问/取证前必须依据 **正当理由 + 令状 + 限定范围** ，尤其对执法机关而言 |

虽然第四修正案本身**没有写出“privacy”这个词** ，但它为隐私权提供了 **宪法级别的间接支撑** ，尤其是：

- 数据主权权利（Data Sovereignty）
- 不被无理由监控的权利（Right to be left alone）
- 合法搜查需授权、有限范围

美国最高法院也多次通过判例 **解释它涵盖“合理隐私期待”（reasonable expectation of privacy）**。

##### 美国隐私法关键事件时间轴总览图

| 年份     | 法律/事件              | 关键词/重点内容                                     |
| -------- | ---------------------- | --------------------------------------------------- |
| **1974** | Privacy Act            | 📌 政府部门如何管理公民数据；仅适用于 **联邦机构**    |
| **1974** | FERPA                  | 📘 教育机构管理学生记录；家长/学生有查阅和更正权     |
| **1986** | ECPA                   | 🔐 禁止非法监听电子通信；扩展原“物理线路”法规        |
| **1994** | CALEA                  | ☎️ 要求运营商提供 **可被监听的技术** 接口              |
| **1996** | HIPAA                  | 🏥 医疗信息隐私与安全；保护 PHI（受保护健康信息）    |
| **1996** | Economic Espionage Act | 🏢 商业秘密盗窃刑事化；定义经济信息为“财产”          |
| **1998** | COPPA                  | 👶 保护13岁以下儿童隐私；需可验证父母同意            |
| **1998** | Identity Theft Act     | 🧑‍💳 身份盗用犯罪化；直接保护被冒用者                 |
| **1999** | GLBA                   | 🏦 金融数据隐私；隐私政策披露，控制数据共享          |
| **2002** | CA SB 1386             | 📣 美国首个数据泄露通知法；适用于加州                |
| **2009** | HITECH                 | ⚠️ 医疗泄露报告机制；HIPAA 补充，500人以上需通报媒体 |
| **2018** | CCPA（加州）           | 🌐 加州版“GDPR”；知情、删除、拒售权利赋予消费者      |
| **2023** | CPRA（加州）           | 🔒 扩展 CCPA，新增“敏感信息”类别与监管机构           |

The Privacy Act of 1974 is perhaps the most significant piece of privacy legislation restricting the way the federal government may deal with private information about individual citizens. It severely limits the ability of federal government agencies to disclose private information to other people or agencies without the prior written consent of the affected individuals. It does provide for exceptions involving the census, law enforcement, the National Archives, health and safety, and court orders.

**Privacy Act of 1974**  mandates that agencies maintain only the records that are necessary for conducting their business and that they destroy those records when they are no longer needed for a legitimate function of government. It provides a formal procedure for individuals to gain access to records the government maintains about them and to request that incorrect records be amended. 

Note: The Privacy Act of 1974 applies only to government agencies. Many people misunderstand this law and believe that it applies to how companies and other organizations handle sensitive personal information, but that is not the case.

**Electronic Communications Privacy Act of 1986 (ECPA)**  makes it a crime to invade the electronic privacy of an individual. This act broadened the Federal Wiretap Act, which previously covered communications traveling via a physical wire, to apply to any illegal interception of electronic communications or to the intentional, unauthorized access of electronically stored data. It prohibits the interception or disclosure of electronic communication and defines those situations in which disclosure is legal. It protects against the monitoring of email and voicemail communications and prevents providers of those services from making unauthorized disclosures of their content.

One of the most notable provisions of the **ECPA** is that it makes it illegal to monitor mobile telephone conversations. In fact, such monitoring is punishable by a fine of up to $500 and a prison term of up to five years.

**Communications Assistance for Law Enforcement Act (CALEA) of 1994** amended the ECPA 1986. CALEA requires all communications carriers to make wiretaps possible for law enforcement with an appropriate court order, regardless of the technology in use.

**Economic Espionage Act of 1996 (商业间谍法)** extends the definition of property to include proprietary economic information so that the theft of this information can be considered industrial or corporate espionage. This changed the legal definition of theft so that it was no longer restricted by physical constraints.

**Health Insurance Portability and Accountability Act of 1996 (HIPPA)** made numerous changes to the laws governing health insurance and health maintenance organizations (HMOs). Among the provisions of HIPAA are privacy and security regulations requiring strict security measures for hospitals, physicians, insurance companies, and other organizations that process or store private medical information about individuals.

HIPAA also clearly defines the rights of individuals who are the subject of medical records and requires organizations that maintain such records to disclose these rights in writing.

**Health Information Technology for Economic and Clinical Health Act of 2009 (HITECH)**  In 2009, Congress amended HIPAA by passing HITECH Act. This law updated many of HIPAA’s privacy and security requirements and was implemented through the HIPAA Omnibus Rule in 2013.

HITECH also introduced new data breach notification requirements. Under the **HITECH Breach Notification Rule** , HIPAA-covered entities that experience a data breach must notify affected individuals of the breach and must also notify both the secretary of health and human services and the media when the breach affects more than 500 individuals.

**In 2002, California passed SB 1386** and became the first state to immediately disclose to individuals the known or suspected breach of personally identifiable information.

This includes unencrypted copies of a person’s name in conjunction with any of the following information:

■✓ Social Security number

■✓ Driver’s license number

■✓ State identification card number

■✓ Credit or debit card number

■✓ Bank account number in conjunction with the security code, access code, or password that would permit access to the account

■✓ Medical records

■✓ Health insurance information

In the years following SB 1386, other states passed similar laws modeled on the California data breach notification law. In 2018, 16 years after the passage of SB 1386, Alabama and South Dakota became the last two states to pass data breach notification laws.

**Children’s Online Privacy Protection Act of 1998 (COPPA)** In April 2000, provisions of the Children’s Online Privacy Protection Act (COPPA) became the law of the land in the United States. COPPA makes a series of demands on websites that cater to children or knowingly collect information from children.

■✓ Websites must have a privacy notice that clearly states the types of information they collect and what it’s used for, including whether any information is disclosed to third parties. The privacy notice must also include contact information for the operators of the site.

■✓ Parents must be provided with the opportunity to review any information collected from their children and permanently delete it from the site’s records.

■✓ Parents must give verifiable consent to the collection of information about children younger than the age of 13 prior to any such collection. Exceptions in the law allow websites to collect minimal information solely for the purpose of obtaining such parental consent.

**Gramm–Leach–Bliley Act of 1999（GLBA 1999）** Until the GLBA became law in 1999, there were strict governmental barriers between financial institutions. Banks, insurance companies, and credit providers were severely limited in the services they could provide and the information they could share with each other. GLBA somewhat relaxed the regulations concerning the services each organization could provide. When Congress passed this law, it realized that this increased latitude could have far-reaching privacy implications. Because of this concern, it included a number of limitations on the types of information that could be exchanged even among subsidiaries of the same corporation and required financial institutions to provide written privacy policies to all their customers.

##### **USA PATRIOT Act of 2001** 

Congress passed the Uniting and Strengthening America by **Providing Appropriate Tools Required to Intercept and Obstruct Terrorism (USA PATRIOT) Act of 2001**  in direct response to the September 11, 2001, terrorist attacks in New York City and Washington, DC. The PATRIOT Act greatly broadened the powers of law enforcement organizations and intelligence agencies across a number of areas, including when **monitoring electronic communications.**

One of the major changes prompted by the PATRIOT Act revolves around the way government agencies obtain wiretapping authorizations. Previously, police could obtain warrants for only one circuit at a time, after proving that the circuit was used by someone subject to monitoring. Provisions of the PATRIOT Act allow authorities to obtain a blanket authorization for a person and then monitor all communications to or from that person under the single warrant.

Another major change is in the way the government deals with internet service providers (ISPs). Under the terms of the PATRIOT Act, ISPs may voluntarily provide the government with a large range of information. The PATRIOT Act also allows the government to obtain detailed information on user activity through the use of a subpoena (as opposed to a wiretap).

Finally, the USA PATRIOT Act amends the Computer Fraud and Abuse Act（CFAA）to provide more severe penalties for criminal acts. The PATRIOT Act provides for jail terms of up to 20 years and once again expands the coverage of the CFAA.

The PATRIOT Act has a complex legislative history. Many of the key provisions of the PATRIOT Act expired in 2015 when Congress failed to pass a renewal bill. However, Congress later passed the **USA Freedom Act** in June 2015, which restored key provisions of the PATRIOT Act. The provisions expired again in March 2020 and, as of the time this book went to press, had not yet been renewed. The future status of PATRIOT Act surveillance is now in doubt.

##### PATRIOT Act vs. USA Freedom Act 权限变化对比表

| 比较维度                   | PATRIOT Act（2001）                                      | USA Freedom Act（2015）                                      |
| -------------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| 📡 **大规模数据收集权**     | **允许**政府大规模收集电话元数据（如电话号码、通话时间） | ❌ **禁止**政府大规模元数据收集，转由**电信公司保留**，政府需通过法院逐案索取 |
| 🔍 **搜查令种类**           | 可申请 **“通用搜查令”**（一份令状监控某人所有通信）       | 保留，但要求**更高的证明标准**和**更清晰的目标限制**         |
| 🕵️ **国家安全信函（NSLs）** | 扩大使用范围，且默认**附带保密令**，禁止披露             | 要求 DOJ 定期审查保密令，并为 NSL 被告人设立更多申诉权       |
| ⚖️ **FISA 法院审查机制**    | 审理过程不透明，公众无从知晓                             | 要求建立 **“公众代表”机制**（Amicus），为 FISA 审查引入反对意见与更广泛视角 |
| 🗓️ **时效性**               | 授权有效期无限延长，除非国会取消                         | **3年定期审查更新机制**，2020年再次失效未续期                |
| 🛡️ **信息共享权**           | 强化情报、执法、移民、金融等多部门信息共享               | 保留共享权，但附加更多合规与审查要求                         |
| 👥 **影响群体**             | 不限于恐怖嫌疑人，广泛适用于外国人/美国人                | 更强调基于具体行为的授权，限制对普通民众的无理由收集         |

PATRIOT Act 的关键监控条款在 2015 年曾失效、随后以 Freedom Act 形式部分恢复，又于 2020 年再次失效——目前其未来命运不确定，是否恢复、修改或废除仍待国会决定。

| 时间点 | 事件                                          | 影响                                           |
| ------ | --------------------------------------------- | ---------------------------------------------- |
| 🗓️ 2001 | 爱国者法案通过                                | 扩大执法监控权，特别是数字通信领域             |
| 🗓️ 2015 | 多条款**到期** → 后续通过 **USA Freedom Act** | 恢复部分条款，强化对政府监控行为的限制与透明度 |
| 🗓️ 2020 | 条款再次**过期**                              | 当前处于“无明确授权”的状态；是否延续取决于立法 |

安全与隐私实务提示（基于当前状态）

| 场景               | 实务建议                                                     |
| ------------------ | ------------------------------------------------------------ |
| ☁️ SaaS/云数据存储  | 必须意识到 **政府可能可要求服务商交出数据**，特别是涉及国家安全调查 |
| 📞 电子通信记录     | 通话记录、登录 IP、时间戳信息等属于元数据，在某些条件下可能被政府请求 |
| 🧾 公司日志保留策略 | 须设立清晰的保留策略 + 合法响应审查流程（如 ECPA、FISA）     |
| ⚖️ 被调查通知权     | PATRIOT Act 某些条款允许**秘密调查**，被调查人无权知晓       |
| 🛡️ 个人用户隐私管理 | 建议采取 E2E 加密、零知识存储策略，以降低不可控暴露风险      |

**PATRIOT Act 强化了政府反恐监控能力，USA Freedom Act 尝试在保留国家安全工具的同时，加入更多**“隐私保护机制”**与审查制衡。随着条款陆续失效，未来趋势将取决于立法与公众舆论走向。**

**Family Educational Rights and Privacy Act (FERPA)** is another specialized privacy bill that affects any educational institution that accepts any form of funding from the federal government (the vast majority of schools). It grants certain privacy rights to students older than 18 and the parents of minor students. Specific FERPA protections include the following:

- Parents/students have the right to inspect any educational records maintained by the institution on the student.

- Parents/students have the right to request correction of records they think are erroneous and the right to include a statement in the records contesting anything that is not corrected.

- Schools may not release personal information from student records without written consent, except under certain circumstances.

**Identity Theft and Assumption Deterrence Act** In 1998, the president signed the Identity Theft and Assumption Deterrence Act into law. In the past, the only legal victims of identity theft were the creditors who were defrauded. This act makes identity theft a crime against the person whose identity was stolen and provides severe criminal penalties (up to a 15-year prison term and/or a $250,000 fine) for anyone found guilty of violating this law.

##### 隐私与安全相关法律对比速查表（按适用行业/对象分类）

| 法律                                      | 生效时间     | 适用对象                    | 保护内容          | 备注/重点                                       |
| ----------------------------------------- | ------------ | --------------------------- | ----------------- | ----------------------------------------------- |
| **Privacy Act of 1974**                   | 1974         | 美国联邦政府机构            | 美国公民个人数据  | 📌 仅适用于政府部门，需获取书面同意才能披露      |
| **ECPA（1986）**                          | 1986         | 所有组织/个人               | 电子通信内容      | 📌 禁止非法监听/访问电子数据，如邮箱、语音信箱等 |
| **CALEA（1994）**                         | 1994         | 电信运营商                  | 合法监听支持      | 📌 要求技术支持政府监听，前提是法院授权          |
| **HIPAA（1996）**                         | 1996         | 医疗行业（医院/保险公司等） | 医疗信息、PHI     | 📌 强制隐私政策，控制访问和披露医疗记录          |
| **HITECH（2009）**                        | 2009         | HIPAA 补充                  | 数据泄露报告义务  | 📌 500人以上需报告给政府和媒体                   |
| **GLBA（1999）**                          | 1999         | 金融机构                    | 财务、信用信息    | 📌 要求隐私政策通知，限制金融数据共享            |
| **FERPA**                                 | 1974         | 所有接受联邦资助的学校      | 学生记录          | 📌 学生可查阅/更正记录，发布需家长/本人同意      |
| **COPPA（2000）**                         | 1998/2000    | 针对儿童的网站/平台         | 13岁以下儿童信息  | 📌 收集前需“可验证的父母同意”，允许家长删除信息  |
| **Identity Theft Deterrence Act（1998）** | 1998         | 所有组织                    | 身份信息（SSN等） | 📌 身份盗用成为针对个人的犯罪，处罚最高15年      |
| **SB 1386（加州）**                       | 2002         | 商业实体                    | 数据泄露信息通知  | 📌 美国首个强制泄露通知法规，后来被各州效仿      |
| **CCPA / CPRA（加州）**                   | 2020 / 2023  | 针对加州居民的企业          | 个人信息广泛权利  | 📌 类似GDPR，赋予知情、删除、拒售等权利          |
| **DPD（欧盟）**                           | 1995（已废） | 欧盟机构及关联企业          | 个人信息基本权利  | 📌 构成GDPR基础，但执行分散                      |
| **GDPR（欧盟）**                          | 2018         | 所有处理欧盟居民数据的组织  | 全面个人隐私权    | 📌 全球最严，适用广，最高罚4%全球营收            |
| **PIPEDA（加拿大）**                      | 2001         | 商业组织                    | 可识别的个人信息  | 📌 部分省有等同法规替代（AB、BC、QC）            |

##### 记忆/考点技巧速览（CISSP备考实用）

| 类型                 | 法律                   | 高频考点                                        |
| -------------------- | ---------------------- | ----------------------------------------------- |
| 政府对公民的隐私义务 | **Privacy Act 1974**   | 仅适用于政府机构 + 必须合法目的保存/销毁        |
| 通信隐私             | **ECPA / CALEA**       | ECPA 禁监听，CALEA 强制技术配合监听（法院授权） |
| 医疗隐私             | **HIPAA / HITECH**     | 明确 PHI 定义 + 报告机制（500人以上需公告）     |
| 金融隐私             | **GLBA**               | 隐私政策通知 + 金融数据共享控制                 |
| 教育隐私             | **FERPA**              | 查阅/更正权 + 家长同意义务                      |
| 儿童隐私             | **COPPA**              | 13岁以下需父母同意 + 可删除权限                 |
| 身份保护             | **Identity Theft Act** | 把“身份盗用”定义为刑事犯罪（个人权利）          |
| 数据泄露             | **SB 1386 / 全美州法** | 数据泄露通知义务先从加州开始，2020年全美覆盖    |
| 欧盟数据保护         | **GDPR**               | 七大原则 + 可跨境约束非欧盟企业                 |
| 加拿大法规           | **PIPEDA**             | 商业用途限制 + 明确例外条款（匿名、职务信息等） |

### European Union Privacy Law

**✅总结：** 欧盟GDPR代表全球最严格隐私法规，强调用户权利与企业责任；美国则以行业/州分散监管为主；加拿大强调可识别信息的商业用途管控；亚太倡导跨境兼容性。

The European Union (EU) has served as a leading force in the world of information privacy, passing a series of regulations designed to protect individual privacy rights. These laws function in a comprehensive manner, applying to almost all individually identifiable information, unlike U.S. privacy laws, which generally apply to specific industries or categories of information.

#### European Union Data Protection Directive (DPD) 1995

- 欧盟最早的隐私法规，确立了数据处理必须满足的**合法依据**（如：同意、合同、法律义务等）
- 强调**个人数据访问、更正、知情和拒绝处理权**
- 为跨境数据流设定了**等效保护要求**

📌 虽然具有指导力，但作为“**指令（Directive）**”形式，成员国可以自行解释与本地立法，因此执行不统一。

On October 24, 1995, the European Parliament passed a sweeping Data Protection Directive (DPD) outlining privacy measures that must be in place for protecting personal data processed by information systems. The directive went into effect three years later in October 1998, serving as the first broad-based privacy law in the world. The DPD required that all processing of personal data meet one of the following criteria:

- Consent
- Contract
- Legal obligation
- Vital interest of the data subject
- Balance between the interests of the data holder and the interests of the data subject

The directive also outlined key rights of individuals about whom data is held and/or processed:

■✓ Right to access the data

■✓ Right to know the data’s source

■✓ Right to correct inaccurate data

■✓ Right to withhold consent to process data in some situations

■✓ Right of legal action should these rights be violated

The passing of the DPD forced organizations around the world, even those based outside Europe, to consider their privacy obligations due to transborder data flow requirements. In cases where personal information about European Union citizens left the EU, those sending the data were required to ensure that it remained protected.

#### European Union General Data Protection Regulation（GDPR）2018

- 替代 DPD，成为具有直接法律效力的“**规章（Regulation）**”
- 目标是：**统一欧盟范围内的数据保护标准**
- 适用范围广泛：即便组织不在欧盟，只要处理欧盟居民数据也受约束

The European Union passed a new, comprehensive law covering the protection of personal information in 2016. The General Data Protection Regulation (GDPR) went into effect in 2018 and replaced the DPD on that date. The main purpose of this law is to provide a single, harmonized law that covers data throughout the European Union, bolstering the personal privacy protections originally provided by the DPD.

A major difference between the GDPR and the data protection directive is the widened scope of the regulation. The new law applies to all organizations that collect data from EU residents or process that information on behalf of someone who collects it. Importantly, the law even applies to organizations that are not based in the EU, if they collect information about EU residents. Depending on how this is interpreted by the courts, it may have the effect of becoming an international law because of its wide scope. The ability of the EU to enforce this law globally remains an open question.

The key provisions of the GDPR include the following:

1. **Lawfulness, fairness, and transparency** says that you must have a legal basis for processing personal information, you must not process data in a manner that is misleading or detrimental to data subjects, and you must be open and honest about data processing activities.

2. **Purpose limitation** says that you must clearly document and disclose the purposes for which you collect data and limit your activity to disclosed purposes.

3. **Data minimization** says that you must ensure that the data you process is adequate for your stated purpose and limited to what you actually need for that purpose.

4. **Accuracy** says that the data you collect, create, or maintain is correct and not misleading, that you maintain updated records, and that you correct or erase inaccurate data.

5. **Storage limitation** says that you keep data only for as long as it is needed to fulfill a legitimate, disclosed purpose and that you comply with the “right to be forgotten” that allows people to require companies to delete their information if it is no longer needed

6. **Security** says that you must have appropriate integrity and confidentiality controls in place to protect data.

7. **Accountability** says that you must take responsibility for actions you take with protected data and that you must be able to demonstrate your compliance.

| 原则                       | 含义                                        |
| -------------------------- | ------------------------------------------- |
| **合法性、公平性、透明度** | 数据处理必须有明确合法依据，不能误导用户    |
| **目的限定**               | 只能按事先声明目的使用数据                  |
| **数据最小化**             | 收集/使用的数据应限于必要最小值             |
| **准确性**                 | 必须保持数据更新、真实，错误信息应更正/删除 |
| **存储期限限制**           | 不得无限保留数据，用户有“被遗忘权”          |
| **安全性**                 | 实施适当的保密性与完整性控制                |
| **可问责性**               | 控制者需证明自身合规责任履行情况            |

#### Cross-Border Information Sharing（GDPR 的跨境传输要求）

GDPR is of particular concern when transferring information across international borders. Organizations needing to conduct transfers between their subsidiaries have two options available for complying with EU regulations:

-  Organizations may adopt a set of standard contractual clauses that have been approved for use in situations where information is being transferred outside of the EU. 

- Organizations may adopt binding corporate rules that regulate data transfers between internal units of the same firm. This is a very time-consuming process—the rules must be approved by every EU member nation where they will be used, so typically this path is only adopted by very large organizations.

| 方法                           | 说明                                                 |
| ------------------------------ | ---------------------------------------------------- |
| ✅ **标准合同条款（SCCs）**     | 欧盟批准的标准化数据保护协议                         |
| ✅ **绑定性公司规则（BCRs）**   | 多国公司内部跨境传输用，审批复杂                     |
| ❌ **Privacy Shield**（已作废） | 曾为美欧数据流动机制，被 Schrems II 判决废除（2020） |

In the past the European Union and the United States operated a safe harbor agreement called Privacy Shield. Organizations were able to certify their compliance with privacy practices through independent assessors and, if awarded the privacy shield, were permitted to transfer information.

However, a 2020 ruling by the European Court of Justice in a case called Schrems II declared the EU/US Privacy Shield invalid. Currently, companies may not rely on the Privacy Shield and must use either standard contractual clauses or binding corporate rules. This may change in the future if the Privacy Shield is modified to meet EU requirements.

In some cases, conflicts arise between laws of different nations. For example, electronic discovery rules in the United States might require the production of evidence that is protected under GDPR. In those cases, privacy professionals should consult with attorneys to identify an appropriate course of action.

The **Asia-Pacific Economic Cooperation (APEC)** publishes a privacy framework that incorporates many standard privacy practices, such as preventing harm, notice, consent, security, and accountability. This framework is used to promote the smooth cross-border flow of information between APEC member nations.

### Canadian Privacy Law

Canadian law affects the processing of personal information related to Canadian residents. Chief among these, the **Personal Information Protection and Electronic Documents Act (PIPEDA)** is a national-level law that restricts how commercial businesses may collect, use, and disclose personal information.

| 项目         | 内容                                                         |
| ------------ | ------------------------------------------------------------ |
| 📜 全称       | **Personal Information Protection and Electronic Documents Act** |
| 📌 适用       | 商业组织处理“可识别个人信息”                                 |
| ✅ 覆盖信息   | 种族、健康、财务、DNA、雇佣历史、员工记录等                  |
| 🚫 排除信息   | 企业信息、匿名数据、公共服务职员职位、商业联系方式（用于业务沟通） |
| ⚖️ 省级替代法 | 阿尔伯塔、BC、魁北克省有“实质等同法”可替代 PIPEDA            |

📌 PIPEDA 对标 GDPR，但偏重于**商业场景、个人控制权和合理同意机制**。

Generally speaking, PIPEDA covers information about an individual that is identifiable to that individual. The Canadian government provides the following examples of information covered by PIPEDA:

■✓ Race, national, or ethnic origin

■✓ Religion

■✓ Age

■✓ Marital status

■✓ Medical, education, or employment history

■✓ Financial information

■✓ DNA

■✓ Identifying numbers

■✓ Employee performance records

The law excludes information that does not fit the definition of personal information, including the following examples provided by the Information Commissioner of Canada:

Information that is not about an individual, because the connection with a person is too weak or far-removed

■✓ Information about an organization such as a business

■✓ Information that has been rendered anonymous, as long as it is not possible to link that data back to an identifiable person

■✓ Certain information about public servants such as their name, position, and title

■✓ A person’s business contact information that an organization collects, uses, or discloses for the sole purpose of communicating with that person in relation to their employment, business, or profession

PIPEDA may also be superseded by province-specific laws that are deemed substantially similar to PIPEDA. These laws currently exist in Alberta, British Columbia, and Quebec. PIPEDA generally does not apply to nonprofit organizations, municipalities, universities, schools, and hospitals.

## State Privacy Laws

In addition to the federal and international laws affecting the privacy and security of information, organizations must be aware of the laws passed by states, provinces, and other jurisdictions where they do business. As with the data breach notification laws discussed earlier in this chapter, states often lead the way in creating privacy regulations that spread across the country and may eventually serve as the model for federal law.

##### 美国隐私法律的分裂式监管模型

美国无统一联邦隐私法，而是按“**行业+州**”方式：

| 类别 | 法律  | 说明                     |
| ---- | ----- | ------------------------ |
| 金融 | GLBA  | 银行与金融信息保护法     |
| 医疗 | HIPAA | 医疗保健信息保护         |
| 儿童 | COPPA | 保护13岁以下儿童在线信息 |
| 教育 | FERPA | 教育记录隐私权利         |

The **California Consumer Privacy Act (CCPA)** is an excellent example of this principle in action. California passed this sweeping privacy law in 2018, modeling it after the European Union’s GDPR. 

| 特点         | 内容                                                      |
| ------------ | --------------------------------------------------------- |
| 🗽 权利赋予   | 用户可知晓、删除、拒绝数据出售、避免因行使权利受歧视      |
| ⚠️ 合规成本高 | 对大型商业组织提出信息披露与响应机制要求                  |
| 📅 时间线     | CCPA 生效于 2020 年，CPRA（加强版）已于 2023 年起全面实施 |

Provisions of the law went into effect in 2020, providing consumers with the following:

■✓ The right to know what information businesses are collecting about them and how the organization uses and shares that information

■✓ The right to be forgotten, allowing consumers to request that the organization delete their personal information, in some circumstances

■✓ The right to opt out of the sale of their personal information

■✓ The right to exercise their privacy rights without fear of discrimination or retaliation for their use

| 法律               | 法律形式       | 适用范围                               | 主要特征                                     |
| ------------------ | -------------- | -------------------------------------- | -------------------------------------------- |
| **GDPR**           | 欧盟统一法案   | 所有处理欧盟居民数据的组织（含非欧盟） | 最严格、覆盖最广、处罚最重（最高4%全球营收） |
| **PIPEDA**         | 加拿大联邦法   | 商业组织                               | 明确同意机制，细化数据处理条目               |
| **CCPA/CPRA**      | 州法           | 对加州居民数据处理的公司               | GDPR式个人权利赋予，美国先行州               |
| **APEC Framework** | 非强制国际指导 | APEC 21个成员经济体                    | 更具灵活性，适合促进区域合作                 |

## Compliance

**合规（Compliance）是指：组织必须遵循的法律、法规、标准或合同义务，通常包括\**内部政策控制 + 外部监管要求**。

Over the past decade, the regulatory environment governing information security has grown increasingly complex. Organizations may find themselves subject to a wide variety of laws (many of which were outlined earlier in this chapter) and regulations imposed by regulatory agencies or contractual obligations.

合规要求来源主要包括：

| 来源       | 示例                                 |
| ---------- | ------------------------------------ |
| 📜 法律法规 | HIPAA、SOX、GDPR、FERPA 等           |
| 🏢 行业标准 | PCI DSS、ISO 27001、NIST SP800-53    |
| 📑 合同条款 | 与银行、供应商、客户签订的服务协议   |
| 🛡️ 政府监管 | 金融、医疗、能源等行业的监管机构审查 |

#### Payment Card Industry Data Security Standard (PCI DSS) 支付卡行业数据安全标准

**PCI DSS 是“契约性合规”而不是法律义务**，但其影响极大，尤其适用于所有**处理支付卡信息（CHD）的组织**。

PCI DSS is an excellent example of a compliance requirement that is not dictated by law but by contractual obligation. PCI DSS governs the security of credit card information and is enforced through the terms of a merchant agreement between a business that accepts credit cards and the bank that processes the business’s transactions.

Organizations that are not merchants but that store, process, or transmit credit card information on behalf of merchants must also comply with PCI DSS.

##### 谁必须遵守？

- **商户**（merchant）→ 接受信用卡支付的公司
- **服务提供商** → 为商户处理/存储/传输信用卡信息的第三方（如支付网关）

**PCI DSS has 12 main requirements.**

1. Install and maintain a firewall configuration to protect cardholder data.

2. Do not use vendor-supplied defaults for system passwords and other security parameters.

3. Protect stored cardholder data.
4. Encrypt transmission of cardholder data across open, public networks.
5. Protect all systems against malware and regularly update antivirus software or programs.
6. Develop and maintain secure systems and applications.
7. Restrict access to cardholder data by business need-to-know.
8. Identify and authenticate access to system components.
9. Restrict physical access to cardholder data.
10. Track and monitor all access to network resources and cardholder data.
11. Regularly test security systems and processes.
12. Maintain a policy that addresses information security for all personnel.

| 类别                     | 控制重点                                                     |
| ------------------------ | ------------------------------------------------------------ |
| **构建安全的网络与系统** | 1️⃣ 配置防火墙:<br/>2️⃣ 禁用默认密码<br/>3️⃣ 保护存储的持卡人数据<br/>4️⃣ 加密公开网络传输<br/>5️⃣ 防病毒防恶意软件<br/>6️⃣ 安全开发与漏洞管理 |
| **访问控制**             | 7️⃣ 最小权限原则<br/>8️⃣ 用户身份认证机制<br/>9️⃣ 限制物理访问（如刷卡进入机房） |
| **监控与测试**           | 🔟 日志审计与访问跟踪<br/>1️⃣1️⃣ 安全系统定期测试（如渗透测试）   |
| **整体安全治理**         | 1️⃣2️⃣ 建立全面的安全策略（包含人员培训、文档记录等）            |

Dealing with the many overlapping, and sometimes contradictory, compliance requirements facing an organization requires careful planning. Many organizations employ full-time IT compliance staff responsible for tracking the regulatory environment, monitoring controls to ensure ongoing compliance, facilitating compliance audits, and meeting the organization’s compliance reporting obligations.

##### 规职责与组织管理结构

组织常设立专门的 **IT合规团队** 或 **GRC（Governance, Risk, Compliance）办公室**，其职责包括：

- 📋 **监管政策更新与法规追踪**
- 📊 **执行内部控制检查与自评**
- 🧾 **配合内/外部审计**
- 📣 **向董事会报告合规状态**
- 📤 **提交外部报告（如 PCI 自评问卷）**

Organizations may be subject to compliance audits, either by their standard internal and external auditors or by regulators or their agents. For example, an organization’s financial auditors may conduct an IT controls audit designed to ensure that the information security controls for an organization’s financial systems are sufficient to ensure compliance with the **Sarbanes–Oxley Act (SOX).** Some regulations, such as PCI DSS, may require the organization to retain approved independent auditors to verify controls and provide a report directly to regulators.

##### 常见审计类型与机制

| 审计类型         | 发起方                     | 示例                             |
| ---------------- | -------------------------- | -------------------------------- |
| ✅ **内部审计**   | 组织自身（或内部审计部门） | SOX 合规前检查、日常控制测试     |
| ✅ **外部审计**   | 会计师事务所或第三方机构   | 年度财务审计、SOC 2 报告         |
| ✅ **合规性审计** | 监管机构或行业联盟         | PCI DSS QSA 审计、HIPAA OCR 检查 |

例如：

- **SOX 审计** 会重点关注 ERP、财务系统的访问控制、日志完整性、变更管理流程等是否受控
- **PCI DSS** 要求满足一定等级的商户需聘请 QSA（合格安全评估员）进行年度审核

In addition to formal audits, organizations often must report regulatory compliance to a number of internal and external stakeholders. For example, an organization’s board of directors (or, more commonly, that board’s audit committee) may require periodic reporting on compliance obligations and status. Similarly, PCI DSS requires organizations that are not compelled to conduct a formal third-party audit to complete and submit a self-assessment report outlining their compliance status.

##### CISSP 考点提醒与实务建议

| 考点                                   | 理解方式                                                     |
| -------------------------------------- | ------------------------------------------------------------ |
| PCI DSS 是否法律？                     | ❌ 否，它是合同义务，由**银行卡网络与发卡银行强制执行**       |
| 不涉及信用卡支付的公司是否需遵守 PCI？ | ❌ 否，但若你是数据托管/传输方也必须遵守                      |
| 什么是自评问卷（SAQ）？                | PCI DSS 要求某些商户需填写 SAQ 报告自身合规状态              |
| 合规审计 vs 内部审计                   | 合规审计通常是**面向外部/监管目标**，内部审计面向组织治理优化 |
| 合规报告对象有哪些？                   | 董事会、审计委员会、监管机构、业务合作方等                   |

✅总结：合规是组织的外部义务与内部控制能力的结合体现，CISSP 专业人员应理解合规要求、管控机制、审计流程、以及如何用安全措施满足法规。

## Contracting and Procurement

The increased use of cloud services and other external vendors to store, process, and transmit sensitive information leads organizations to a new focus on implementing security reviews and controls in their contracting and procurement processes. Security professionals should conduct reviews of the security controls put in place by vendors, both during the initial vendor selection and evaluation process and as part of ongoing vendor governance reviews.

##### 为何采购安全评估很重要？

当组织通过第三方厂商处理敏感数据时：

- 📉 安全控制权下放，风险却仍由组织承担（数据责任仍属原拥有者）
- 🧾 法规合规（如 GDPR、HIPAA）要求供应商也必须承担安全责任
- 🔄 风险不可转移，**安全责任必须通过合同/审计/评估来落实**

These are some questions to cover during these vendor governance reviews:

What types of sensitive information are stored, processed, or transmitted by the vendor?

■✓ What controls are in place to protect the organization’s information?

■✓ How is your organization’s information segregated from that of other clients?

■✓ If encryption is relied on as a security control, what encryption algorithms and key lengths are used? How is key management handled?

■✓ What types of security audits does the vendor perform, and what access does the client have to those audits?

■✓ Does the vendor rely on any other third parties to store, process, or transmit data? How do the provisions of the contract related to security extend to those third parties?

■✓ Where will data storage, processing, and transmission take place? If outside the home country of the client and/or vendor, what implications does that have?

■✓ What is the vendor’s incident response process, and when will clients be notified of a potential security breach?

■✓ What provisions are in place to ensure the ongoing integrity and availability of client data?

##### 供应商安全审查重点问题（逐项解读）

| 问题                                                | 解读与关注点                                                 |
| --------------------------------------------------- | ------------------------------------------------------------ |
| **1. 有哪些敏感信息交由供应商处理？**               | 明确数据分类与重要性，决定是否允许云处理、是否需加密         |
| **2. 供应商有哪些安全控制？**                       | 是否有访问控制、审计日志、多因子、物理/逻辑隔离、DLP等       |
| **3. 如何与其他客户的数据隔离？**                   | 公有云 / SaaS 服务中，需确保数据逻辑隔离（multi-tenancy 安全） |
| **4. 加密控制细节？算法？密钥管理？**               | AES-256是否到位？TLS版本？密钥由谁持有？有HSM吗？            |
| **5. 审计机制？我方能否获取审计报告？**             | SOC 2、ISO 27001、PCI DSS 报告是否可用？是否含红线事件披露？ |
| **6. 是否涉及 **第四方**？我方数据是否外包再外包？** | 是否会引入未经批准的子承包商？对其有安全责任传导机制吗？     |
| **7. 数据存储/处理/传输位置？是否跨境？**           | GDPR下尤为关键。跨境传输需依据 SCC、BCR 等机制合规           |
| **8. 安全事件响应机制？何时通知？**                 | 是否承诺72小时内通知？是否明确沟通窗口与应急联系人？         |
| **9. 数据完整性与可用性保障？**                     | 是否有备份机制？冗余架构？业务连续性计划？灾难恢复测试频率？ |

This is just a brief listing of some of the concerns you may have. Tailor the scope of your security review to the specific concerns of your organization, the type of service provided by the vendor, and the information that will be shared with them.

##### 合同安全条款（Contractual Clauses）常见内容

为规避风险，CISSP专业人员应协助法务团队在合同中加入如下内容：

| 合同条款                         | 说明                                               |
| -------------------------------- | -------------------------------------------------- |
| 📜 **安全责任明确化条款**         | 明确厂商承担哪些安全任务（如加密、备份、权限管理） |
| 📤 **数据访问与共享限制**         | 禁止未经授权访问或与第三方共享我方数据             |
| 🧪 **安全测试权条款**             | 保留定期安全审查、漏洞扫描、渗透测试的权利         |
| 🚨 **事件响应与通报条款**         | 指明在多长时间内必须通知我方，是否需联动应急处置   |
| 🛡️ **合规保证条款**               | 承诺符合 PCI DSS / HIPAA / GDPR / ISO 27001 等标准 |
| 🧾 **审计权与证据要求**           | 保留查看其审计报告、日志、审计链条的权利           |
| 🔚 **终止后的数据归还与销毁机制** | 明确服务终止时如何回收数据、清除副本、销毁证据     |

##### CISSP 实务建议与考试要点

| 项目                       | 建议/要点                                                   |
| -------------------------- | ----------------------------------------------------------- |
| 安全团队是否应参与采购？   | ✅ 是的，越早介入越能影响合同条款与厂商选择                  |
| 审查频率应如何设定？       | 合同签署前 + 年度复审 + 安全事件后即时审查                  |
| 应否要求对方拥有安全认证？ | ✅ 推荐至少 ISO 27001 / SOC 2 类型 II，视数据敏感性而定      |
| 应否限制数据跨境？         | ✅ 若受 GDPR 或国家/行业数据法限制，应严格控制并明列合规机制 |
| 第四方风险是否必须评估？   | ✅ 必须（尤其在供应链场景），否则存在责任空洞                |

✅**总结**：采购安全不是事后监控，而应在厂商选择、合同签署、服务交付全流程中嵌入安全控制与合规审查机制，是现代信息安全治理的关键一环。

# Summary

Computer security necessarily entails a high degree of involvement from the legal community. We learned about the laws that govern security issues such as computer crime, intellectual property, data privacy, and software licensing.

Three major categories of law impact information security professionals. **Criminal law** outlines the rules and sanctions for major violations of the public trust. **Civil law** provides us with a framework for conducting business. Government agencies use **administrative law** to promulgate the day-to-day regulations that interpret existing law.

The laws governing information security activities are diverse and cover all **three categories**. 

1. Some, such as the Electronic Communications Privacy Act and the Digital Millennium Copyright Act, are **criminal laws** where violations may result in criminal fines and/or prison time. 
2. Others, such as trademark and patent law, are **civil laws** that govern business transactions. 
3. Finally, many government agencies promulgate **administrative law**, such as the HIPAA Security Rule, that affects specific industries and data types.

Information security professionals should be aware of the compliance requirements specific to their **industry and business activities.** Tracking these requirements is a complex task and should be assigned to one or more compliance specialists who monitor changes in the law, changes in the business environment, and the intersection of those two realms.

It’s also not sufficient to simply worry about your own security and compliance. With increased adoption of cloud computing, many organizations now share sensitive and personal data with vendors that act as service providers. Security professionals must take steps to ensure that vendors treat data with as much care as the organization itself would and also meet any applicable compliance requirements.

## Exam Essentials

- **Understand the differences between criminal law, civil law, and administrative law.** Criminal law protects society against acts that violate the basic principles we believe in. Violations of criminal law are prosecuted by federal and state governments. Civil law provides the framework for the transaction of business between people and organizations. Violations of civil law are brought to the court and argued by the two affected parties. Administrative law is used by government agencies to effectively carry out their day-to-day business.

- **Be able to explain the basic provisions of the major laws designed to protect society against computer crime.**  The Computer Fraud and Abuse Act (as amended) protects computers used by the government or in interstate commerce from a variety of abuses. The Electronic Communications Privacy Act (ECPA) makes it a crime to invade the electronic privacy of an individual.
- **Know the differences among copyrights, trademarks, patents, and trade secrets.**  Copyrights protect original works of authorship, such as books, articles, poems, and songs. Trademarks are names, slogans, and logos that identify a company, product, or service. Patents provide protection to the creators of new inventions. Trade secret law protects the operating secrets of a firm.
- **Be able to explain the basic provisions of the Digital Millennium Copyright Act of 1998.** The Digital Millennium Copyright Act prohibits the circumvention of copy protection mechanisms placed in digital media and limits the liability of internet service providers for the activities of their users.
- **Know the basic provisions of the Economic Espionage Act of 1996**. The Economic Espionage Act provides penalties for individuals found guilty of the theft of trade secrets. Harsher penalties apply when the individual knows that the information will benefit a foreign government.
- **Understand the various types of software license agreements.** Contractual license agreements are written agreements between a software vendor and user. Shrink-wrap agreements are written on software packaging and take effect when a user opens the package. Click-through agreements are included in a package but require the user to accept the terms during the software installation process.
- **Understand the notification requirements placed on organizations that experience a data breach.**  California’s SB 1386 implemented the first statewide requirement to notify individuals of a breach of their personal information. All other states eventually followed suit with similar laws. Currently, federal law only requires the notification of individuals when a HIPAA-covered entity breaches their protected health information.
- **Understand the major laws that govern privacy of personal information in the United States, the European Union, and Canada.**  The United States has a number of privacy laws that affect the government’s use of information as well as the use of information by specific industries, such as financial services companies and healthcare organizations that handle sensitive information. The EU has a more comprehensive General Data Protection Regulation that governs the use and exchange of personal information. In Canada, the Personal Information Protection and Electronic Documents Act (PIPEDA) governs the use of personal information.
- **Explain the importance of a well-rounded compliance program.**  Most organizations are subject to a wide variety of legal and regulatory requirements related to information security. Building a compliance program ensures that you become and remain compliant with these often overlapping requirements.
- **Know how to incorporate security into the procurement and vendor governance process.** The expanded use of cloud services by many organizations requires added attention to conducting reviews of information security controls during the vendor selection process and as part of ongoing vendor governance.
- **Be able to determine compliance and other requirements for information protection.** Cybersecurity professionals must be able to analyze a situation and determine what jurisdictions and laws apply. They must be able to identify relevant contractual, legal, regulatory, and industry standards and interpret them for their given situation.
- **Know legal and regulatory issues and how they pertain to information security.** Understand the concepts of cybercrime and data breaches and be able to apply them in your environment when incidents arise. Understand what licensing and intellectual property protections apply to your organization’s data and your obligations when encountering data belonging to other organizations. Understand the privacy and export control issues associated with transferring information across international borders.
