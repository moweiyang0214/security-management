# Business Continuity Planning

- **Domain 1.0: Security and Risk Management**

- **Domain 7.0: Security Operations**

## Planning for Business Continuity

**Business continuity planning (BCP)** involves assessing the risks to organizational processes and creating policies, plans, and procedures to minimize the impact those risks might have on the organization if they were to occur. BCP is used to maintain the continuous operation of a business in the event of an emergency. The goal of BCP planners is to implement a combination of policies, procedures, and processes such that a potentially disruptive event has as little impact on the business as possible.

As long as the continuity of the organization’s ability to perform its mission-critical work tasks is maintained, BCP can be used to manage and restore the environment.

##### Business Continuity Planning vs. Disaster Recovery Planning

Both activities help prepare an organization for a disaster. They intend to keep operations running continuously, when possible, and recover functions as quickly as possible if a disruption occurs. 

The perspective difference is that

-  **business continuity activities** are typically strategically focused at a high level and center themselves on business processes and operations. 
-  **Disaster recovery plans** tend to be more tactical and describe technical activities such as recovery sites, backups, and fault tolerance.

The **overall goal of BCP** is to provide a quick, calm, and efficient response in the event of an emergency and to enhance a company’s ability to recover from a disruptive event promptly.

The BCP process has **four main steps:**

1. Project scope and planning
2. Business impact analysis
3. Continuity planning
4. Approval and implementation

### Step 1. Project Scope and Planning

Organizations should approach the planning process with **several goals** in mind:

- Perform a structured review of the business’s organization from a crisis planning point of view.
- Create a BCP team with the approval of senior management.
- Assess the resources available to participate in business continuity activities.
- Analyze the legal and regulatory landscape that governs an organization’s response to a catastrophic event.

The purpose of this phase is to ensure that the organization dedicates sufficient time and attention to both developing the project scope and plan and then documenting those activities for future reference.

#### Organizational Review

perform an analysis of the business organization to identify all departments and individuals who have a stake in the BCP process. 

#### **identification process**

- **Operational departments** that are responsible for the core services the business provides to its clients
- C**ritical support services**, such as the IT department, facilities and maintenance personnel, and other groups responsible for the upkeep of systems that support the operational departments
- **Corporate security teams** responsible for physical security, since they are many times the first responders to an incident and are also responsible for the physical safeguarding of the primary facility and alternate processing facility
- **Senior executives** and other key individuals essential for the ongoing viability of the organization

#### BCP Team Selection

Representatives from each of the organization’s departments responsible for the core services performed by the business

■✓ Business unit team members from the functional areas identified by the organizational analysis

■✓ IT subject-matter experts with technical expertise in areas covered by the BCP

■✓ Cybersecurity team members with knowledge of the BCP process

■✓ Physical security and facility management teams responsible for the physical plant

■✓ Attorneys familiar with corporate legal, regulatory, and contractual responsibilities

■✓ Human resources team members who can address staffing issues and the impact on individual employees

■✓ Public relations team members who need to conduct similar planning for how they will communicate with stakeholders and the public in the event of a disruption

■✓ Senior management representatives with the ability to set the vision, define priorities, and allocate resources

You need to strike a balance between representing different points of view and creating a team with explosive personality differences. Your goal should be to create a group that is as diverse as possible and still operates in harmony.

#### Resource Requirements 

After the team validates the organizational review, it should turn to an assessment of the resources required by the BCP effort. This assessment involves the resources needed by three distinct BCP phases:

1. **BCP Development** The BCP team will require some resources to perform the four elements of the BCP process : project scope and planning, business impact analysis, continuity planning, and approval and implementation. It’s more than likely that the major resource consumed by this BCP phase will be effort expended by members of the BCP team and the support staff they call on to assist in the development of the plan.
2. **BCP Testing, Training, and Maintenance** The testing, training, and maintenance phases of BCP will require some hardware and software commitments. Still, once again, the major commitment in this phase will be the effort of the employees involved in those activities.
3. **BCP Implementation** When a disaster strikes and the BCP team deems it necessary to conduct a full-scale implementation of the business continuity plan, the implementation will require significant resources. Those resources include a large amount of effort (BCP will likely become the focus of a large part, if not all, of the organization) as well as direct financial expenses.

**personnel** are one of the most significant resources consumed by the BCP process.

Leaders are responsible for resource utilization management. They will put your BCP proposal under a microscope, and you should prepare to defend the necessity of your plan with coherent, logical arguments that address the business case for BCP.

