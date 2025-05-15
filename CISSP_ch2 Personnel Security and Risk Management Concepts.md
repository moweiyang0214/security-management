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

**Inherent risk** is the level of natural, native, or default risk that exists in an environment, system, or product prior to any risk management efforts being performed. Inherent risk can exist due to the supply chain, developer operations, design and architecture of a system, or the knowledge and skill base of an organization. Inherent risk is also known as initial risk or starting risk. This is the risk that is identified by the risk assessment process.

Once safeguards, security controls, and countermeasures are implemented, the risk that remains is known as residual risk. **Residual risk** consists of threats to specific assets against which upper management chooses not to implement a response. In other words, residual risk is the risk that management has chosen to accept rather than mitigate. 

**Total risk** is the amount of risk an organization would face if no safeguards were implemented. A conceptual formula for total risk is as follows:

**threats * vulnerabilities * asset value = total risk**

The controls gap is the amount of risk that is reduced by implementing safeguards.

**total risk – controls gap = residual risk**

**Control risk** is the risk that is introduced by the introduction of the countermeasure to an environment. Most safeguards, security controls, and countermeasures are themselves some sort of technology.

Although a control may reduce the risk of a threat to an asset, it may also introduce a new risk of a threat that can compromise the control itself. Thus, risk assessment and response must be an iterative operation that looks back on itself to make continuous improvements.

### Cost vs. Benefit of Security Controls

An estimation of the yearly costs for the safeguard to be present in the organization is needed. This estimation can be called the **annual cost of the safeguard (ACS)**. Several common factors affect ACS:

- Cost of purchase, development, and licensing
- Cost of implementation and customization
- Cost of annual operation, maintenance, administration, and so on
- Cost of annual repairs and upgrades
- Productivity improvement or loss
- Changes to environment
- Cost of testing and evaluation

**cost/benefit calculation**, or cost/benefit analysis. This calculation is used to determine whether a safeguard actually improves security without costing too much. To determine whether the safeguard is financially equitable, use the following formula:

**[ALE pre-safeguard – ALE post-safeguard] – annual cost of safeguard (ACS)** = value of the safeguard to the company

- If the result is negative, the safeguard is not a financially responsible choice. 

- If the result is positive, then that value is the annual savings your organization may reap by deploying the safeguard because the rate of occurrence is not a guarantee of occurrence. 
- If multiple safeguards seem to have a positive cost/benefit result, then the safeguard with the **largest benefit** is the most cost-effective option.

In review, to perform the cost/benefit analysis of a safeguard, you must calculate the following three elements:

- The pre-safeguard ALE for an asset-threat pairing
- The potential post-safeguard ALE for an asset-threat pairing
- The ACS (annual cost of the safeguard)

**(ALE1 – ALE2) – ACS,**

The countermeasure with the greatest resulting value from this cost/benefit formula makes the most economic sense to deploy against the specific asset-threat pairing.

![image-20250515112846290](/Users/TODO/Library/Application Support/typora-user-images/image-20250515112846290.png)

To effectively manage the security function, you must assess the budget, the benefit and performance metrics, and the necessary resources of each security control. Only after a thorough evaluation can you determine which controls are essential and beneficial not only to security, but also to your bottom line.

Keep in mind that organizational security should be based on a business case, be legally justifiable, and be reasonably in line with security frameworks, regulations, and best practices.

### Countermeasure Selection and Implementation

Keep in mind that security should be designed to support and enable business tasks and functions. Thus, countermeasures and safeguards need to be evaluated in the context of a business process. If there is no clear business case for a safeguard, it is probably not an effective security option.

Security controls, countermeasures, and safeguards can be implemented **administratively**, **logically/technically**, or **physically**. These three categories of security mechanisms should be implemented in a conceptual layered **defense-in-depth manner** in order to provide **maximum benefit.**

![image-20250515113512402](/Users/TODO/Library/Application Support/typora-user-images/image-20250515113512402.png)

