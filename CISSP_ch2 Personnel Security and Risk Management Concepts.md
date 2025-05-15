# Personnel Security and Risk Management Concepts

**Domain 1 Security and Risk Management**

### Personnel Security Policies and Procedures

Humans are often considered the weakest element in any security solution. No matter what physical or logical controls are deployed, humans can discover ways to avoid them, circumvent(规避) or subvert(颠覆) them, or disable them. Thus, it is important to take into account the humanity of your users when designing and deploying security solutions for your environment. To understand and apply security governance, you must address the weakest link in your security chain- people.

Issues, problems, and compromises related to humans occur at all stages of a security solution development. This is because humans are involved throughout the development, deployment, and ongoing management of any solution. Therefore, you must evaluate the effect users, designers, programmers, developers, managers, vendors, consultants, and implementers have on the process.

#### Onboarding: Employment Agreements and Policies

To maintain security, access should be assigned according to the principle of least privilege. The principle of least privilege states that users should be granted the minimum amount of access necessary for them to complete their required work tasks or job responsibilities. True application of this principle requires low-level granular control over all resources and functions.

An **acceptable use policy (AUP)** defines what is and what is not an acceptable activity, practice, or use for company equipment and resources. The AUP is specifically designed to assign security roles within the organization as well as prescribe the responsibilities tied to those roles. This policy defines a level of acceptable performance and expectation of behavior and activity. Failure to comply with the policy may result in job action warnings, penalties, or termination.

In addition to employment agreements, there may be other security-related documentation that must be addressed. One common document is a **nondisclosure agreement (NDA).** An NDA is used to protect the confidential information within an organization from being disclosed by a current or former employee. Violations of an NDA are often met with strict penalties. Throughout a worker’s employment, they may be asked to sign additional NDAs as their job responsibilities change and they are needing to access new sensitive, proprietary, or confidential assets. When an employee leaves the organization, they should be reminded of their legal obligation to maintain silence on all items covered by any signed NDAs. In fact, they may be required to re-sign the NDA upon departure as a means to legally confirm that they are fully aware of their legally recognized obligation to maintain trade secrets and other confidential information.

#### Employee Oversight(监督)

Throughout the employment lifetime of personnel, managers should regularly review or audit the job descriptions, work tasks, privileges, and responsibilities for every staff member. It is common for work tasks and privileges to drift over time. Drifting job responsibilities or privilege creep can also result in security violations. Excess privileges held by a worker represent increased risk to the organization.

Reviewing and then adjusting user capabilities to realign with the principle of least privilege is a risk reduction strategy.

For some organizations, mostly those in the financial industry, a key part of this review process is enforcing mandatory vacations. **Mandatory vacations** are used as a peer review process. This process requires a worker to be away from the office and without remote access for one to two weeks per year. While the worker is on the “vacation,” a different worker performs their work duties with their actual user account, which makes it easier to verify the work tasks and privileges of employees while attempting to detect abuse, fraud, or negligence on the part of the original employee.

When several people work together to perpetrate a crime, it’s called **collusion**. Employing the principles of 

- **separation of duties,** 
- **restricted job responsibilities,** 
- **mandatory vacations,** 
- **job rotation, and** 
- **cross-training** 

reduces the likelihood that a coworker will be willing to collaborate on an illegal or abusive scheme because of the higher risk of detection. 

Collusion and other privilege abuses can also be reduced through **strict monitoring of special privileges** and **privileged accounts**, such as those of an administrator, root, and others.

#### Offboarding, Transfers, and Termination Processes

Offboarding is the removal of an employee’s identity from the IAM system once that person has left the organization. But offboarding can also be an element used when an employee transfers into a new job position at the same organization, especially when they are shifting between departments, facilities, or geographic locations.

Personnel transfers may be treated as a fire/rehire rather than a personnel move. This depends on the organization’s policies and the means they have determined to best manage this change. 

When a full offboarding is going to occur, whether as part of a fire/rehire transfer, a retirement, or a termination, this can include 