#### Legal and Regulatory Requirments

Developing a strong, documented business continuity plan can help your organization win new clients and additional business from existing clients. If you can show your customers the sound procedures you have in place to continue serving them in the event of a disaster, they’ll place greater confidence in your firm and might be more likely to choose you as their preferred vendor.

Laws regarding computing systems, business practices, and disaster management change frequently. They also vary from jurisdiction to jurisdiction. Be sure to keep your attorneys involved throughout the lifetime of your BCP, including the testing and maintenance phases. If you restrict their involvement to a pre-implementation review of the plan, you may not become aware of the impact that changing laws and regulations have on your corporate responsibilities.

### Step 2. Business Impact Analysis(BIA)

the heart of the work—the business impact analysis (BIA)

The BIA identifies the business processes and tasks that are critical to an organization’s ongoing viability and the threats posed to those resources. 

It also assesses the likelihood that each threat will occur and the impact those occurrences will have on the business. 

The results of the BIA provide you with quantitative measures that can help you prioritize the commitment of business continuity resources to the various local, regional, and global risk exposures facing your organization.

Risk assessment process is focused on individual **assets**, whereas the BCP focuses on **business processes** and **tasks**.

##### Type 1. Quantitative Impact Assessment

Involves the use of numbers and formulas to reach a decision. This type of data often expresses options in terms of the dollar value to the business.

##### Type 2. Qualitative Impact Assessment

Takes non-numerical factors, such as reputation, investor/customer confidence, workforce stability, and other concerns, into account. This type of data often results in categories of prioritization (such as high, medium, and low).

#### Step 2.1 Identifying Priorities

The first BIA task facing the BCP team is identifying business priorities. Depending on your line of business, certain activities are essential to your day-to-day operations when disaster strikes. You should create a comprehensive list of critical business functions and rank them in order of importance.

To begin the quantitative assessment, the BCP team should sit down and draw up a list of organization assets and then assign an **asset value (AV)** in monetary terms to each asset. These values form the basis of risk calculations performed later in the BIA.

The second quantitative measure that the team must develop is the **maximum tolerable downtime (MTD),** sometimes also known as **maximum tolerable outage (MTO).** The MTD is the maximum length of time a business function can tolerate a disruption before suffering irreparable harm.

The **recovery time objective (RTO)** for each business function is the amount of time in which you think you can feasibly recover the function in the event of a disruption.

Ensure that your RTOs are less than your MTDs, resulting in a situation in which a function should never be unavailable beyond the maximum tolerable downtime.

The **recovery point objective (RPO)** is the data loss equivalent to the time-focused RTO. The RPO defines the point in time before the incident where the organization should be able to recover data from a critical business process.

| 概念                                 | 中文名称                    | 定义                                                       | 作用                            | 举例                                 |
| ------------------------------------ | --------------------------- | ---------------------------------------------------------- | ------------------------------- | ------------------------------------ |
| **Asset Value (AV)**                 | 资产价值                    | 用货币衡量的组织资产价值                                   | 用于评估丧失该资产的经济影响    | 某客户数据库系统价值 ¥2,000,000      |
| **Maximum Tolerable Downtime (MTD)** | 最大可容忍停机时间          | **最长**可以容忍某功能中断的时间，超出将造成**不可逆损害** | 判定哪个业务最急、影响最重      | 财务系统MTD = 48小时                 |
| **Recovery Time Objective (RTO)**    | 恢复时间目标                | 计划中**可实现的**最短恢复时间                             | 设定实际操作目标，保证不超过MTD | 财务系统RTO = 12小时                 |
| **Recovery Point Objective (RPO)**   | 恢复点目标 / 数据恢复点目标 | 可容忍的数据丢失时间窗口（以**回溯点**衡量）               | 决定**数据备份频率**要求        | RPO = 4小时，表示至少每4小时备份一次 |

要求：**RTO ≤ MTD 且 RPO 足够短 → 数据 + 功能双恢复要求**

易混淆知识点区别

| 概念对比       | 区别点                                                       |
| -------------- | ------------------------------------------------------------ |
| **MTD vs RTO** | MTD 是最大可承受极限（业务角度），RTO 是计划中实际能恢复的时间（技术角度） |
| **RTO vs RPO** | RTO 是恢复“功能”时间，RPO 是恢复“数据”点时间                 |
| **AV vs MTD**  | AV 是“资产有多值钱”，MTD 是“资产能停多久”                    |