1. Administrative Controls

The category of administrative controls are the policies and procedures defined by an organization’s security policy and other regulations or requirements. They are sometimes referred to as management controls, managerial controls, or procedural controls.

These controls focus on personnel oversight and business practices. Examples of administrative controls include policies, procedures, hiring practices, background checks, data classifications and labeling, security awareness and training efforts, reports and reviews, work supervision, personnel controls, and testing.

2. Technical or Logical Controls

It involves the hardware or software mechanisms used to manage access and provide protection for IT resources and systems. Examples of logical or technical controls include authentication methods (such as passwords, smartcards, and biometrics), encryption, constrained interfaces, access control lists, protocols, firewalls, routers, intrusion detection systems (IDSs), and clipping levels.

3. Physical Controls

Physical controls are security mechanisms focused on providing protection to the facility and real-world objects. Examples of physical controls include guards, fences, motion detectors, locked doors, sealed windows, lights, cable protection, laptop locks, badges, swipe cards, guard dogs, video cameras, access control vestibules, and alarms.

### Applicable Types of Controls

security control refers to a broad range of controls that perform such tasks as ensuring that only authorized users can log on and preventing unauthorized users from gaining access to resources. Controls mitigate a wide variety of information security risks.

#### Preventive Control

A preventive control (aka preventative control) is deployed to thwart or stop unwanted or unauthorized activity from occurring. Examples of preventive controls include fences, locks, authentication, access control vestibules, alarm systems, separation of duties, job rotation, data loss prevention (DLP), penetration testing, access control methods, encryption, auditing, security policies, security-awareness training, antimalware software, firewalls, and intrusion prevention systems (IPSs).

#### Deterrent Control

A deterrent control is deployed to discourage security policy violations. Deterrent and preventive controls are similar, but deterrent controls often depend on individuals being convinced not to take an unwanted action. Some examples include policies, securityawareness training, locks, fences, security badges, guards, access control vestibules, and security cameras.

#### Detective Control

A detective control is deployed to discover or detect unwanted or unauthorized activity. Detective controls operate after the fact and can discover the activity only after it has occurred. Examples of detective controls include security guards, motion detectors, recording and reviewing of events captured by security cameras or CCTV, job rotation, mandatory vacations, audit trails, honeypots or honeynets, intrusion detection systems (IDSs), violation reports, supervision and review of users, and incident investigations.

#### Compensation Control

A compensation control is deployed to provide various options to other existing controls to aid in enforcement and support of security policies. They can be any controls used in addition to, or in place of, another control. They can be a means to improve the effectiveness of a primary control or as the alternate or failover option in the event of a primary control failure. For example, if a preventive control fails to stop the deletion of a file, a backup can be a compensation control, allowing for restoration of that file. Here’s another example: if a building’s fire prevention and suppression systems fail and the building is damaged by fire so that it is not inhabitable, a compensation control would be having a disaster recovery plan (DRP) with an alternate processing site available to support work operations.

#### Corrective Control

A corrective control modifies the environment to return systems to normal after an unwanted or unauthorized activity has occurred. It attempts to correct any problems resulting from a security incident. Corrective controls can be simple, such as terminating malicious activity or rebooting a system. They also include antimalware solutions that can remove or quarantine a virus, backup and restore plans to ensure that lost data can be restored, and intrusion prevention systems (IPSs) that can modify the environment to stop an attack in progress. The control is deployed to repair or restore resources, functions, and capabilities after a violation of security policies. Examples include installing a spring on a door so that it will close and relock, and using file integrity–checking tools, such as sigverif from Windows, which will replace corrupted boot files upon each boot event to protect the stability and security of the booted OS.

#### Recovery Control