- disabling and/or deleting the user account, 
- revoking certificates, 
- canceling access codes, 
- and terminating other specifically granted privileges. 

It is common to disable accounts of prior employees in order to retain the identity for auditing purposes for a few months.

After the allotted time, if no incidents are discovered in regard to the ex-employee’s account, then it can be deleted from the IAM completely. If the account is deleted prematurely, any logged events that are of a security concern no longer point to an actual account and thus can make tracking down further evidence of violations more complicated.

if a person is not acceptable as an employee in one department, is it realistic to assume they would be in another? Rather than passing around the problem, the better option is to terminate the problematic employee, especially if direct training and coaching does not provide a resolution.

**Terminations** are typically unpleasant processes for all involved. However, when well planned and scripted, they might be elevated to a neutral experience. The intent of a termination policy is to reduce the risk associated with employee termination while treating the person with respect. The termination meeting should take place with at least one witness, preferably a higher-level manager and/or a security guard. Once the employee has been informed of their release, they should be reminded of the liabilities and restrictions placed on the former employee based on the employment agreement, NDAs, and any other securityrelated documentation.

During this meeting, all organization-specific identification, access, or badges as well as devices, cards, keys, and access tokens should be collected.

For nonvoluntary terminations where there is a perceived risk of a confrontation, the termination process may need to be abrupt and attended by security guards. Any need to resolve HR issues, retrieve company equipment, review NDAs, and so forth can be handled afterward through an attorney.

An exit interview is normally done by an HR person who specializes in those interviews with the idea of learning from the employee’s experience. The purpose of an exit interview is to understand why the employee is leaving, what their perspective is of the organization (its personnel, culture, process, etc.), and what they suggest could be done to improve conditions for current and future employees. Information learned from an exit interview may assist the organization with retaining employees through employment improvements and process/policy changes.

![image-20250513223304093](/Users/TODO/Library/Application Support/typora-user-images/image-20250513223304093.png)

The following list includes some other security issues that should be handled as soon as possible:

- Remove or disable the employee’s user account at the same time as or just before they are notified of being terminated.
- Make sure the employee returns any organizational equipment or supplies from their vehicle or home.
- Arrange for a member of the security department to accompany the released employee while they gather their personal belongings from the work area.
- Inform all security personnel and anyone else who watches or monitors any entrance point to ensure that the ex-employee does not attempt to reenter the building without an escort.

#### Vendor, Consultant, and Contractor Agreements and Controls

Vendor, consultant, and contractor controls are used to define the levels of performance, expectation, compensation, and consequences for entities, persons, or organizations that are external to the primary organization.

**Multiparty risk** exists when several entities or organizations are involved in a project. The risk or threats are often due to the variations of objectives, expectations, timelines, budgets, and security priorities of those involved.

**Using service-level agreements (SLAs)** is a means to ensure that organizations providing services maintain an appropriate level of service agreed on by both the service provider, vendor, or contractor and the customer organization.

SLAs and vendor, consultant, and contractor controls are an important part of risk reduction and risk avoidance. By clearly defining the **expectations and penalties** for external parties, everyone involved knows what is expected of them and what the consequences are in the event of a failure to meet those expectations.

SLAs should include a **focus on protecting and improving security** in addition to ensuring **quality and timely** services at a **reasonable price**. Some SLAs are set and cannot be adjusted, whereas with others you may have significant influence over their content. You should ensure that an SLA supports the tenets of your security policy and infrastructure rather than being in conflict with them, which could introduce weak points, vulnerabilities, or exceptions.

**Outsourcing** is the term often used to describe the use of an external third party, such as a vendor, consultant, or contractor, rather than performing the task or operation in-house.

Vendors, consultants, and contractors also represent an increase in risk of trade secret theft or **espionage**(间谍活动) Some organizations may benefit from a **vendor management system (VMS)**. A VMS is a software solution that assists with the management and procurement of staffing services, hardware, software, and other needed products and services.

In regard to security, a VMS can potentially keep communications and contracts confidential, require encrypted and authenticated transactions, and maintain a detailed activity log of events related to vendors and suppliers.