✅ **AV 衡量价值，MTD 定极限，RTO 保进度，RPO 控丢失。**

#### Step 2.2 Risk Identification

identification of risks posed to your organization. Risks come in two forms: natural risks and person-made risks. 

##### natural threats:

- Violent storms/hurricanes/tornadoes/blizzards
- Lightning strikes
- Earthquakes
- Mudslides/avalanches
- Volcanic eruptions
- Pandemics

**特点：难以预测、严重影响、周期性或突然性强**

| 威胁类别              | 说明                                 | 防御建议                                   |
| --------------------- | ------------------------------------ | ------------------------------------------ |
| 飓风/暴风雪/龙卷风    | 强风破坏建筑、供电中断               | 结构加固、防风卷帘、发电机、紧急撤离流程   |
| 雷击                  | 电力冲击，可能破坏系统硬件           | 安装避雷针、断电保护、UPS                  |
| 地震/火山/雪崩/泥石流 | 地质活动造成结构破坏、断网、交通中断 | 抗震设计、地理迁移、灾难预案               |
| 疫情/传染病           | 大规模人员停工或死亡，业务中断       | 居家办公、远程访问策略、医疗防护、隔离区域 |

##### Person-made threats:

- Terrorist acts/wars/civil unrest
- Theft/vandalism
- Fires/explosions
- Prolonged power outages
- Building collapses
- Transportation failures
- Internet disruptions
- Service provider outages
- Economic crises

| 威胁类别                  | 说明                                 | 防御建议                               |
| ------------------------- | ------------------------------------ | -------------------------------------- |
| 恐怖袭击/内乱/战争        | 目标重要资产、基础设施破坏           | 政府合作、应急撤离计划、冗余设施       |
| 偷盗/破坏/入侵            | 非法访问、数据泄露、系统篡改         | 门禁、视频监控、访问控制、报警系统     |
| 火灾/爆炸                 | 设施损坏、数据毁灭                   | 烟雾探测、自动喷淋、防火墙体、安全演练 |
| 电力中断                  | 系统宕机、数据丢失、业务停摆         | UPS、发电机、负载均衡                  |
| 建筑倒塌                  | 安全事故、人力伤亡                   | 定期检测建筑结构、合规标准维护         |
| 交通失败（物流/出行中断） | 无法及时供货、人员无法到岗           | 多仓储备、远程工作、供应商多元化       |
| 网络/服务中断             | 无法通信、系统挂起                   | 冗余ISP、云容灾、链路负载均衡          |
| 经济危机                  | 营收急降、合作断裂、无法支出安全预算 | 风险准备金、弹性预算、安全投资优先级   |

**特点：源于人类行为，部分可预测，关键在于**制度、教育、控制手段的建立

| 风险类别                | 中文名称 | 触发方式                           | 可控性                     | 常见示例                               |
| ----------------------- | -------- | ---------------------------------- | -------------------------- | -------------------------------------- |
| **Natural Threats**     | 自然威胁 | 自然环境、气候、地质等外部自然力量 | ❌ 不可控制，只能防御       | 地震、洪水、飓风、疫情、雪崩、火山     |
| **Person-made Threats** | 人为威胁 | 人类活动、行为、决策、攻击         | ✅ 可控性较高，可预防与治理 | 恐袭、火灾、盗窃、暴乱、断电、系统崩溃 |

You may want to use them as a starting point, but a full listing of risks facing your organization will require input from all members of the BCP team. The risk identification portion of the process is purely qualitative. At this point in the process, the BCP team should not be concerned about the likelihood that each type of risk will materialize or the amount of damage such an occurrence would inflict upon the continued operation of the business. The results of this analysis will drive both the qualitative and quantitative portions of the remaining BIA tasks.

SOC report. SOC 1 report, covers only internal controls over financial reporting. If you want to verify the security, privacy, and availability controls, you’ll want to review either an SOC 2 or SOC 3 report. The American Institute of Certified Public Accountants (AICPA) sets and maintains the standards surrounding these reports to mainta

| 步骤                 | 说明                                               |
| -------------------- | -------------------------------------------------- |
| 1️⃣ 资产识别           | 要保护什么？（人、数据、设备、场所、品牌）         |
| 2️⃣ 威胁识别           | 谁/什么可能带来破坏？（自然、人为）                |
| 3️⃣ 脆弱性识别         | 有哪些弱点可能被利用？（系统漏洞、地理、管理缺陷） |
| 4️⃣ 风险形成           | 风险 = 威胁 × 脆弱性 × 资产影响                    |
| 5️⃣ 风险记录（RA结果） | 作为后续控制选型与优先级依据                       |