Recovery controls are an extension of corrective controls but have more advanced or complex abilities. A recovery control attempts to repair or restore resources, functions, and capabilities after a security policy violation. Recovery controls typically address more significant damaging events compared to corrective controls, especially when security violations may have occurred. Examples of recovery controls include backups and restores, fault-tolerant drive systems, system imaging, server clustering, antimalware software, and database or virtual machine shadowing. In relation to business continuity and disaster recovery, recovery controls can include hot, warm, and cold sites; alternate processing facilities; service bureaus; reciprocal agreements; cloud providers; rolling mobile operating centers; and multisite solutions.

#### Directive Control

A directive control is deployed to direct, confine, or control the actions of subjects to force or encourage compliance with security policies. Examples of directive controls include security policy requirements or criteria, posted notifications, guidance from a security guard, escape route exit signs, monitoring, supervision, and procedures.

#### 七大控制类型对比解析

| 控制类型         | 目的（做什么）                               | 何时起作用            | 常见例子                                              |
| ---------------- | -------------------------------------------- | --------------------- | ----------------------------------------------------- |
| **Preventive**   | **预防** → 阻止不该发生的事情                | **事前**              | 门禁、锁、访问控制、MFA、防火墙、加密、DLP、IPS、培训 |
| **Deterrent**    | **威慑** → 吓阻攻击者不敢做不该做的事情      | **事前（心理影响）**  | 监控摄像头标志、法律警告、警卫、告示、政策培训、徽章  |
| **Detective**    | **侦测** → 识别、发现违规行为                | **事中/事后**         | IDS、摄像头录像、审计日志、蜜罐、强制休假、作业轮换   |
| **Corrective**   | **纠正** → 尝试修复问题或停止恶意行为        | **事后立即**          | 杀毒软件、终止进程、替换文件、重启、门弹簧、自修脚本  |
| **Recovery**     | **恢复** → 恢复服务、系统和数据              | **严重问题后**        | 备份/恢复、灾备站点、镜像、热/冷备、RAID、云容灾      |
| **Compensating** | **补偿/替代** → 辅助或替代主控制策略的效果   | **辅助层面/替代措施** | 备用网点、冗余机制、补救协议、次要控制手段、灾备计划  |
| **Directive**    | **指令/引导** → 告诉人们该做什么，强制合规性 | **事前行为引导**      | 指示牌、逃生路线、SOP流程、安全指南、管理监督         |

易混淆澄清

| 易混组合                    | 区别点                                                       |
| --------------------------- | ------------------------------------------------------------ |
| **Preventive vs Deterrent** | Preventive 是**技术上阻止**攻击，Deterrent 是**心理上威慑**攻击 |
| **Detective vs Corrective** | Detective 是**发现问题**，Corrective 是**修复问题**          |
| **Corrective vs Recovery**  | Corrective 是“微修”，Recovery 是“灾难后大修复”               |
| **Compensating vs Backup**  | Backup 是技术手段，Compensating 是**策略性备用控制**，可包含多个措施 |

一句话记忆口诀（考试速记）

✅ **阻、吓、查、修、复、补、管**

| 类型缩写 | 中文 | 英文         | 口诀含义       |
| -------- | ---- | ------------ | -------------- |
| **阻**   | 阻止 | Preventive   | 阻止风险发生   |
| **吓**   | 威慑 | Deterrent    | 吓退坏人心理   |
| **查**   | 检测 | Detective    | 发现违规行为   |
| **修**   | 纠正 | Corrective   | 恢复初步功能   |
| **复**   | 恢复 | Recovery     | 灾后系统重建   |
| **补**   | 补偿 | Compensating | 替代或补足控制 |
| **管**   | 指引 | Directive    | 明确规定流程   |

### Security Control Assessment(SCA)

A security control assessment (SCA) is the formal evaluation of a security infrastructure’s individual mechanisms against a baseline or reliability expectation.

The goals of an SCA are to ensure the effectiveness of the security mechanisms, evaluate the quality and thoroughness of the risk management processes of the organization, and produce a report of the relative strengths and weaknesses of the deployed security infrastructure.

✅ **风险评估（RA）** 是识别“**有什么风险**”和“**我们怕什么**”；
✅ **安全控制评估（SCA）** 是验证“**我们做的控制有没有效果、有没有执行到位**”。