#### Compliance Policy Requirements

**Compliance** is the act of conforming to or adhering to rules, policies, regulations, standards, or requirements. Compliance is an important concern of security governance. 

Compliance is a form of administrative or managerial security control because it focuses on policies and people abiding by those policies.

#### Privacy Policy Requirements

Privacy can be a difficult concept to define. The term is used frequently in numerous contexts without much quantification or qualification. Here are some partial definitions of privacy:

- Active prevention of unauthorized access to information that is personally identifiable (that is, data points that can be linked directly to a person or organization), known as personally identifiable information (PII)
- Freedom from unauthorized access to information deemed personal or confidential
- Freedom from being observed, monitored, or examined without consent or knowledge

Protecting individuals from unwanted observation, direct marketing, and disclosure of private, personal, or confidential details is usually considered a worthy effort.

There are many legislative and regulatory compliance issues in regard to privacy. Many U.S. regulations—such as the Health Insurance Portability and Accountability Act (**HIPAA**), the Sarbanes–Oxley Act of 2002 (**SOX**), the Family Educational Rights and Privacy Act (FERPA), and the Gramm–Leach–Bliley Act—as well as the European Union’s General Data Protection Regulation (**GDPR**) (Regulation [EU] 2016/679)—include privacy requirements.

If you gather any type of information about any person or company, you must address privacy.

### Understand and Apply Risk Management Concepts

**Risk management** is a detailed process of **identifying factors** that could damage or disclose assets, **evaluating those factors** in light of **asset value** and **countermeasure** cost, and **implementing cost-effective solutions** for mitigating or reducing risk.

The primary goal of risk management is to reduce risk to an acceptable level.

Risk management is composed of two primary elements:

- **risk assessment**
- **risk response**

**Risk assessment** or risk analysis is the examination of an environment for risks, evaluating each threat event as to its likelihood of occurring and the severity of the damage it would cause if it did occur, and assessing the cost of various countermeasures for each risk.

**Risk response** involves evaluating countermeasures, safeguards, and security controls using a cost/benefit analysis; adjusting findings based on other conditions, concerns, priorities, and resources; and providing a proposal of response options in a report to senior management.

**Risk awareness** is the effort to increase the knowledge of risks within an organization. This includes understanding the value of assets, inventorying the existing threats that can harm those assets, and the responses selected and implemented to address the identified risk. Risk awareness helps to inform an organization about the importance of abiding by security policies and the consequences of security failures.

### Risk Terminology and Concepts

**Asset** An asset is anything used in a business process or task. If an organization relies on a person, place, or thing, whether tangible or intangible, then it is an asset.

**Asset Valuation **a dollar figure is assigned as the asset value (AV).

**Threats** Any potential occurrence that may cause an undesirable or unwanted outcome for an organization or for a specific asset is a threat.

**Threat Agent/Actors** Threat agents or threat actors intentionally exploit vulnerabilities. Threat agents are usually people, but they could also be programs, hardware, or systems. Threat agents wield threats in order to cause harm to targets.

**Threat Events** Threat events are accidental occurrences and intentional **exploitations**(挖掘) of vulnerabilities.

**Threat Vector** A threat vector or attack vector is the path or means by which an attack or attacker can gain access to a target in order to cause harm. Threat vectors can include email, web surfing, external drives, Wi-Fi networks, physical access, mobile devices, cloud, social media, supply chain, removable media, and commercial software.

**Vulnerability** (漏洞) The weakness in an asset or the absence or the weakness of a safeguard or countermeasure is a vulnerability.

**Exposure** Exposure is being susceptible to asset loss because of a threat; there is the possibility that a vulnerability can or will be exploited by a threat agent or event. The quantitative risk analysis value of **exposure factor (EF)** is derived from this concept.

**Risk**  Risk is the possibility or likelihood that a threat will exploit a vulnerability to cause harm to an asset and the severity of damage that could result. 

**risk = probability of harm * severity of harm**