#### Step 2.3 Likelihood Assessment

**Likelihood Assessment = 用 ARO 把“模糊的风险”变成“可比较的数字”**，为 BCP 投资与策略提供数据基础。

Identifies the likelihood that each risk will occur. We describe this likelihood using the same process used for the risk assessment in Chapter 2. 

- First, we determine the annualized rate of occurrence (ARO) that reflects the number of times a business expects to experience a given disaster each year. This annualization process simplifies comparing the magnitude of very different risks.

- **ARO – Annualized Rate of Occurrence**

  - **定义**：某种风险在**一年内预计发生的次数**
  - **数值形式**：可为整数（1次/年）或小数（0.1次/年 = 10年一次）

  📌 **ARO 用途**：配合 Asset Value（AV）和 Exposure Factor（EF）来计算 **Annualized Loss Expectancy（ALE）**

The BCP team should sit down and determine an ARO for each risk identified in the previous section. Base these numbers on corporate history, professional experience of team members, and advice from experts, such as meteorologists, seismologists, fire prevention professionals, and other consultants, as needed.

数据来源建议

| 来源             | 内容                           | 适用风险类型                      |
| ---------------- | ------------------------------ | --------------------------------- |
| **公司历史**     | 是否发生过同类事件、频率、后果 | 火灾、停电、系统宕机              |
| **行业专家意见** | 评估技术类、人为类风险         | 恶意攻击、社会事件                |
| **政府机构数据** | 官方灾害风险地图、事件统计     | 地震（USGS）、洪水（FEMA）        |
| **保险公司数据** | 各类风险的统计频率、损失均值   | 全面风险分析，特别是灾难/自然风险 |

Government resources

- the U.S. Geological Survey **(USGS)** developed the earthquake hazard map
- the Federal Emergency Management Agency **(FEMA)** coordinates the development of detailed flood maps of local communities throughout the United States. 

In addition to the government resources, **insurance companies** develop large repositories of risk information as part of their actuarial processes. You may be able to obtain this information from them to assist in your BCP efforts. After all, you have a mutual interest in preventing damage to your business!

**可能性评估流程**

| 步骤                    | 内容                                               |
| ----------------------- | -------------------------------------------------- |
| 1️⃣ 收集风险事件清单      | 来自 Step 2.2 风险识别（如：火灾、洪水、网络断链） |
| 2️⃣ 为每项风险分配 ARO    | 基于经验、历史、外部资源估算每种事件年发生频率     |
| 3️⃣ 使用 ARO 进行定量分析 | 支撑风险优先级排序、投入资源评估、保险采购策略等   |

#### Step 2.4 Impact Analysis

analyze the data gathered during risk identification and likelihood assessment and attempt to determine what impact each one of the identified risks would have on the business if it were to occur.

three specific metrics:

1. the exposure factor(EF)
2. the single loss expectancy(SLE): **SLE = AV × EF**
3. the annualized loss expectancy(ALE) : **ALE = SLE × ARO**

**总结关联公式**

**SLE（Single Loss Expectancy）** = AV × EF（资产价值 × 暴露因子）

**ARO** = 年均发生次数

**ALE** = 年均预期损失额，衡量优先防护级别！

| 问题方向                             | 关键点                                  |
| ------------------------------------ | --------------------------------------- |
| “哪个指标衡量风险发生频率？”         | **ARO**                                 |
| “用于支持风险比较的统计依据有哪些？” | 公司历史、专家建议、FEMA/USGS、保险数据 |
| “评估一年内业务受灾损失？”           | ARO × SLE = ALE                         |
| “ARO 为 0.1 表示？”                  | 每10年平均发生一次                      |

**✅总结**：**EF 是损失程度，SLE 是损失金额，ARO 是事件频率，ALE 是年均损失影响。SLE × ARO = ALE，全面量化帮助你做出科学安全投资决策。**

From a qualitative point of view, you must consider the **nonmonetary impact** that interruptions might have on your business.

- Loss of **goodwill** among your client base(客户信任丧失)
- Loss of employees to other jobs after prolonged downtime(员工流失)
- Social/ethical responsibilities to the community(社会/道德责任)
- Negative publicity(媒体负面舆情)

**定性风险影响（Qualitative Impact）**

虽然SLE和ALE能用数字说话，但BCP也必须考虑以下“**非货币损失**”，这些对企业声誉和生存同样致命：