#### SCA vs RA 定义对比

| 项目       | **Risk Assessment（风险评估）**              | **Security Control Assessment（安全控制评估）**  |
| ---------- | -------------------------------------------- | ------------------------------------------------ |
| 📌 中文名   | 风险评估                                     | 安全控制评估                                     |
| 🎯 目的     | 识别、评估、分析**资产面临的威胁和风险水平** | 评估现有**安全控制措施是否有效、是否按设计执行** |
| 🔍 关注点   | 风险（威胁 × 脆弱性 × 影响）                 | 控制措施（设计、部署、操作）是否符合预期         |
| 🎯 核心问题 | “有哪些风险存在？”、“哪个资产最脆弱？”       | “我们的安全控制做得够不够好？”、“控制是否落地？” |
| 📄 输出结果 | 风险等级列表、优先级排序、风险应对建议       | 控制的合规性评估报告、改进建议、认证依据         |
| 🧭 依据参考 | **NIST 800-30**、ISO 27005、OCTAVE           | **NIST 800-53A**、ISO 27001审核、FedRAMP等       |

### 场景：你公司部署了一个客户服务系统

- **Risk Assessment 做什么？**
  - 识别系统面临的威胁（如数据泄露、DDoS）
  - 分析漏洞（如弱密码、不加密传输）
  - 评估潜在影响和发生概率
  - 结果：建议优先加密数据、限制访问权限、部署WAF等
- **Security Control Assessment 做什么？**
  - 审查系统是否**真的部署了WAF？是否启用了HTTPS？**
  - 检查权限控制是否符合策略
  - 验证配置与标准一致（如NIST 800-53控制要求）
  - 结果：指出某台服务器没加密、某日志没保留、权限配置过宽 → 提交整改建议

| 对比维度     | 风险评估（RA）                           | 安全控制评估（SCA）                        |
| ------------ | ---------------------------------------- | ------------------------------------------ |
| **起点**     | 资产/业务                                | 安全控制措施                               |
| **作用阶段** | 安全生命周期早期（识别阶段）             | 中期/后期（验证与评审阶段）                |
| **执行方式** | 风险评分、资产分类、威胁建模（如STRIDE） | 文档审查、系统测试、技术验证               |
| **执行角色** | 风险分析师、信息安全管理人员             | 安全审核员、安全架构师、第三方审计员       |
| **输出用途** | 决定优先控制哪些风险                     | 判断控制设计和执行是否达标，支持认证或整改 |

#### Monitoring and Measurement

Security controls should provide benefits that can be monitored and measured. If a security control’s benefits cannot be quantified, evaluated, or compared, then it does not actually provide any security. A security control may provide native or internal monitoring, or external monitoring may be required. You should take this into consideration when making initial countermeasure selections.

#### Risk Reporting and Documentation 

**Risk reporting** is a key task to perform at the conclusion of a risk analysis. Risk reporting involves the production of a risk report and a presentation of that report to the interested/ relevant parties.

A **risk report** should be accurate, timely, comprehensive of the entire organization, clear and precise to support decision making, and updated on a regular basis.

A **risk register** or **risk log** is a document that inventories all the identified risks to an organization or system or within an individual project. A risk register is used to record and track the activities of risk management, including the following:

- Identifying risks
- Evaluating the severity of and prioritizing those risks
- Prescribing responses to reduce or eliminate the risks
- Tracking the progress of risk mitigation

A risk register can serve as a project management document to track completion of risk response activities as well as a historical record of risk management over time.

A risk matrix or risk heat map is a form of risk assessment that is performed on a basic graph or chart. It is sometimes labeled as a qualitative risk assessment. The simplest form of a risk matrix is a 3×3 grid comparing probability and damage potential.

#### Continuous Improvement

Risk analysis identifies risks, quantifies the impact of threats, and aids in budgeting for security. It helps integrate the needs and objectives of the security policy with the organization’s business goals and intentions. 

