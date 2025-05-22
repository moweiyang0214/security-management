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

Civil laws form the bulk of the U.S. body of laws. They are designed to provide for an orderly society and govern matters that are not crimes but that require an **impartial(公正的) arbiter(仲裁者) ** to settle between individuals and organizations.

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

