**Safeguards** A safeguard, security control, protection mechanism, or countermeasure is anything that removes or reduces a vulnerability or protects against one or more specific threats.

**Attack** An attack is the intentional attempted exploitation of a vulnerability by a threat agent to cause damage, loss, or disclosure of assets.

**Breach**(泄漏) A breach, **intrusion**(入侵), or **penetration**(渗透) is the occurrence of a security mechanism being bypassed or thwarted by a threat agent. A breach is a successful attack.

![image-20250514224316883](/Users/TODO/Library/Application Support/typora-user-images/image-20250514224316883.png)

#### Asset Valuation

A primary goal of risk analysis is to ensure that only cost-effective safeguards are deployed. As a rule, the annual costs of safeguards should not exceed the potential annual cost of asset value loss.

The following list includes tangible and intangible issues that contribute to the valuation of assets:

■✓ Purchase cost

■✓ Development cost

■✓ Administrative or management cost

■✓ Maintenance or upkeep cost

■✓ Cost in acquiring asset

■✓ Cost to protect or sustain asset

■✓ Value to owners and users

■✓ Value to competitors

■✓ Intellectual property or equity value

■✓ Market valuation (sustainable price)

■✓ Replacement cost

■✓ Productivity enhancement or degradation

■✓ Operational costs of asset presence and loss

■✓ Liability of asset loss

■✓ Usefulness

■✓ Relationship to research and development

Assigning or determining the value of assets to an organization can fulfill numerous requirements by

■✓ Serving as the foundation for performing a cost/benefit analysis of asset protection when performing safeguard selection

■✓ Serving as a means for evaluating the cost-effectiveness of safeguards and countermeasures

■✓ Providing values for insurance purposes and establishing an overall net worth or net value for the organization

■✓ Helping senior management understand exactly what is at risk within the organization

■✓ Preventing negligence of due care/due diligence and encouraging compliance with legal requirements, industry regulations, and internal security policies

#### Identify Threats and Vulnerabilities

In most cases, a team rather than a single individual should perform risk assessment and analysis. Also, the team members should be from various departments within the organization. It is not usually a requirement that all team members be security professionals or even network/system administrators. The diversity of the team based on the demographics of the organization will help exhaustively identify and address all possible threats and risks.

Risk assessment is a highly involved, detailed, complex, and lengthy process. Often risk analysis cannot be properly handled by existing employees because of the size, scope, or liability of the risk; thus, many organizations bring in risk management consultants to perform this work. This provides a high level of expertise, does not bog down employees, and can be a more reliable measurement of real-world risk. But even risk management consultants do not perform risk assessment and analysis on paper only; they typically employ **risk assessment software.** This software **streamlines the overall task,** provides more reliable results, and produces standardized reports that are acceptable to insurance companies, boards of directors, and so on.

#### Risk Assessment/Analysis

Risk is personal, or at least specific to an organization based on its assets, its threats, its threat agents/actors, and its risk tolerance.

There are two primary risk assessment methodologies: quantitative and qualitative. 

- **Quantitative risk** **analysis** assigns real dollar figures to the loss of an asset and is based on mathematical calculations. 

- **Qualitative risk** **analysis** assigns subjective and intangible values to the loss of an asset and takes into account perspectives, feelings, intuition, preferences, ideas, and gut reactions.

The goal of risk assessment is to identify risks (based on asset-threat pairings) and rank them in order of criticality. 

At some point, the evaluation shifts from being mostly subjective qualitative to more substantial quantitative.

##### Qualitative Risk Analysis

Qualitative risk analysis is more **scenario based** than it is calculator based. Rather than assigning exact dollar figures to possible losses, you rank threats on a relative scale to evaluate their **risks, costs, and effects**.

The process of performing qualitative risk analysis involves **judgment, intuition, and experience.**

**Techniques** to perform qualitative risk analysis:

- Brainstorming
- Storyboarding
- Focus groups
- Surveys
- Questionnaires
- Checklists
- One-on-one meetings
- Interviews
- **Scenarios**: The basic process for all these mechanisms involves the creation of scenarios. A scenario is a written description of a single major threat.
- **Delphi technique**: The Delphi technique is simply an anonymous feedback-and-response process used to enable a group to reach an anonymous consensus. The goal or purpose of the Delphi technique is to facilitate the evaluation of ideas, concepts, and solutions on their own merit without the discrimination that often occurs based on who the idea comes from.

##### Quatitative Risk Analysis

The quantitative method results in concrete probability indications or a numeric indication of relative risk potential. That means the end result is a report that has dollar figures for levels of risk, potential loss, cost of countermeasures, and value of safeguards.

The major steps or phases in quantitative risk analysis are as follows

1. Inventory assets, and assign a value (**asset value [AV]**).

2. Research each asset, and produce a list of all possible threats to each individual asset. This results in asset-threat pairings.

3. For each asset-threat pairing, calculate the **exposure factor (EF)**.

4. Calculate the **single loss expectancy (SLE)** for each asset-threat pairing.

5. Perform a threat analysis to calculate the likelihood of each threat being realized within a single year—that is, the **annualized rate of occurrence (ARO)**.

6. Derive the overall loss potential per threat by calculating the **annualized loss expectancy (ALE).**

7. Research countermeasures for each threat, and then calculate the changes to ARO, EF, and ALE based on an applied countermeasure.

8. Perform a **cost/benefit** analysis of each countermeasure for each threat for each asset. Select the most appropriate response to each threat.

![image-20250514225749619](/Users/TODO/Library/Application Support/typora-user-images/image-20250514225749619.png)

The cost functions associated with quantitative risk analysis include the following:

**Exposure Factor(EF)** represents the percentage of loss that an organization would experience if a specific asset were violated by a realized risk. The EF can also be called the loss potential.

**Single-Loss Expectancy(SLE)**  is the potential loss associated with a single realized threat against a specific asset.

SLE = asset value (AV) * exposure factor (EF) 

**Annualized Rate of Occurrence(ARO)**  is the expected frequency with which a specific threat or risk will occur (that is, become realized) within a single year.

**Annualized Loss Expectancy(ALE)**  is the possible yearly loss of all instances of a specific realized threat against a specific asset.

ALE = SLE * ARO 

ALE = AV * EF * ARO

The largest ALE is the biggest problem the organization is facing and thus the first risk to be addressed in risk response.

### Risk Responses

There are several possible risk respons options to risk:

- **Mitigation or reduction**(缓解): is the implementation of safeguards, security controls, and countermeasures to reduce and/or eliminate vulnerabilities or block threats. 
- **Assignment or transfer** is the placement of the responsibility of loss due to a risk onto another entity or organization. Purchasing cybersecurity or traditional insurance and outsourcing are common forms of assigning or transferring risk.
- **Deterrence**(威慑): is the process of implementing deterrents to would-be violators of security and policy. The goal is to convince a threat agent not to attack. making it known that the organization is willing to cooperate with authorities and prosecute those who participate in cybercrime.
- **Avoidance**: is the process of selecting alternate options or activities that have less associated risk than the default, common, expedient, or cheap option. The risk is avoided by eliminating the risk cause. 
- **Acceptance**: is the result after a cost/benefit analysis shows countermeasure costs would outweigh the possible cost of loss due to a risk. It also means that management has agreed to accept the consequences and the loss if the risk is realized. In most cases, accepting risk requires a clearly written statement that indicates why a safeguard was not implemented, who is responsible for the decision, and who will be responsible for the loss if the risk is realized, usually in the form of a document signed by senior management.
- **Reject or ignore** An unacceptable possible response to risk is to reject risk or ignore risk. Denying that a risk exists and hoping that it will never be realized are not valid or prudent(谨慎的) due care/due diligence responses to risk. Rejecting or ignoring risk may be considered negligence in court.