The risk analysis/risk assessment is a “point in time” metric. Threats and vulnerabilities constantly change, and the risk assessment needs to be redone periodically in order to support continuous improvement.

| 概念                       | 定义                                                         | 特点                           | 举例                               |
| -------------------------- | ------------------------------------------------------------ | ------------------------------ | ---------------------------------- |
| **Risk Assessment**        | 在特定时间点对组织资产的威胁、漏洞和影响进行识别、分析和评估 | **“一次性”/“定期更新”的活动**  | 每年Q1对所有系统做一次全面安全评估 |
| **Continuous Improvement** | 通过不断反思、修正、升级，以**动态应对风险与业务变化**       | **持续、周期性、与运营一体化** | 每季度复审风险控制有效性，优化策略 |

**总结区别**：

- Risk Assessment 是一张照片（point-in-time snapshot）📸
- Continuous Improvement 是一个视频（不断调整迭代）🎥

##### RMM

An **enterprise risk management (ERM)** program can be evaluated using the **Risk Maturity Model (RMM).** An RMM assess the key indicators and activities of a mature, sustainable, and repeatable risk management process. There are several RMM systems, each prescribing various means to achieve greater risk management capability.

RMM 衡量的是你风险管理体系的成熟度，而管理 EOSL 设备是你实际操作中安全成熟度的重要体现。

The typical RMM levels are as follows:

1. **Ad hoc**—A chaotic starting point from which all organizations initiate risk management.

2. **Preliminary**—Loose attempts are made to follow risk management processes, but each department may perform risk assessment uniquely.

3. **Defined**—A common or standardized risk framework is adopted organization-wide.

4. **Integrated**—Risk management operations are integrated into business processes, metrics are used to gather effectiveness data, and risk is considered an element in business strategy decisions.

5. **Optimized**—Risk management focuses on achieving objectives rather than just reacting to external threats; increased strategic planning is geared toward business success rather than just avoiding incidents; and lessons learned are reintegrated into the risk management process.

##### RMM（Risk Maturity Model）各等级对比

| 级别               | 特征描述                                 | 管理状态               | 举例                                                         |
| ------------------ | ---------------------------------------- | ---------------------- | ------------------------------------------------------------ |
| **1. Ad hoc**      | 混乱、无流程、临时响应                   | 几乎没有正式的风险管理 | 某中小企业从未评估过其IT资产面临的威胁                       |
| **2. Preliminary** | 有人尝试管理风险，但方式零散             | 部门各自为政           | 财务部门做自己的风险表，技术部门做自己的评估                 |
| **3. Defined**     | 有标准流程，全组织统一框架               | 开始制度化             | 统一使用NIST RMF 或 ISO 27005 进行评估                       |
| **4. Integrated**  | 风险管理内嵌于业务流程，形成闭环反馈     | 成熟运营               | 所有新项目上线前必须进行自动化风险评分，并输出风险接受/缓解决策 |
| **5. Optimized**   | 以目标为导向，主动推动业务成功、持续学习 | 高度成熟               | 用历史事件教训不断调整策略，建立内部知识库，风险管理推动战略落地 |

**重点区分：**

- “Defined” 是**标准化**；
- “Integrated” 是**嵌入业务决策**；
- “Optimized” 是**从应对威胁 → 转向达成目标**

An often-overlooked area of risk is that of legacy devices, which may be EOL and/or EOSL

EOL vs EOSL（遗留系统风险管理）

- **End-of-life (EOL)** is the point at which a manufacturer no longer produces a product. Service and support may continue for a period of time after EOL, but no new versions will be made available for sale or distribution. An EOL product should be scheduled for replacement before it fails or reaches end-of-support (EOS) or end-of-service life (EOSL).
- **End-of-service-life (EOSL)** or **end-of-support (EOS)** are those systems that are no longer receiving updates and support from the vendor. If an organization continues to use an EOSL system, then the risk of compromise is high because any future exploitation will never be patched or fixed. It is of utmost importance to move off EOSL systems in order to maintain a secure environment. It might not seem initially cost-effective or practical to move away from a solution that still works just because the vendor has terminated support. However, the security management efforts you will expend will likely far exceed the cost of developing and deploying a modern system–based replacement. For example, Adobe Flash Player reached its EOSL on December 31, 2020, and should be uninstalled, as recommended by Adobe.