| 非金钱影响                                                   | 示例                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| 🤝 客户信任丧失（goodwill）                                   | 系统故障后客户流失，投诉增加               |
| 👥 员工流失(Loss of employees)                                | 长时间停工导致员工跳槽或情绪崩溃           |
| 🌍 社会/道德责任(Social/ethical responsibilities to the community) | 医疗系统宕机影响病人治疗；食品厂污染未披露 |
| 📰 媒体负面舆情(Negative publicity)                           | 数据泄露被媒体曝光，股价暴跌，品牌信誉受损 |

#### Step 2.5 Resource Prioritization

✅ **总结**：资源优先化 = 用数据+常识+管理意图，共同决定先保护哪些最关键的风险点

Prioritize the allocation of business continuity resources to the various risks that you identified and assessed in earlier phases of the BIA.

This step provides you with a prioritized list of the risks that you should address. Select as many items as you’re willing and able to handle simultaneously from the top of the list and work your way down. Eventually, you’ll reach a point at which you’ve exhausted either the list of risks (unlikely!) or all your available resources (much more likely!).

You must sit down with the BCP team and representatives from the senior management team and combine the two lists into a single prioritized list.

Qualitative concerns may justify elevating or lowering the priority of risks that already exist on the ALE-sorted quantitative list. The potential loss of reputation within the business community resulting from the destruction of a fire suppression company by fire might be too challenging to overcome and result in the eventual collapse of the business, justifying the increased priority.

##### 工作流程总结

| 步骤           | 描述                                                   | 来源                  |
| -------------- | ------------------------------------------------------ | --------------------- |
| 1️⃣ 整理风险清单 | 所有已识别的风险（自然、人为）                         | Step 2.2              |
| 2️⃣ 附加概率     | 每项风险的 ARO 年频率                                  | Step 2.3              |
| 3️⃣ 附加影响     | 每项风险的 SLE/ALE                                     | Step 2.4              |
| 4️⃣ 初步排序     | 用 **ALE从高到低**排序                                 | 定量评估优先顺序      |
| 5️⃣ 战略调整     | 结合 **定性因素、声誉影响、行业道德责任** 进行排序微调 | 高层参与，调整合理性  |
| 6️⃣ 确定资源能力 | 核心问题：“我们同时能应对多少？”                       | 财务、人力、时间      |
| 7️⃣ 输出正式清单 | 前N项为**立即资源投放目标**，其余暂缓或接受            | 优化ROI、提升业务韧性 |

##### CISSP 应试要点与实战建议

| 维度           | 考点提示                                              |
| -------------- | ----------------------------------------------------- |
| 📌 数值优先     | BIA排序初步依赖 **ALE大小**                           |
| 📌 管理参与     | 最终排序必须经由高层 **确认/调整**                    |
| 📌 定性影响作用 | 声誉、伦理、员工满意度等可调整排序                    |
| 📌 资源有限性   | 最终计划只能涵盖“能力范围内的风险”                    |
| 📌 安全不是全包 | **某些风险可接受**，必须有记录和说明（residual risk） |

### Step 3 Continuity Planning

**✅ 总结：**Step 3 = 从“理论分析”走向“实际操作”的关键转折：**先定方向（策略制定），再定方案（流程设计），最终形成完整COOP计划**。

| 模块           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 📌 目标         | 将前面识别与分析的关键风险 → 转化为**实际可执行的应对方案**  |
| 📌 输出产物     | **COOP：Continuity of Operations Plan（运营持续计划）**      |
| ⏱️ 适用时间范围 | 灾难发生后开始执行，持续1小时～30天之间的“短期维稳运营方案”  |
| 📦 保护资产范围 | 三类：**人员（people）+ 设施（facilities）+ 基础设施（infra）** |

The first two phases of the BCP process (project scope and planning and the business impact analysis) focus on determining how the BCP process will work and prioritizing the business assets that you must protect against interruption.

While continuity planning focuses on developing and implementing a continuity strategy to minimize the impact realized risks might have on protected assets.

There are two primary subtasks involved in continuity planning:

- Strategy development
- Provisions and processes

The goal of this process is to create a continuity of operations plan **(COOP). **The continuity of operations plan focuses on how an organization will carry out critical business functions beginning shortly after a disruption occurs and extending for up to one month of sustained operations.

##### Step 3 阶段的输出内容会成为最终 **COOP 文档** 的主体部分：

- 谁负责？
- 在什么时间节点做什么？
- 恢复顺序？
- 联络人、清单、切换流程？