| 响应方式                   | 中文解释      | 核心思路                         | 是否可取   | 举例说明                                     |
| -------------------------- | ------------- | -------------------------------- | ---------- | -------------------------------------------- |
| **Mitigation / Reduction** | 风险缓解/降低 | **采取控制手段来降低威胁或漏洞** | ✔️ 推荐     | 部署防火墙、防病毒、MFA、补丁管理等          |
| **Assignment / Transfer**  | 风险转移      | **让他人承担损失责任**           | ✔️ 推荐     | 买保险、外包云服务、签责任协议               |
| **Deterrence**             | 威慑措施      | **震慑威胁者，让其不敢实施攻击** | ✔️ 辅助策略 | 告示牌、监控摄像头、起诉公告                 |
| **Avoidance**              | 风险回避      | **改变做法，彻底绕开风险源头**   | ✔️ 建议     | 放弃上线风险过高的新功能、取消高危供应商合作 |
| **Acceptance**             | 风险接受      | **理性权衡后，接受潜在损失**     | ✔️ 条件允许 | 某非核心系统宕机1小时的损失低于加固成本      |
| **Rejection / Ignore**     | 拒绝/忽视     | **否认风险存在、不做处理**       | ❌ 错误行为 | “黑客不会攻击我们”，忽视渗透测试结果         |

CISSP 考试要特别注意的点

| 考点类型                   | 提示说明                                     |
| -------------------------- | -------------------------------------------- |
| ❗ Risk Acceptance ≠ 忽视   | 接受是有计划、经审批的；忽视是违规行为       |
| ❗ Mitigation ≠ Elimination | 缓解是**降低风险**，不是消除                 |
| ❗ Transfer 并非无风险      | 责任可能被转移，但声誉/法律责任可能仍保留    |
| ❗ Deterrence 是心理战术    | 目的是“劝退攻击者”，但不等于技术控制         |
| ❗ Rejection 永远是错的     | 拒绝或否认风险 = 缺乏 due care，违反合规义务 |

These risk responses are all related to an organization’s risk appetite and risk tolerance. 

- **Risk appetite**(willingness) is the total amount of risk that an organization is willing to shoulder in aggregate across all assets. 
- **Risk capacity**(capability) is the level of risk an organization is able to shoulder. An organization’s desired risk appetite may be greater than its actual capacity. 
- **Risk tolerance** is the amount or level of risk that an organization will accept per individual asset-threat pair. 
- **Risk target** is the preferred level of risk for a specific asset-threat pairing. 
- **Risk limit** is the maximum level of risk above the risk target that will be tolerated before further risk management actions are taken.

风险能力 ≥ 风险食欲 ≥ 风险容忍度 ≥ 风险目标 ≤ 风险上限

| 概念               | 中文名            | 定义关键词                              | 范围层级      | 类比举例                                      |
| ------------------ | ----------------- | --------------------------------------- | ------------- | --------------------------------------------- |
| **Risk Appetite**  | 风险食欲/接受意愿 | 组织愿意整体承担的**风险总量**          | 全组织层面    | 我能接受每年投资有 10% 的亏损潜在可能性       |
| **Risk Capacity**  | 风险承受能力      | 组织**能够**承担的最大风险限度（能力）  | 全组织层面    | 我的财务状况最多只能承受 5% 的亏损            |
| **Risk Tolerance** | 风险容忍度        | 单个资产+威胁对组合的**可接受波动范围** | 局部/战术层面 | 某个系统最多可以承受 1 小时的中断             |
| **Risk Target**    | 风险目标值        | 针对某威胁-资产对，期望维持的风险水平   | 局部/操作层面 | 希望把某服务的入侵风险控制在“中”以下          |
| **Risk Limit**     | 风险上限          | 超过“目标”多少范围时就必须触发应对措施  | 局部/操作层面 | 如果服务宕机超过 2 小时就必须启动应急响应计划 |

✅ **Risk Appetite** 是你“想承担多少”
✅ **Risk Capacity** 是你“最多能承受多少”
✅ **Risk Tolerance** 是你对“某个风险的容忍范围”
✅ **Risk Target** 是你“理想中希望保持的风险状态”
✅ **Risk Limit** 是你“绝对不能超过的临界线”