| 概念                            | 定义                                       | 风险程度 | 举例                                              |
| ------------------------------- | ------------------------------------------ | -------- | ------------------------------------------------- |
| **EOL（End-of-Life）**          | 厂商停止生产产品（但可能仍支持）           | 中等     | 某老旧网络设备不再销售，但还能打补丁              |
| **EOSL（End-of-Service-Life）** | 厂商完全停止支持和补丁服务                 | 高危     | Windows Server 2008、Adobe Flash 不再收到任何更新 |
| **继续使用EOSL的后果**          | 高风险、无补丁、漏洞永久存在，合规审计失败 | 危险行为 | 2024年还在用Win7+IE浏览器系统支撑内部OA           |

**CISSP观点：**

- **应制定计划迁移EOL/EOSL系统**
- **使用遗留系统要纳入风险管理体系，不能因为“还能用”就忽视其威胁**

| 易混点                                | 正确理解                                                     |
| ------------------------------------- | ------------------------------------------------------------ |
| 风险评估 vs 安全控制评估              | 前者是识别风险（找问题），后者是检查控制是否有效（解决方案是否做得好） |
| EOL ≠ EOSL                            | EOL是“产品不卖了”，但可能还有补丁；EOSL是“彻底没人管”，安全风险最大 |
| Continuous Improvement ≠ 风险定期评估 | 持续改进是整个管理流程的迭代，不只是“多做几次风险评估”       |

### Risk Frameworks

A risk framework is a guideline or recipe for how risk is to be assessed, resolved, and monitored.

**NIST** 提供的两大**风险管理框架**：

- Risk Management Framework (**RMF**) , establishes mandatory requirements for federal agencies; established in 2010
- Cybersecurity Framework (**CSF**), designed for critical infrastructure and commercial organizations; established in 2014

| 维度       | **RMF**（Risk Management Framework）             | **CSF**（Cybersecurity Framework）                        |
| ---------- | ------------------------------------------------ | --------------------------------------------------------- |
| 📌 全称     | 风险管理框架                                     | 网络安全框架                                              |
| 🧭 初衷     | 为**美国政府机构**提供强制性信息系统安全管理流程 | 为**关键基础设施与商业机构**提供自愿性、灵活的安全框架    |
| 🏛️ 应用对象 | 联邦政府机构、国防系统、承包商（必须遵循）       | 金融、电网、制造业、医疗等私营组织（推荐性）              |
| 🎯 核心功能 | 管理信息系统生命周期内的**风险控制决策**         | 帮助组织理解、沟通、评估并提升其**整体网络安全能力**      |
| 📆 发布年份 | 2010                                             | 2014（**最新版是CSF 2.0，2024发布**）                     |
| 📄 架构结构 | 严格流程（6步：Categorize → Monitor）            | 五大功能域（Identify、Protect、Detect、Respond、Recover） |
| 📊 目标导向 | 以**系统为中心（system-centric）**               | 以**组织为中心（organization-centric）**                  |
| ⚖️ 法规属性 | **强制执行**（适用于政府采购、FedRAMP等）        | **自愿采纳**（但广泛用于业界评估、沟通）                  |

The RMF, establishes mandatory security requirements for federal agencies. This is the primary risk framework referenced by the CISSP exam. 

The RMF has six cyclical phases.

![image-20250515152455592](/Users/TODO/Library/Application Support/typora-user-images/image-20250515152455592.png)

**Prepare** to execute the RMF from an organization- and system-level perspective by establishing a context and priorities for managing security and privacy risk.