#### Step 3.1 Strategy Development (策略制定)

**定义**：连接前期分析（BIA）与后续操作（实施）的桥梁部分

**任务**：

1. 确定哪些风险需要被BCP处理

2. 明确资源投入优先级与可行性

3. 明确哪些风险接受残余风险、哪些需控制

**Strategy Development** bridges the gap between the business impact analysis(BIA) and the continuity planning phases of BCP development. 

The BCP team must now take the prioritized list of concerns raised by the quantitative and qualitative resource prioritization exercises and determine which risks will be addressed by the business continuity plan.

Fully addressing all the contingencies would require the implementation of provisions and processes that maintain a zero-downtime posture in the face of every possible.

Once the BCP team determines which risks require mitigation and the level of resources that will be committed to each mitigation task, they are ready to move on to the provisions and processes phase of continuity planning.

#### Step 3.2 Provisions and Processes (机制与流程设计)

**定义**：真正的“干活阶段”：设计每类资产应对灾难的**实际操作机制**。设计机制（程序+物理+技术）针对：People / Facilities / Infrastructure

Provision and Processes phase is the meat of the entire business continuity plan. In this task, the BCP team **designs the specific procedures** and **mechanisms** that will mitigate the risks deemed unacceptable during the strategy development stage. Three categories of assets must be protected through BCP provisions and processes: 

- people, 
- buildings/facilities,
- infrastructure. 

##### 3.2.1 People

you must ensure that the people within your organization are safe before, during, and after an emergency. **保障人的生命安全与工作延续能力**。

Once you’ve achieved that goal, you must make provisions to allow your employees to conduct both their BCP and operational tasks in as normal a manner as possible, given the circumstances.

| 时段         | 安全目标                                       |
| ------------ | ---------------------------------------------- |
| 📍 **灾难前** | 提前培训、告警通知机制、应急联系人系统         |
| ⚠️ **灾难中** | 保护员工生命安全、指引行动、紧急疏散           |
| ✅ **灾难后** | 员工心理安抚、恢复通信与远程办公、功能团队重启 |

**people are your most valuable asset. **Make sure that your business continuity plan makes adequate provisions for the security of your employees, customers, suppliers, and any other individuals who may be affected.

##### 人员保障的两大维度：

1. **生命安全（Safety）**： 首要原则：**保命优先于恢复生产**

| 安全机制           | 说明                                         |
| ------------------ | -------------------------------------------- |
| 紧急联络机制       | 更新员工电话、家庭联系人、HR系统同步         |
| 疏散演练与路线图   | 公布疏散路线、定期演练火灾/地震逃生          |
| 员工健康与医疗准备 | 提供口罩、药品、医疗协作通道（如疫情）       |
| 安全区域/集合点    | 每栋楼设定集合点，设定管理员负责确认到达情况 |

2. **运营保障（Continuity of Work）**： 在确保人安全之后，让员工**能恢复工作、继续维持关键业务运作**

| 措施           | 内容说明                                               |
| -------------- | ------------------------------------------------------ |
| 💻 远程办公策略 | VPN、云桌面、权限访问控制、安全认证机制                |
| 🧑‍💻 BCP职责分工 | 谁负责联络？谁负责评估系统？哪些员工是关键岗位？       |
| 📋 人员冗余配置 | 确保每个关键岗位至少两人备援（如IT管理员、财务签署人） |
| 🎓 BCP意识培训  | 所有员工需理解自己的应急职责，参与演练                 |
| 🛂 外部人员管理 | 对客户、供应商、现场访客也应有通知/接待机制            |

##### 考试重点

| 重点考点                         | 说明                                            |
| -------------------------------- | ----------------------------------------------- |
| 📌 人员是“最宝贵的资产”           | 所有BCP资源规划时，**人员保护优先于系统和数据** |
| 📌 BCP ≠ 仅IT恢复                 | 必须涵盖员工、客户、供应商等“人”的影响面        |
| 📌 BCP要支持员工安全 + 工作连续性 | 仅保护人命还不够，还要让他们“能工作”            |
| 📌 所有人员策略要事前规划         | 疫情、断电、封控等不能临时编制对策              |

**✅ 总结：** **人是BCP的核心第一优先项。你不仅要救他们的命，还要让他们能继续工作。**

##### 3.2.2 Buildings and Facilities