- **Categorize** the system and the information processed, stored, and transmitted by the system based on an analysis of the impact of loss.
- **Select** an initial set of controls for the system and tailor the controls as needed to reduce risk to an acceptable level based on an assessment of risk.
- **Implement** the controls and describe how the controls are employed within the system and its environment of operation.
- **Assess** the controls to determine if the controls are implemented correctly, operating as intended, and producing the desired outcomes with respect to satisfying the security and privacy requirements.
- **Authorize** the system or common controls based on a determination that the risk to organizational operations and assets, individuals, other organizations, and the nation is acceptable.
- **Monitor** the system and the associated controls on an ongoing basis to include assessing control effectiveness, documenting changes to the system and environment of operation, conducting risk assessments and impact analyses, and reporting the security and privacy posture of the system.

### 🔹 **RMF 六大阶段（必须记住！）**

1. **Categorize** – 分类系统与数据重要性
2. **Select** – 选择控制措施（参考 **NIST 800-53**）
3. **Implement** – 实施控制
4. **Assess** – 评估控制效果（对接 **NIST 800-53A**）
5. **Authorize** – 授权系统运行
6. **Monitor** – 持续监控安全态势

📌 **关键词记忆：CS-IAM（Categorize, Select, Implement, Assess, Authorize, Monitor）**

The CSF is not a checklist or procedure—it is a prescription of operational activities that are to be performed on an ongoing basis for the support and improvement of security over time. The CSF is more of an improvement system rather than its own specific risk management process or security infrastructure.

### 🔹 **CSF 五大功能（功能导向）**

1. **Identify** – 资产、风险、业务环境识别
2. **Protect** – 加强控制措施、培训、数据防护
3. **Detect** – 事件检测、监控、报警
4. **Respond** – 响应流程、通报、修复
5. **Recover** – 恢复能力、业务连续性、教训总结

📌 **关键词记忆：IPDRR**

实用场景举例

| 应用场景                                 | 推荐框架 | 理由                                                 |
| ---------------------------------------- | -------- | ---------------------------------------------------- |
| 联邦政府采购新系统需建立安全控制         | **RMF**  | 符合 FedRAMP、FISMA 要求，需严格控制流程与授权       |
| 金融行业提升企业整体网络安全成熟度       | **CSF**  | 可灵活自定义优先级，适合与业务流程结合，评估成熟度   |
| 某医疗公司希望用标准框架引导安全投资方向 | **CSF**  | 面向组织整体能力构建，支持沟通、优先排序和预算制定   |
| 国防承包商上线系统需授权使用             | **RMF**  | 遵循 **NIST 800-53** 控制集，支持系统授权流程（ATO） |

考试易混淆

| 考题角度                     | 答题关键                           |
| ---------------------------- | ---------------------------------- |
| 哪个是强制性的？             | **RMF** 针对政府、承包商，强制执行 |
| 哪个更灵活、适用于商业组织？ | **CSF** 是自愿性框架，面向业界     |
| 哪个基于系统生命周期？       | **RMF**（系统为中心）              |
| 哪个用于评估组织安全成熟度？ | **CSF**（组织为中心）              |
| 哪个与 NIST 800-53 强关联？  | **RMF** 直接引用该控制列表         |

The **NIST RMF** is the primary focus of the **CISSP exam**, but you might want to review other risk management frameworks for use in the real world. Please consider the following for future research:

- The Committee of Sponsoring Organizations **(COSO)** of the Treadway Commission’s Enterprise Risk Management **(ERM)**— Integrated Framework
- **ISACA’s Risk IT Framework**
- Operationally Critical Threat, Asset, and Vulnerability Evaluation **(OCTAVE)**
- Factor Analysis of Information Risk **(FAIR)**
- Threat Agent Risk Assessment **(TARA)**