Many businesses require specialized facilities to carry out their critical operations. These might include standard office facilities, manufacturing plants, operations centers, warehouses, distribution/logistics centers, and repair/maintenance depots, among others. When you perform your BIA, you will identify those facilities that play a critical role in your organization’s continued viability. Your continuity plan should address two areas for each critical facility: 

- **Hardening Provisions（加固机制）** Your BCP should outline mechanisms and procedures that can be put in place to protect your existing facilities against the risks defined in the strategy development phase. Hardening provisions might include steps as simple as patching a leaky roof or as complex as installing reinforced hurricane shutters and fireproof walls.

  - 将设施从“易损”变为“有韧性”，提升**生存能力和业务持续性**

  - | 类别         | 具体措施举例                                               |
    | ------------ | ---------------------------------------------------------- |
    | **物理加固** | 安装防爆门、防火墙、钢化玻璃、抗震结构、屋顶修补、防洪闸门 |
    | **电力安全** | 部署UPS（不间断电源）、柴油发电机                          |
    | **环境控制** | 空调系统冗余、防火感应器、灭火装置（气体型/干粉）          |
    | **访问控制** | 门禁系统、生物识别、警卫巡逻、监控摄像头                   |
    | **运营程序** | 应急预案张贴、员工避险演练、防火疏散图                     |

- **Alternate Sites（备用场地）** If it’s not feasible to harden a facility against a risk, your BCP should identify alternate sites where business activities can resume immediately (or at least in a time that’s shorter than the maximum tolerable downtime for all affected critical business functions). Chapter 18 describes a few of the facility types that might be useful in this stage. Typically, an alternate site is associated with disaster recovery planning (DRP) rather than BCP. The organization might identify the need for an alternate site during BCP development, but it takes an actual interruption to trigger the use of the site, making it fall under the DRP.

  - 如果加固不可行或设施仍可能瘫痪，就必须准备一个**替代位置**继续运行业务， 用站点虽然在 BCP 中定义，但**只有在灾难触发后才进入 DRP 执行阶段**

  - | 阶段 | 内容                   | 类型     |
    | ---- | ---------------------- | -------- |
    | BCP  | 识别并规划备用站点     | 策略层面 |
    | DRP  | 灾难发生后启动备用站点 | 执行层面 |

  - 备用站点的类型分类（CISSP重点）

  - | 类型                     | 描述                                     | 启动速度       | 成本             |
    | ------------------------ | ---------------------------------------- | -------------- | ---------------- |
    | **Hot Site**             | 实时同步、配置完整的站点                 | 几分钟～几小时 | 高               |
    | **Warm Site**            | 有基础设施但数据需同步和配置             | 几小时～几天   | 中               |
    | **Cold Site**            | 空场地，需搬设备、配置、部署             | 几天～几周     | 低               |
    | **Mobile Site**          | 拖车式或临时布置的可移动站点（如军用车） | 快速部署       | 中               |
    | **Reciprocal Agreement** | 与他组织互用设施                         | 不稳定         | 极低             |
    | **Cloud-based DR**       | 弹性云恢复能力                           | 快速           | 灵活但长期有成本 |

##### 3.2.3 Infrastructure

基础设施（Infrastructure）之所以重要：因为它是支撑你组织核心业务流程（如供应链、订单系统、客户服务、财务系统等）正常运行的**命脉系统**。

##### ✅ 总结：基础设施保障 = 抗打能力（硬化）+ 替代机制（冗余）+ 云中的责任边界明晰**

Every business depends on some sort of infrastructure for its critical processes. For many companies, a vital part of this infrastructure is an IT backbone of communications and computer systems that process orders, manage the supply chain, handle customer interaction, and perform other business functions. This backbone consists of servers, workstations, and critical communications links between sites.

The BCP must address how the organization will protect these systems against risks identified during the strategy development phase. As with buildings and facilities, there are two main methods of providing this protection:

- **Physically Hardening Systems（物理加固）** You can protect systems against the risks by introducing protective measures such as computer-safe fire suppression systems and uninterruptible power supplies.

  - 对现有系统做“抗打击”处理，提升灾难抵抗力

  - | 加固内容     | 示例                                               |
    | ------------ | -------------------------------------------------- |
    | 🔥 火灾防护   | 安装机房级干粉灭火器、气体灭火系统（不伤电子设备） |
    | ⚡ 电力保障   | 配备 UPS（不间断电源）、备用发电机                 |
    | 🌊 防水防潮   | 提高机房地基、防潮门、防水涂层                     |
    | 🔒 安全访问   | 控制物理访问、监控、身份验证门禁                   |
    | 🌐 网络硬化   | 专线防切断、布设双链路、备用ISP                    |
    | 🌎 分布式架构 | 避免将所有设备堆在一个物理站点（单点故障）         |