| 框架名称          | 类型           | 核心特点                                 | 适合对象/环境                   |
| ----------------- | -------------- | ---------------------------------------- | ------------------------------- |
| **COSO ERM**      | 企业治理级     | 宏观、战略导向，强调内部控制与财务合规性 | 企业高层、审计、合规、金融行业  |
| **ISACA Risk IT** | IT治理级       | 专注IT风险与业务目标对齐，基于 COBIT     | CIO、安全策略制定者、审计师     |
| **OCTAVE**        | 组织驱动型     | 自上而下识别风险，聚焦信息资产与业务影响 | 中大型组织、政策导向环境        |
| **FAIR**          | 定量建模型     | 基于概率的财务风险量化（用美元衡量）     | CISO、CFO、需量化风险的人       |
| **TARA**          | 威胁情报驱动型 | 用威胁场景优先排序，筛选最重要的风险对   | 高技术企业、APT防护、国防承包商 |

### 🎯 **1. COSO ERM**

> **Committee of Sponsoring Organizations – Enterprise Risk Management**

- 目标：将风险管理与组织整体战略、价值创造对齐
- 强调 **内部控制（Internal Control）+ 财务合规 + 高管职责**
- 八大元素：目标设定、事件识别、风险评估、控制活动等

📌 **举例：** 上市公司需向SEC展示全面风险管理架构时采用 COSO。

------

### 🎯 **2. ISACA Risk IT Framework**

> 来自 COBIT 背后的组织 ISACA，强调 **IT风险与业务目标的整合**

- 包含三个主要领域：**风险治理、风险评估、风险响应**
- 关注如何从战略层面将 IT 风险映射为业务影响
- 可结合 COBIT、Val IT 使用

📌 **举例：** 一个金融机构将 IT 系统风控与其贷款、客户交易系统进行对齐。

------

### 🎯 **3. OCTAVE**

> **Operationally Critical Threat, Asset, and Vulnerability Evaluation**

- 由 Carnegie Mellon CERT 开发
- 自上而下，由业务部门主导风险识别
- 强调“业务视角”而不是“技术漏洞视角”

📌 **举例：** 医疗机构进行基于资产的风险识别时，使用 OCTAVE 定义核心病患数据系统和威胁场景。

------

### 🎯 **4. FAIR**

> **Factor Analysis of Information Risk**

- 强调 **定量分析**，可将风险转化为美元损失（Loss Event Value）
- 支持建模、优先排序、可视化报告
- 可结合 GRC 工具使用（如 RiskLens）

📌 **举例：** CISO 希望用**金钱语言与 CFO 交流**，比较投资安全控制 vs 避免的潜在损失。

------

### 🎯 **5. TARA**

> **Threat Agent Risk Assessment** — 来自 MITRE

- 基于威胁建模（threat agent profiling）的方法
- 按 **攻击者能力/意图 + 攻击路径 + 缺口** 优先筛选风险
- 常配合 MITRE ATT&CK、CAPEC 使用

📌 **举例：** 某国防供应商希望防御特定APT组织 → 用 TARA 针对攻击者画像进行风险建模。

| 目标导向 | 框架         | 关键词助记                        |
| -------- | ------------ | --------------------------------- |
| 企业战略 | **COSO ERM** | CFO & CEO 看的框架（重治理）      |
| IT治理   | **Risk IT**  | 和 COBIT 最搭，关注IT对业务的影响 |
| 组织资产 | **OCTAVE**   | 从业务角度识别风险，自上而下      |
| 定量决策 | **FAIR**     | 用钱衡量风险，和 CFO 说话用的     |
| 威胁画像 | **TARA**     | 专打黑客/APT，用威胁情报驱动决策  |

## Social Engineering

Social engineering is a form of attack that exploits human nature and human behavior.

People are a weak link in security because they can make mistakes, be fooled into causing harm, or intentionally violate company security.

It is important to consider the risks that personnel represent to your organization and implement security strategies to minimize and handle those risks.

**Social engineering attacks** take two primary forms: 

- convincing someone to perform an unauthorized operation 
- convincing someone to reveal confidential information.