- **Alternative Systems（替代系统/冗余机制）** You can also protect business functions by introducing redundancy (either redundant components or completely redundant systems/communications links that rely on different facilities).

  - 当原系统不可用时，用备份系统、链路或服务维持运行

  - | 替代机制             | 示例                                    |
    | -------------------- | --------------------------------------- |
    | 📡 冗余通信链路       | 主链路中断时自动切换至备线              |
    | 🖥️ 备用服务器/站点    | 热备（Hot Site）或冷备（Cold Site）部署 |
    | 💽 数据多地备份       | 异地灾备中心、云同步、快照恢复          |
    | ☁️ 云架构容灾         | 跨区域部署在云服务商多个数据中心        |
    | 🔗 多云/混合云冗余    | 阿里+AWS、Azure+本地IDC多活架构         |
    | 🧳 SaaS应用备用服务商 | 第三方CRM不可用时切换至备选系统         |

These same principles apply to whatever infrastructure components serve your critical business processes—transportation systems, electrical power grids, banking and financial systems, water supplies, and so on.

##### 典型基础设施清单（你必须考虑的组件）

| 类别       | 示例                                      |
| ---------- | ----------------------------------------- |
| 💻 IT系统   | 应用服务器、数据库服务器、工作站、VPN网关 |
| 🌐 网络设施 | 路由器、防火墙、负载均衡、专线            |
| 🏗️ 物理基础 | 机房、冷却系统、配电、地基                |
| 🔋 能源保障 | UPS、发电机、电池组                       |
| 🏭 业务设施 | 呼叫中心、POS系统、自动仓储系统           |
| ☁️ 云服务商 | AWS、Azure、阿里云——必须评估其BCP能力     |
| 🏦 金融系统 | 第三方支付平台、银行API、ERP接口          |

As organizations move many of their technology operations to the cloud, this doesn’t reduce their reliance on physical infrastructure. Although the company may no longer operate the infrastructure themselves, they still rely on the physical infrastructure of their cloud service providers and should take measures to ensure they are comfortable with the level of continuity planning conducted by those providers. A disruption at a key cloud provider that affects one of the organization’s own critical business functions can be just as damaging as a failure of the organization’s own infrastructure.

##### 关于“云”的重要提醒（CISSP常考）

虽然你不再拥有物理机房，但你依然**依赖云服务商的数据中心、电网、链路和BCP能力**

| 问题                 | 建议                                         |
| -------------------- | -------------------------------------------- |
| 云服务中断怎么办？   | 评估云厂商SLAs、部署跨区域备份、使用多云架构 |
| 云灾备谁负责？       | 与厂商签署责任协议、明确RPO/RTO边界          |
| 云中数据备份谁保障？ | 建议客户自主备份、控制关键数据副本           |

##### 实际应用场景

| 场景               | 应对措施                                   |
| ------------------ | ------------------------------------------ |
| 总部服务器室断电   | 启动UPS，1小时内切换至温备站点             |
| 主ISP断网          | 自动切换至备用ISP线路，使用云加速服务      |
| AWS某区域故障      | 启动跨区负载、CDN缓存、云容灾              |
| 企业私有云机房中毒 | 恢复至上次快照、隔离传播节点、启用清洁备机 |

##### CISSP 应试重点

| 题型                         | 答题要点                |
| ---------------------------- | ----------------------- |
| 如何保证IT系统不因灾难中断？ | 冗余部署 + 物理硬化     |
| 云计算是否减少BCP工作量？    | ❌ 否！依赖转移≠责任消失 |
| 基础设施中断是否影响BCP？    | ✅ 是核心风险来源之一    |
| BCP处理基础设施的方式？      | 硬化 + 替代系统部署     |

##### CISSP 应试提示

| 考点                       | 关键词识别                               |
| -------------------------- | ---------------------------------------- |
| 哪一步输出 COOP？          | Step 3 整体目标                          |
| 策略制定 vs 流程设计区别？ | 3.1 定战略、3.2 执行细节                 |
| 为什么不能解决所有风险？   | 成本、现实资源限制（考残余风险residual） |
| 哪些资产要保护？           | **人 + 建筑 + IT基础设施**               |
| 备用站点在哪一步处理？     | 属于 3.2 Facilities 的 Provisions 内容   |

### Step 4. Plan Approval and Implementation









































