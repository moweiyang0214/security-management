# Protecting Security of Assets

- Domain 2.0: Asset Security

## Identifying and Classifying Information and Assets

Managing the data lifecycle refers to protecting it from when it is first created until it is destroyed.

One of the first steps in the lifecycle is identifying and classifying information and assets. Organizations often include classification definitions within a security policy. Personnel then label assets appropriately based on the security policy requirements. 

In this context, assets include sensitive data, the hardware used to process it, and the media used to hold it.

### Defining Sensitive Data

Sensitive data is any information that isn’t public or unclassified. It can include confidential, proprietary, protected, or any other type of data that an organization needs to protect due to its value to the organization, or to comply with existing laws and regulations.

#### PII (Personally Identifiable Information)

Personally identifiable information (PII) is any information that can identify an individual. National Institute of Standards and Technology (NIST) Special Publication (SP) 800-122 provides a more formal definition:

>  Any information about an individual maintained by an agency, including

- (1) any information that can be used to distinguish or trace an individual’s identity, such as name, social security number, date and place of birth, mother’s maiden name, or biometric records; and

- (2) any other information that is linked or linkable to an individual, such as medical, educational, financial, and employment information.

The key is that organizations have a responsibility to protect PII. This includes PII related to employees and customers. Many laws require organizations to notify individuals if a data breach results in a compromise of PII.

Protection for personally identifiable information (PII) drives privacy and confidentiality requirements for rules, regulations, and legislation worldwide. NIST SP 800-122, Guide to Protecting the Confidentiality of Personally Identifiable Information (PII), provides more information on how to protect PII.

#### Protected Health Information

Protected health information (PHI) is any health-related information that can be related to a specific person. In the United States, the Health Insurance Portability and Accountability Act (HIPAA) mandates PHI protection. HIPAA provides a more formal definition of PHI:

>  Health information means any information, whether oral or recorded in any form or medium, that—

- (A) is created or received by a health care provider, health plan, public health authority, employer, life insurer, school or university, or health care clearinghouse; and

- (B) relates to the past, present, or future physical or mental health or condition of any individual, the provision of health care to an individual, or the past, present, or future payment for the provision of health care to an individual.

HIPAA defines PHI much more broadly than only medical care providers, such as doctors and hospitals. Any employer that provides, or supplements, healthcare policies collects and handles PHI. It’s common for organizations to provide or supplement healthcare policies, so HIPAA applies to a large percentage of organizations in the United States.

#### Proprietary Data

Proprietary data refers to any data that helps an organization maintain a competitive edge. It could be software code it developed, technical plans for products, internal processes, intellectual property, or trade secrets. If competitors can access the proprietary data, it can seriously affect the primary mission of an organization.

Although copyrights, patents, and trade secret laws provide a level of protection for proprietary data, this isn’t always enough. Many criminals ignore copyrights, patents, and laws. Similarly, foreign entities have stolen a significant amount of proprietary data.

### Defining Data Classifications

Organizations typically include data classifications in their security policy or a data policy. A data classification identifies the value of the data to the organization and is critical to protect data confidentiality and integrity. The policy identifies classification labels used within the organization. It also identifies how data owners can determine the proper classification and how personnel should protect data based on its classification.

As an example, government data classifications include top secret, secret, confidential, and unclassified. Anything above unclassified is sensitive data, but clearly, these have different values. The U.S. government provides clear definitions for these classifications. As you read them, note that the wording of each definition is close except for a few key words. Top secret uses the phrase “exceptionally grave damage,” secret uses the phrase “serious damage,” and confidential uses “damage”:

1. **Top Secret** label is “applied to information, the unauthorized disclosure of which reasonably could be expected to cause exceptionally grave damage to the national security that the original classification authority is able to identify or describe.”
2. **Secret** label is “applied to information, the unauthorized disclosure of which reasonably could be expected to cause serious damage to the national security that the original classification authority is able to identify or describe".
3. **Confidential** label is “applied to information, the unauthorized disclosure of which reasonably could be expected to cause damage to the national security that the original classification authority is able to identify or describe.”
4. **Unclassified** refers to any data that doesn’t meet one of the descriptions for top secret, secret, or confidential data. Within the United States, unclassified data is available to anyone, though it often requires individuals to request the information using procedures identified in the **Freedom of Information Act (FOIA)**.

There are additional subclassifications of unclassified, such as **for official use only (FOUO)** and **sensitive but unclassified (SBU)**. Documents with these designations have strict controls limiting their distribution. As an example, the **U.S. Internal Revenue Service (IRS)** uses **SBU for individual tax records**, restricting access to these records.

A **classification authority** is the entity that applies the original classification to the sensitive data, and strict rules identify who can do so. For example, the U.S. president, vice president, and agency heads can classify data in the United States. Additionally, individuals in any of these positions can delegate permission for others to classify data.

An organization doesn’t just consider **the sensitivity of the data** but also **the criticality of the data**. They could use the same phrases of “exceptionally grave damage,” “serious damage,” and “damage” that the U.S. government uses when describing top secret, secret, and confidential data.

Some nongovernmental organizations use labels such as **Class 3, Class 2, Class 1, and Class 0.** Other organizations use more meaningful labels such as **confidential (or proprietary)**, **private, sensitive**, and **public**.

![image-20250526173232006](/Users/leiwang/Library/Application Support/typora-user-images/image-20250526173232006.png)

Both government and civilian classifications identify the relative value of the data to the organization, with top secret representing the highest classification for governments and confidential representing the highest classification for organizations.

The following sections identify the meaning of some common nongovernment classifications. Remember, even though these are commonly used, there is no standard that all private organizations must use.

1. **Confidential or Proprietary** label typically refers to the highest level of classified data. In this context, a data breach would cause exceptionally grave damage to the mission of the organization. As an example, attackers have repeatedly attacked Sony, stealing more than 100 terabytes of data, including full-length versions of unreleased movies. These quickly showed up on file-sharing sites, and security experts estimate that people downloaded these movies up to a million times. With pirated versions of the movies available, many people skipped seeing them when Sony ultimately released them. This directly affected Sony’s bottom line. The movies were proprietary, and the organization might have considered it exceptionally grave damage. In retrospect, they may choose to label movies as confidential or proprietary and use the strongest access controls to protect them.
2. **Private** label refers to data that should stay private within the organization but that doesn’t meet the definition of confidential or proprietary data. In this context, a data breach would cause serious damage to the mission of the organization. Many organizations label PII and PHI data as private. It’s also common to label internal employee data and some financial data as private. As an example, the payroll department of a company would have access to payroll data, but this data is not available to regular employees.
3. **Sensitive** data is similar to confidential data. In this context, a data breach would cause damage to the mission of the organization. As an example, IT personnel within an organization might have extensive data about the internal network, including the layout, devices, operating systems, software, Internet Protocol (IP) addresses, and more. If attackers have easy access to this data, it makes it much easier for them to launch attacks. Management may decide they don’t want this information available to the public, so they might label it as sensitive.
4. **Public** data is similar to unclassified data. It includes information posted in websites, brochures, or any other public source. Although an organization doesn’t protect the confidentiality of public data, it does take steps to protect its integrity. For example, anyone can view public data posted on a website. However, an organization doesn’t want attackers to modify this data, so it takes steps to protect it.

 No matter what labels an organization uses, it still has an obligation to protect sensitive information.

After classifying the data, an organization takes additional steps to manage it based on its classification. Unauthorized access to sensitive information can result in significant losses to an organization. However, basic security practices, such as properly marking, handling, storing, and destroying data and hardware assets based on classifications, helps prevent losses.

### Defining Asset Classifications

**Asset classifications should match the data classifications**. In other words, if a computer is processing top secret data, the computer should also be classified as a top secret asset. Similarly, if media such as internal or external drives hold top secret data, the media should also be classified as top secret.

It is common to use clear marking on the hardware assets so that personnel are reminded of data that can be processed or stored on the asset. For example, if a computer is used to process top secret data, the computer and the monitor will have clear and prominent labels reminding users of the classification of data that can be processed on the computer.

### Understanding Data States

It’s important to protect data in all data states, including while it is at rest, in motion, and in use.

- **Data at Rest**  (sometimes called **data on storage**) is any data stored on media such as system hard drives, solid-state drives (SSDs), external USB drives, storage area networks (SANs), and backup tapes. Strong symmetric encryption protects data at rest.
- **Data in transit** (sometimes called **data in motion** or being communicated) is any data transmitted over a network. This includes data transmitted over an internal network using wired or wireless methods and data transmitted over public networks such as the internet. A combination of symmetric and asymmetric encryption protects data in transit.
- **Data in use**  (also known as data being processed) refers to data in memory or temporary storage buffers while an application is using it. Applications often decrypt encrypted data before placing it in memory. This allows the application to work on it, but it’s important to flush these buffers when the data is no longer needed. In some cases, it’s possible for an application to work on encrypted data using homomorphic encryption. This limits the risk because memory doesn’t hold unencrypted data.

The best way to protect the confidentiality of data is to use strong encryption protocols, Additionally, strong authentication and authorization controls help prevent unauthorized access.

As an example, consider a web application that retrieves credit card data for quick access and reuse with the user’s permission for an ecommerce transaction. The credit card data is stored on a database server and protected while **at rest**, while **in transit**, and while **in use**.

Database administrators take steps to encrypt sensitive data stored on the database server (data at rest). They would typically **encrypt columns holding sensitive data** such as credit card data. Additionally, they would **implement strong authentication and authorization** controls to prevent unauthorized entities from accessing the database.

#### Determining Compliance Requirements

Some organizations have created a formal position called a compliance officer. The person filling this role ensures that the organization is conducting all business activities by following the laws and regulations that apply to the organization. Of course, this starts by first determining everywhere the organization operates, and what compliance requirements apply.

#### Determining Data Security Controls

After defining data and asset classifications, you must define the security requirements and identify security controls to implement those requirements. Management then decides on a data security policy dictating the use of specific security controls to protect data in these categories. The policy will likely address data stored in files, in databases, on servers such as email servers, on user systems, sent via email, and stored in the cloud.

Encryption converts cleartext data into scrambled ciphertext and makes it more difficult to read. Using strong encryption methods such as Advanced Encryption Standard with 256bit keys (AES 256) makes it almost impossible for unauthorized personnel to read the text.

![image-20250526204852438](/Users/leiwang/Library/Application Support/typora-user-images/image-20250526204852438.png)

Security administrators use the requirements defined in the security policy to identify security controls. Administrators should identify methodologies, making it easy for employees to meet the requirements.

Although it’s possible to meet all the requirements for securing email shown in Table 5.1, doing so might require implementing other solutions. For example, several software companies sell a range of products that organizations can use to automate these tasks. Users apply relevant labels (such as confidential, private, sensitive, and public) to emails before sending them. These emails pass through a **data loss prevention (DLP) server** that **detects the labels and applies the required protection**. The settings for these DLP solutions can be configured for an organization’s specific needs.

you should define requirements for data stored on assets such as servers, data backups stored onsite and offsite, and proprietary data.

Additionally, identity and access management security controls help ensure that only authorized personnel can access resources.

## Establishing Information and Asset Handling Requirements

A key goal of managing sensitive data is to prevent data breaches. A data breach is an event in which an unauthorized entity can view or access sensitive data. If you pay attention to the news, you probably hear about data breaches quite often. Large data breaches such as the Marriott data breach of 2020 hit the mainstream news. Marriott reported that attackers stole personal data, including names, addresses, email addresses, employer information, and phone numbers, of approximately 5.2 million guests.

#### Data Maintenance

Data maintenance refers to ongoing efforts to organize and care for data throughout its lifetime. In general, if an organization stores all sensitive data on one server, it is relatively easy to apply all the appropriate controls to this one server. In contrast, if sensitive data is stored throughout an organization on multiple servers and end-user computers and mixed with nonsensitive data, it becomes much harder to protect it.

**One network processes unclassified data only. Another network processes classified data.** Techniques such as air gaps ensure the two networks never physically touch each other. An air gap is a physical security control and means that systems and cables from the classified network never physically touch systems and cables from the unclassified network. Additionally, the classified network can’t access the internet, and internet attackers can’t access it.

Still, there are times when personnel need to add data to the classified network, such as when devices, systems, and applications need updates. 

- One way is manual; personnel copy the data from the unclassified network to a USB device and carry it to the classified network. 
- Another method is to use a **unidirectional network bridge; this connects the two networks but allows the data to travel in only one direction, from the unclassified network to the classified network**.
-  A third method is to **use a technical guard solution**, which is a combination of hardware and software placed between the two networks. **A guard solution allows properly marked data to travel between the two networks.**

Additionally, an organization should routinely review data policies to ensure that they are kept up to date and that personnel are following the policies. It’s often **a good practice to review the causes of recent data breaches and ensure that similar mistakes are not causing needless vulnerabilities.**

#### Data Loss Prevention

Data loss prevention (DLP) systems attempt to detect and block data exfiltration attempts. These systems have the capability of **scanning unencrypted data looking for keywords and data patterns**. For example, imagine that your organization uses data classifications of **Confidential**, **Proprietary**, **Private**, and **Sensitive**. **A DLP system can scan files for these words and detect them.**

Pattern-matching DLP systems look for specific patterns. For example, U.S. Social Security numbers have a pattern of nnn-nn-nnnn (three numbers, a dash, two numbers, a dash, and four numbers). The DLP can look for this pattern and detect it. Administrators can set up a DLP system to look for any patterns based on their needs. Cloud-based DLP systems can look for the same code words or strings.

There are two primary types of DLP systems:

1. **Network-Based DLP** scans all outgoing data looking for specific data. Administrators place it on the edge of the network to scan all data leaving the organization. If a user sends out a file containing restricted data, the DLP system will detect it and prevent it from leaving the organization. The DLP system will send an alert, such as an email to an administrator. Cloud-based DLP is a subset of network-based DLP.
2. **Endpoint-Based DLP** can scan files stored on a system as well as files sent to external devices, such as printers. For example, an organization’s endpoint-based DLP can prevent users from copying sensitive data to USB flash drives or sending sensitive data to a printer. Administrators configure the DLP to scan the files with the appropriate keywords, and if it detects files with these keywords, it will block the copy or print job. It’s also possible to configure an endpoint-based DLP system to regularly scan files (such as on a file server) for files containing specific keywords or patterns, or even for unauthorized file types, such as MP3 files.

DLP systems typically can perform deep-level examinations. For example, if users embed the files in compressed zip files, a DLP system can still detect the keywords and patterns. However, a **DLP system can’t decrypt data or examine encrypted data.**

##### Discovery capability

Most DLP solutions also include discovery capabilities. **The goal is to discover the location of valuable data within an internal network.** When security administrators know where the data is, they can take additional steps to protect it. As an example, a database server may include unencrypted credit card numbers. When the DLP discovers and reports this, database administrators can ensure the numbers are encrypted. As another example, company policy may dictate that employee laptops do not contain any PII data. A DLP content discovery system can search these and discover any unauthorized data. Additionally, many content discovery systems can search cloud resources used by an organization.

#### Marking Sensitive Data and Assets

**Marking (or labeling)** **sensitive information** ensures that users can easily identify the classification level of any data. The most important information that a mark or a label provides is the classification of the data. For example, a label of top secret makes it clear to anyone who sees the label that the information is classified top secret. When users know the value of the data, they are more likely to take appropriate steps to control and protect it based on the classification. Marking includes both physical and electronic marking and labels.

**Physical labels** indicate the security classification for the data stored on assets such as media or processed on a system. For example, if a backup tape includes secret data, a physical label attached to the tape makes it clear to users that it holds secret data.

Similarly, if a computer processes sensitive information, the computer would have a label indicating the highest classification of information that it processes. A computer used to process confidential, secret, and top secret data should be marked with a label indicating that it processes top secret data. Physical labels remain on the system or media throughout its lifetime.

Marking also includes using digital marks or labels. A simple method is to include the classification as a **header or footer** in a document or embed it as a **watermark**. A benefit of these methods is that they also appear on printouts. Even when users include headers and footers on printouts, most organizations require users to place printed sensitive documents within a folder that includes a label or cover page clearly indicating the classification. Headers aren’t limited to files. Backup tapes often include header information, and the classification can be included in this header.

Another benefit of headers, footers, and watermarks is that DLP systems can identify documents that include sensitive information and apply the appropriate security controls. Some DLP systems will also add metadata tags to the document when they detect that the document is classified. These tags provide insight into the document’s contents and help the DLP system handle it appropriately.

Similarly, some organizations mandate specific desktop backgrounds on their computers. For example, a system used to process proprietary data might have a black desktop background with the word Proprietary in white and a wide orange border. **The background could also include statements such as “This computer processes proprietary data”** and statements reminding users of their responsibilities to protect the data.

Organizations often identify procedures to downgrade media. For example, if a backup tape includes confidential information, an administrator might want to downgrade the tape to unclassified. The organization would identify trusted procedures that will **purge（净化/高强度清除） ** the tape of all usable data. After administrators purge the tape, they can then downgrade it and replace the labels.

However, many organizations prohibit downgrading media at all. For example, a data policy might prohibit downgrading a backup tape that contains top secret data. Instead, the policy might mandate destroying this tape when it reaches the end of its lifecycle. Similarly, it is rare to downgrade a system. In other words, if a system has been processing top secret data, it would be rare to downgrade it and relabel it as an unclassified system. In any event, approved procedures would need to be created to inform personnel what can be downgraded and what should be destroyed.

Note: If media or a computing system needs to be downgraded to a less sensitive classification, it must be sanitized using appropriate procedures.

#### Handling Sensitive Information and Assets

Handling refers to the secure transportation of media through its lifetime. Personnel handle data differently based on its value and classification, and as you’d expect, highly classified information needs much greater protection. Even though this is common sense, people still make mistakes. Many times, people get accustomed to handling sensitive information and become lackadaisical about protecting it.

A common occurrence is the loss of control of backup tapes. Backup tapes should be protected with the same level of protection as the data that they contain. In other words, if confidential information is on a backup tape, the backup tape should be protected as a confidential asset.

Policies and procedures need to be in place to ensure that people understand how to handle sensitive data. This starts by ensuring that systems and media are labeled appropriately. Logging, monitoring, and auditing verify that sensitive information is handled appropriately before a significant loss occurs. If a loss does occur, investigators use audit trails to help discover what went wrong. Any incidents that occur because personnel didn’t handle data appropriately should be quickly investigated and actions taken to prevent a reoccurrence.

#### Data Collection Limitation

**One of the easiest ways to prevent the loss of data is to simply not collect it.** As an example, consider a small ecommerce company that allows customers to make purchases with a credit card. It uses a credit card processor to process credit card payments. If the company just passes the credit card data to the processor for approval and never stores it in a company server, the company can never lose the credit card data in a breach.

In contrast, imagine a different ecommerce company sells products online. Every time a customer makes a purchase, the company collects as much information as possible on the customer, such as the name, email address, physical address, phone number, credit card data, and more. It suffers a data breach and all this data is exposed, resulting in significant liabilities for the company.

The guideline is clear. **If the data doesn’t have a clear purpose for use, don’t collect it and store it.** This is also why many privacy regulations mention limiting data collection.

#### Data Location

Data location refers to the location of data backups or data copies. Imagine a small organization’s primary business location is in Norfolk, Virginia. The organization stores all the data on site. However, they regularly perform backups of the data.

A best practice is to keep a backup copy on site and another backup copy off site. If a disaster, such as a fire, destroys the primary business location, the organization would still have a backup copy stored off site.

Some organizations maintain data in large data centers. It’s common to replicate this data to one or more other data centers to maintain the availability of the critical data. These data centers are typically located in separate geographical locations. When using cloud storage for backups, some organizations may need to verify the location of the cloud storage to ensure it is in a separate geographical location.

#### Storing Sensitive Data

Sensitive data should be stored in such a way that it is protected against any type of loss. Encryption methods prevent unauthorized entities from accessing the data even if they obtain databases or hardware assets.

If sensitive data is stored on physical media such as portable disk drives or backup tapes, personnel should follow basic physical security practices to prevent losses due to theft. This includes storing these devices in locked safes or vaults, or within a secure room that includes several additional physical security controls. For example, a server room includes physical security measures to prevent unauthorized access, so storing portable media within a locked cabinet in a server room would provide strong protection.

Additionally, environmental controls protect the media. This includes **temperature** and **humidity** controls such as **heating**(供暖), **ventilation(通风)**, and **air-conditioning(空调) (HVAC)** systems.

Here’s a point that end users often forget: the value of any sensitive data is much greater than the value of the media holding the sensitive data. In other words, it’s cost-effective to purchase high-quality media, especially if the data will be stored for a long time, such as on backup tapes. Similarly, the purchase of **high-quality USB flash drives with built-in encryption is worth the cost**. Some of these **USB flash drives include biometric authentication mechanisms using fingerprints, which provide added protection.**

Note：Encryption of sensitive data provides an additional layer of protection and should be considered for any data at rest. If data is encrypted, it becomes much more difficult for an attacker to access it, even if it is stolen.

#### Data Destruction

When an organization no longer needs sensitive data, personnel should destroy it. Proper destruction ensures that it cannot fall into the wrong hands and result in unauthorized disclosure. Highly classified data requires different steps to destroy it than data classified at a lower level. An organization’s security policy or **data policy should define the acceptable methods of destroying data based on the data’s classification.** For example, an organization may require the complete destruction of media holding highly classified data, but allow personnel to use software tools to overwrite data files classified at a lower level.

**NIST SP 800-88 Rev. 1,** “Guidelines for Media Sanitization,” provides comprehensive details on different sanitization methods. **Sanitization methods (such as clearing（清除）, purging（净化/高强度清除）, and destroying（销毁）)** help ensure that data cannot be recovered. Proper sanitization steps remove all sensitive data before disposing of a computer. This includes removing or destroying data on **nonvolatile memory（非易失性存储器）, internal hard drives（内部硬盘）, and solid-state drives (SSDs，固态硬盘).** It also includes removing all CDs/DVDs and Universal Serial Bus (USB) drives.

Sanitization can refer to the **destruction of media** or **using a trusted method to purge（净化/高强度清除） classified data from the media without destroying it**.

#### Eliminating Data Remanence

**Data remanence（数据残留）** is the data that remains on media after the data was supposedly erased.

It typically refers to data on a hard drive as **residual magnetic flux（残留磁通）** or **Slack Space（扇区簇未使用空间）**. If media includes any type of private and sensitive data, it is important to eliminate data remanence.

Some operating systems fill this slack space with data from memory. If a user was working on a top secret file a moment ago and then creates a small unclassified file, the small file might contain top secret data pulled from memory. This is one of the reasons why personnel should never process classified data on unclassified systems. Sophisticated users can also hide data within slack space using tools such as bmap (Linux) and slacker (Windows).

##### 删除 ≠ 清除 —— 数据残留的风险

虽然系统提供的“删除”或“清空回收站”功能看起来数据没了，但：

- 实际上**只是删除了“索引”或“引用”**，原始数据仍存在于磁盘上。
- 即使使用工具将数据“覆盖”，**磁性介质上仍可能存在微弱残影**，这种“鬼影”就像老式显示器上长时间显示相同画面后留下的残像。
- **数字取证工具（如 FTK、Autopsy）**能恢复这些数据，攻击者也能利用。

Using system tools to delete data generally leaves much of the data remaining on the media, and widely available tools can easily undelete it. Even when you use sophisticated tools to overwrite the media, traces of the original data may remain as less perceptible magnetic fields. This is like a ghost image that can remain on some older TV and computer monitors if the same data is displayed for long periods of time. Forensics experts and attackers have tools they can use to retrieve this data even after it has been supposedly overwritten.

One way to remove data remanence is with a **degausser**. A degausser generates a heavy magnetic field, which realigns the magnetic fields in magnetic media such as traditional hard drives, magnetic tape, and floppy disk drives. Degaussers using power will reliably rewrite these magnetic fields and remove data remanence. However, they are only effective on magnetic media.

##### Degaussing（消磁）适用于磁性存储

消磁器（degausser）是处理传统磁性介质的有效手段：

| ⚙️ 原理       | 生成强磁场，干扰原始数据磁性排列，使其不可恢复 |
| ------------ | ---------------------------------------------- |
| 🎯 适用对象   | 磁带、传统硬盘（HDD）、软盘                    |
| ❌ 不适用对象 | **固态硬盘（SSD）**，因其非磁性，不受磁场影响  |

🧠 **结论**：你不能用消磁器“清除”SSD 数据。

In contrast, SSDs use integrated circuitry instead of magnetic flux on spinning platters. Because of this, degaussing SSDs won’t remove data. However, even when using other methods to remove data from SSDs, data remnants often remain.

Some SSDs include built-in erase commands to sanitize the entire disk, but unfortunately, these weren’t effective on some SSDs from different manufacturers. Due to these risks, the best method of sanitizing SSDs is destruction. The U.S. National Security Agency (NSA) requires the destruction of SSDs using an approved disintegrator. Approved disintegrators shred the SSDs to a size of 2 millimeters (mm) or smaller. Many organizations sell multiple information destruction and sanitization solutions used by government agencies and organizations in the private sector that the NSA has approved.

##### 为什么 SSD 更难清除？

固态硬盘（SSD）使用**集成电路**存储数据而非磁性盘片：

- 虽然有些 SSD 提供**内建的擦除命令（如 ATA Secure Erase）**，但**不同厂商实现不同，不一定可靠**。
- 即使你“格式化”或“安全删除”，**仍可能残留数据碎片（remnants）**。
- 因此，美国国家安全局（NSA）**不信任逻辑删除方法**，要求对 SSD **物理破坏**。

Another method of protecting SSDs is to ensure that all stored data is encrypted. If a sanitization method fails to remove all the data remnants, the remaining data would be unreadable.

##### NSA 推荐的销毁方法：Disintegration（粉碎）

| 方法          | 描述                                                   |
| ------------- | ------------------------------------------------------ |
| NSA认证销毁器 | 一种“粉碎器”，能将 SSD **物理切割成 2mm 或更小的颗粒** |
| 适用场景      | 涉密单位（如政府机构）、需彻底消除敏感数据的商业场景   |

💡 一些厂商提供**NSA认证的硬件设备**，也面向企业销售。

##### 额外保护：数据加密 + 清除

由于 SSD 擦除存在不确定性，一种**更保险的做法**是：

1. **平时数据加密**（全盘加密，如 BitLocker、VeraCrypt）
2. 清除时只需销毁密钥或覆盖密钥存储区域

✨ 即使残留数据仍存在，也**无法解密**，自然“安全无用”。

总结：

| 类型                       | 优点             | 缺点          | 是否适合SSD |
| -------------------------- | ---------------- | ------------- | ----------- |
| 删除/格式化                | 快速、方便       | 容易恢复      | ❌           |
| 覆盖工具                   | 可处理 HDD       | 对 SSD 不稳定 | ❌           |
| 消磁（Degauss）            | 彻底摧毁磁性数据 | 无效于 SSD    | ❌           |
| 物理粉碎（Disintegration） | 最彻底           | 成本高        | ✅ 推荐      |
| 加密 + 删除密钥            | 高效、安全       | 依赖加密强度  | ✅ 推荐      |

Be careful when performing any type of clearing, purging, or sanitization process. The human operator or the tool involved in the activity may not properly perform the task of completely removing data from the media. Software can be flawed, magnets can be faulty, and either can be used improperly. Always verify that the desired result is achieved after performing any sanitization process.

#### Common Data Destruction Methods

The following list includes some common terms associated with destroying data:

1. **Erasing（抹除）** media is simply performing a delete operation against a file, a selection of files, or the entire media. In most cases, the deletion or removal process removes only the directory or catalog link to the data. The actual data remains on the drive. As new files are written to the media, the system eventually overwrites the erased data, but depending on the size of the drive, how much free space it has, and several other factors, the data may not be overwritten for months. Anyone can typically retrieve the data using widely available undelete tools.
2. **Clearing or overwriting（重写覆盖）** is a process of preparing media for reuse and ensuring that the cleared data cannot be recovered using traditional recovery tools. When media is cleared, unclassified data is written over all addressable locations on the media. One method writes a single character, or a specific bit pattern, over the entire media. A more thorough method writes a single character over the entire media, writes the character’s complement over the entire media, and finishes by writing random bits over the entire media. It repeats this in three separate passes, as shown in Figure 5.2. Although this sounds like the original data is lost forever, it may be possible to retrieve some of the original data using sophisticated laboratory or forensics techniques. Additionally, not all types of data storage respond well to clearing techniques. For example, spare sectors on hard drives, sectors labeled as “bad,” and areas on many modern SSDs are not necessarily cleared and may still retain data.
3. **Purging（净化/高强度清除）** is a more intense form of clearing that prepares media for reuse in less secure environments. It provides a level of assurance that the original data is not recoverable using any known methods. A purging process will repeat the clearing process multiple times and may combine it with another method, such as degaussing, to completely remove the data. Even though purging is intended to remove all data remnants, it isn’t always trusted. For example, the U.S. government doesn’t consider any purging method acceptable to purge top secret data. Media labeled top secret will always remain top secret until it is destroyed.
4. **Degaussing（消磁）** A degausser creates a strong magnetic field that erases data on some media in a process called degaussing. Technicians commonly use degaussing methods to remove data from magnetic tapes with the goal of returning the tape to its original state. It is possible to degauss hard disks, but we don’t recommend it. Degaussing a hard disk will normally destroy the electronics used to access the data. However, you won’t have any assurance that all the data on the disk has actually been destroyed. Someone could open the drive in a clean room and install the platters on a different drive to read the data.
   - Degaussing does not affect optical CDs, DVDs, or SSDs.
5. **Destruction（销毁）** is the final stage in the lifecycle of media and is the most secure method of sanitizing media. When destroying media, ensure that the media cannot be reused or repaired and that data cannot be extracted from the destroyed media. Methods of destruction include incineration, crushing, shredding, disintegration, and dissolving using caustic or acidic chemicals. Some organizations remove the platters in highly classified disk drives and destroy them separately.

**Declassification** involves any process that purges media or a system in preparation for reuse in an unclassified environment. Sanitization methods can be used to prepare media for declassification, but often the efforts required to securely declassify media are significantly greater than the cost of new media for a less secure environment. Additionally, even though purged data is not recoverable using any known methods, there is a remote possibility that an unknown method is available. Instead of taking the risk, many organizations choose not to declassify any media and instead destroy it when it is no longer needed.

#### Cryptographic Erasure（加密抹除）

Cryptographic Erasure 是一种**通过摧毁加密密钥来让数据无法访问**的方法，而不是实际删除数据本身。

**加密抹除**通过**销毁密钥**来“使数据失效”，是一种**逻辑删除方法**

- 📌 **原理**：数据原本已被加密 → 删除加密密钥 → 即使数据仍存在，**也无法解密访问**
- 📌 **类比**：你锁了一个箱子，把钥匙销毁，箱子内容就“不可用”了

使用时需确保：

- 使用**强加密**
- **销毁所有密钥副本**
- 可结合其他方法增强安全性（如数据覆写）

是云环境下**最实用、少数可行的“安全删除”手段**

If data is encrypted on a device, it’s possible to use cryptographic erasure or cryptoshredding to destroy the data. However, these terms are misleading. They don’t erase or shred the data. Instead, they destroy the encryption key, or both the encryption key and decryption key if two are used. With the cryptographic keys erased, data remains encrypted and can’t be accessed.

##### 特点分析

| 特性             | 描述                                             |
| ---------------- | ------------------------------------------------ |
| 🔐 不直接删除数据 | 数据仍保留在存储介质中，只是**失去了可用性**     |
| 🚫 销毁加密密钥   | 一旦密钥被删除或销毁，数据就无法解密             |
| ✅ 快速高效       | 相比物理粉碎或全盘覆写，速度更快、资源更少       |
| ☁️ 常用于云环境   | 在云存储中尤其适用，因为无法访问硬件进行传统擦除 |

When using this method, you should use another method to overwrite the data. If the original encryption isn’t strong, someone may be able to decrypt it without the key. Additionally, there are often backups of cryptographic keys, and if someone discovers a backup key, they can still access the data.

##### ⚠️ 注意事项和风险

虽然是一个“高效逻辑删除”方案，但仍有风险和注意点：

1. **原始加密必须足够强**：
   - 如果加密算法较弱，攻击者可能**暴力破解数据**。
   - 推荐使用**AES-256等强加密算法**。
2. **需搭配物理覆盖更安全**：
   - 如果担心加密数据泄漏，最好再执行**覆盖操作**（如填零、写随机值）。
3. **必须销毁所有密钥备份**：
   - 组织可能有加密密钥的备份。
   - 如果攻击者拿到备份密钥，数据仍可被访问。

When using cloud storage, destroying the cryptographic keys may be the only form of secure deletion available to an organization.

##### ☁️ 云存储中的应用价值

在**云环境**中（如 AWS、Azure、Google Cloud）：

- 用户无法控制物理磁盘，因此传统的“物理粉碎”无法实施。
- 云服务提供商通常使用**加密抹除（Cryptographic Erasure）作为删除手段**。
- 一旦销毁主密钥，服务商也无法恢复数据，符合**GDPR、HIPAA等合规性要求**。

#### Ensuring Appropriate Data and Asset Retention

Retention（数据保留）requirements apply to data or records, media holding sensitive data, systems that process sensitive data, and personnel who have access to sensitive data. Record retention and media retention is the most important element of asset retention.

**Retention（保留）要求**适用于：

- 各类数据和记录（如审计日志、邮件）
- 储存敏感数据的介质（如磁带、硬盘）
- 处理敏感数据的系统
- 接触敏感数据的人员记录（如员工账户活动日志）

关键目标：**保留有用的数据、销毁无用的数据，控制成本、规避风险、符合法律。**

Record retention involves retaining and maintaining important information as long as it is needed and destroying it when it is no longer needed. An organization’s security policy or data policy typically **identifies retention time frames.** Some laws and regulations dictate the length of time that an organization should retain data, such as three years, seven years, or even indefinitely. Organizations have the responsibility of identifying laws and regulations that apply and complying with them. However, even in the absence of external requirements, an organization should still identify how long to retain data.

As an example, many organizations require the retention of all audit logs for a specific amount of time. The period can be dictated by laws, regulations, requirements related to partnerships with other organizations, or internal management decisions. These audit logs allow the organization to reconstruct the details of past security incidents. When an organization doesn’t have a retention policy, administrators may delete valuable data earlier than management expects them to or attempt to keep data indefinitely. The longer an organization retains data, the more it costs in terms of media, locations to store it, and personnel to protect it.

##### ✅ 为什么要保留？

- **符合法律法规**：例如金融、医疗或政府相关数据要求保留3年、7年甚至永久。
- **追踪安全事件**：如审计日志可用于回溯分析入侵或泄露。
- **业务连续性**：恢复历史配置、应对调查和合规审核。

##### ⛔ 不保留的风险：

- 删除太早：重要证据、合规记录被破坏。
- 保留太久：增加存储成本、管理负担、**法律负担增加**。

**End-of-life (EOL), end-of-support (EOS), and end-of-service-life (EOSL)** can apply to either software or hardware. In the context of asset retention, they apply directly to hardware assets. Most vendors refer to EOL as the time when they stop offering a product for sale. However, they will still support the products they’ve sold, at least for a while. EOS refers to the time when this support ends. Most hardware is on a refresh cycle based on the EOL and EOS time frames. Organizations sometimes retain legacy hardware to access older data, such as data on tape drives.

##### 与硬件相关的术语

| 术语                            | 意义         | 说明                                       |
| ------------------------------- | ------------ | ------------------------------------------ |
| **EOL（End of Life）**          | 停止销售     | 供应商不再出售产品，但可能继续支持一段时间 |
| **EOS（End of Support）**       | 停止支持     | 不再提供技术支持、补丁或更新               |
| **EOSL（End of Service Life）** | 服务寿命终止 | 通常意味着不能再使用该产品处理关键任务     |

组织可能会保留老旧硬件（如磁带机）用于读取历史数据。但应评估这些资产的安全性和兼容性。

##### Retention Policies Can Reduce Liabilities

**Saving data longer than necessary also presents unnecessary legal issues.** As an example, aircraft manufacturer Boeing was once the target of a class action lawsuit. Attorneys for the claimants learned that Boeing had a warehouse filled with 14,000 email backup tapes and demanded the relevant tapes. Not all the tapes were relevant to the lawsuit, but Boeing had to first restore the 14,000 tapes and examine the content before they could turn them over. Boeing ended up settling the lawsuit for $92.5 million, and analysts speculated that there would have been a different outcome if those 14,000 tapes hadn’t existed.

The Boeing lawsuit is an extreme example, but it’s not the only one. These events have prompted many companies to implement aggressive email retention policies. It is not uncommon for an email policy to require the deletion of all emails older than six months. These policies are often implemented using automated tools that search for old emails and delete them without any user or administrator intervention.

A company cannot legally delete potential evidence after a lawsuit is filed. However, if a retention policy dictates deleting data after a specific amount of time, it is legal to delete this data before any lawsuits have been filed. Not only does this practice prevent wasting resources to store unneeded data, it also provides an added layer of legal protection against wasting resources by looking through old, irrelevant information.

##### 📌 总结：Retention 是信息治理的核心策略

- 不仅仅是“存 vs 删”，而是平衡：
  - **合规性**
  - **成本**
  - **业务需求**
  - **法律风险**
- 最佳实践是：**设定保留策略 + 自动化删除机制 + 审计记录留痕**

## Data Protection Methods

#### Digital Rights Management（数字版权管理）

**Digital rights management (DRM)** methods attempt to provide copyright protection for copyrighted works. The purpose is to prevent the unauthorized use, modification, and distribution of copyrighted works such as intellectual property. 

**Digital Rights Management（数字版权管理）** 是一组技术和策略，用来控制对数字内容（如音乐、电影、电子书、软件等）的**访问、使用、复制和分发**。目的是 **防止未经授权的使用和盗版**，从而保护著作权人和版权所有者的权益。

Here are some methods associated with DRM solutions:

1. **DRM License** A license grants access to a product and defines the terms of use. A DRM license is typically a small file that includes the terms of use, along with a decryption key that unlocks access to the product.
2. **Persistent Online Authentication** (also known as always-on DRM) requires a system to be connected with the internet to use a product. The system periodically connects with an authentication server, and if the connection or authentication fails, DRM blocks the use of the product.
3. **Continuous Audit Trail** A continuous audit trail tracks all use of a copyrighted product. When combined with persistence, it can detect abuse, such as concurrent use of a product simultaneously but in two geographically different locations.
4. **Automatic Expiration** Many products are sold on a subscription basis. For example, you can often rent new streaming movies, but these are only available for a limited time, such as 30 days. When the subscription period ends, an automatic expiration function blocks any further access.

##### DRM 的常见方法与机制

1. **DRM License（授权文件）**

- DRM 使用一种小型的数字许可证文件来限制内容的使用方式。
- 包含：
  - 使用条款（如“只能播放 5 次”）
  - 解密密钥（用来解锁内容）
- 没有密钥或授权许可，用户无法访问内容。

2. **Persistent Online Authentication（持续在线验证）**

- 又称“Always-On DRM”，即“总是在线的 DRM”。
- 内容使用时需要持续联网并通过验证服务器确认合法性。
- 一旦无法验证（如断网、验证失败），内容将无法访问。
- 常用于**云游戏**、**SaaS 软件**、**数字视频服务（如 Netflix）**。

3. **Continuous Audit Trail（连续审计跟踪）**

- 记录内容使用的完整日志，包括时间、地点、频率等。
- 可用于发现异常使用，如：
  - 同一账号在美国和欧洲同时播放电影
- 用于版权保护、违规行为分析及取证。

4. **Automatic Expiration（自动过期机制）**

- 常见于**租赁模式**的数字商品（如新上映电影）。
- 内容在 30 天内可观看，或点播后只能保留 48 小时。
- 过期后 DRM 自动锁定，阻止访问。

**DRM methods are used to protect copyrighted data, but they aren’t used to protect trademarks, patents, or trade secrets.**

Some DRM methods attempt to prevent the copying, printing, and forwarding of protected materials. 

Digital watermarks are sometimes placed within audio or video files using steganography. They don’t prevent copying but can be used to detect the unauthorized copying of a file. They can also be used for copyright enforcement and prosecution. 

Similarly, metadata is sometimes placed into files to identify the buyer.

##### 📷 DRM 其他补充手段

**✅ 数字水印（Digital Watermarking）**

- 利用**隐写术**嵌入音频/视频中。
- 不阻止复制，但可以追踪内容源，识别泄漏来源。
- 用于版权执法和法律诉讼。

**✅ 元数据标记（Metadata Tagging）**

- 文件中嵌入用户信息（如购买人姓名、账户）。
- 即使文件被复制或篡改，仍可追踪原始购买者。

Many organizations and individuals are opposed to DRM. They claim it restricts the fair use of materials they purchase. For example, after paying for some songs, they want to copy them onto both an MP3 player and a smartphone. Additionally, people against DRM claim it isn’t effective against people that want to bypass it but instead complicates the usage for legitimate users.

虽然 DRM 旨在保护版权，但它也引起了大量批评：

**✴️ 合理使用受限**

- 用户购买内容后难以自由使用：
  - 拷贝到多个设备
  - 离线观看、离线听歌
  - 制作备份

**✴️ 正常用户体验受损**

- DRM 对黑客常常无效，但对普通用户限制却很大。
- 被认为“打击不了盗版者，却限制了合法用户”。

**✴️ 软件依赖性强**

- 必须依赖 DRM 平台运行，一旦平台关闭或服务中断，用户无法再访问自己购买的内容。

##### 总结

DRM 是知识产权保护的技术防线之一，但在实施中需要权衡**版权保护与用户体验**之间的关系。对信息安全专业人士而言，理解 DRM 不仅有助于支持合法内容使用，也有助于处理与内容管理相关的合规问题。

| 目标              | 实现机制                |
| ----------------- | ----------------------- |
| 限制访问权限      | 授权文件 + 解密密钥     |
| 防止盗版传播      | 持续在线验证 + 水印技术 |
| 控制使用次数/时效 | 自动过期控制            |
| 提供可追溯性      | 审计跟踪 + 用户标记     |

#### Cloud Access Security Broker

**CASB**（云访问安全代理）是一种部署在**用户与云服务之间**的软件安全控制点。它可以部署在：

- ✅ 本地（On-premises）
- ✅ 云中（Cloud-native）

所有访问云服务的请求 **必须先通过 CASB**，CASB 在中间起到安全网关的作用。

##### 🛡️ CASB 的主要功能

1. **强制执行安全策略**

- 例如：要求上传到云的数据必须是加密的。
- 管理员可定义加密、审计、访问控制等策略，由 CASB 实时执行。

2. **认证与授权控制**

- 验证用户身份（Authentication）
- 控制谁能访问哪些云资源（Authorization）

3. **日志记录与审计**

- CASB 会记录所有访问行为
- 可用于审计分析、取证调查

4. **异常检测与告警**

- 检测非正常行为（如异常登录位置、大流量下载）
- 触发预设告警机制

5. **复制企业内部安全机制**

- **如数据丢失防护**（DLP）、访问控制、加密策略、行为分析等

A cloud access security broker (CASB) is software placed logically between users and cloudbased resources. It can be on-premises or within the cloud. Anyone who accesses the cloud goes through the CASB software. It monitors all activity and enforces administrator-defined security policies.

As a simple example, imagine a company has decided to use a cloud provider for data storage but management wants all data stored in the cloud to be encrypted. The CASB can monitor all data going to the cloud and ensure that it arrives and is stored in an encrypted format.

A CASB would typically include authentication and authorization controls and ensure only authorized users can access the cloud resources. The CASB can also log all access, monitor activity, and send alerts on suspicious activity. In general, any security controls that an organization has created internally can be replicated to a CASB. This includes any DLP functions implemented by an organization.

CASB solutions can also be effective at detecting shadow IT. Shadow IT is the use of IT resources (such as cloud services) without the approval of, or even the knowledge of, the IT department. If the IT department doesn’t know about the usage, it can’t manage it. One way a CASB solution can detect shadow IT is by collecting and analyzing logs from network firewalls and web proxies.

##### CASB 与 Shadow IT

**Shadow IT** 指员工在未经 IT 部门批准的情况下擅自使用云服务、应用或系统。

**CASB 如何检测 Shadow IT？**

- 收集分析网络防火墙与代理服务器的访问日志
- 判断哪些云服务是“未经批准”的服务
- 检测非官方应用流量（如员工私自使用 Dropbox、WeTransfer 等）

这样能帮助 IT 安全团队发现：

- 隐藏的风险服务
- 企业数据是否被上传至不安全的平台

##### ✅ 主流 CASB 实现方式汇总

| 实现方式                                         | 描述与适用场景                                               |
| ------------------------------------------------ | ------------------------------------------------------------ |
| 1️⃣ API-based CASB                                 | 通过调用 SaaS 应用（如 O365、G Suite、Box、Salesforce）的 API 实现数据控制与监控 |
| 2️⃣ Proxy-based CASB                               | 使用反向代理或前向代理截取用户与云之间的流量，实现实时控制与内容审查 |
| 3️⃣ Agent-based CASB                               | 在终端设备部署代理程序，监控和限制云服务的访问，特别适合 BYOD 或无法控制网络路径的场景 |
| 4️⃣ OPA + Sidecar 模式                             | 在云原生或容器化环境中使用 Sidecar 与 OPA 实现细粒度访问控制与策略执行 |
| 5️⃣ 云厂商原生集成（如 Azure Defender, AWS Macie） | 借助公有云服务商提供的原生 CASB/安全控制功能，快速实现策略编排、威胁检测和数据保护 |

##### 具体实现方式解析

1. ✅ **API-based CASB（基于API）**

- **优点**：部署快、无需改动网络结构，适合管理已知的SaaS应用
- **厂商代表**：Microsoft Defender for Cloud Apps、Bitglass、Netskope、McAfee MVISION
- **功能示例**：
  - 审计 SaaS 应用行为（登录、上传、共享记录）
  - 控制敏感数据分享（如 DLP 规则阻止上传身份证、财务数据）
  - 强制多因素认证、阻止高风险国家访问

2. 🛡️ **Proxy-based CASB（代理模式）**

- **前向代理**：部署于用户网络出入口，对所有访问请求检查并重定向到 CASB
- **反向代理**：适用于只监控特定云服务（如 Salesforce）流量，在登录和访问时被拦截、审查
- **适用场景**：想实时控制流量/文件/行为，需要做内容检查（如病毒扫描、OCR、正则匹配）
- **挑战**：对 TLS 流量需做中间人解密；部署较复杂，对性能有一定影响

3. 💻 **Agent-based CASB（客户端代理）**

- 在员工电脑/移动设备上安装代理软件，强制使用 CASB 策略（即使在外部网络）
- **适合场景**：BYOD（自带设备）环境，尤其是公司无法控制用户网络流量的情况
- **风险/挑战**：设备管理成本高；部分员工或业务团队抗拒安装代理

4. 🔍 **OPA + Sidecar（云原生、容器场景）**

- 适用于微服务、大规模K8s平台、CI/CD环境下细粒度控制
- 和 DevSecOps、Zero Trust 深度融合
- 适合开发者主导的安全流程（GitOps、策略即代码）

5. ☁️ **云厂商原生安全工具**

- 如 Azure 的 Defender for Cloud、AWS Macie、Google CASB
- 优点：原生集成、易部署、自动关联账户和资源、合规报告丰富
- 局限：多云环境或第三方 SaaS 时功能覆盖不足

##### 🔄 选型建议

| 使用场景                              | 推荐实现方式                |
| ------------------------------------- | --------------------------- |
| 使用主流 SaaS，轻量合规、操作审计需求 | ✅ API-based CASB            |
| 高度敏感数据、需要实时阻断或内容审查  | ✅ Proxy-based（前向或反向） |
| 多设备接入、零信任访问控制需求        | ✅ Agent-based CASB          |
| DevOps 环境、微服务、大规模K8s        | ✅ OPA + Sidecar             |
| Azure/AWS/Google 内部系统为主         | ✅ 云厂商原生 CASB 工具      |

- **OPA + Sidecar** 是技术先进、可编程、安全粒度极高的一种现代化 CASB 实现方式，尤其适合云原生团队。
- 但 **API-based 和 Proxy-based** 依然是大多数组织落地 CASB 的“快速起步方案”，特别适合对主流 SaaS（如 Office 365、Google Workspace）进行统一治理。
- 最佳实践是 **结合多种方式**，构建一个覆盖全面、策略统一、可自动化的云访问安全体系。

##### CASB总结

| 功能类别       | CASB 的作用                        |
| -------------- | ---------------------------------- |
| 安全策略执行   | 控制上传数据加密、下载权限等       |
| 访问控制       | 身份验证和权限管理                 |
| 行为监控       | 日志记录、行为分析、异常告警       |
| Shadow IT 检测 | 发现和阻止未授权云服务使用         |
| 合规与审计     | 支持满足法规要求与企业内部合规需求 |

CASB 是现代云安全架构的重要组成部分，适用于越来越多使用 SaaS、PaaS、IaaS 服务的企业环境。

#### Pseudonymization（假名化）

**Pseudonymization（假名化）** 是一种**数据保护技术**，它将直接识别数据主体的个人信息（如姓名、地址、身份证号）用**假名（pseudonyms）**替代，从而使数据无法直接识别个人。

Pseudonymization refers to the process of using pseudonyms to represent other data. When pseudonymization is performed effectively, it can result in less stringent requirements that would otherwise apply under the European Union (EU) General Data Protection Regulation (GDPR).

Similarly, pseudonymization can prevent data from directly identifying an entity, such as a person. As an example, consider a medical record held by a doctor’s office. Instead of including personal information such as the patient’s name, address, and phone number, it could just refer to the patient as Patient 23456 in the medical record. The doctor’s office still needs this personal information, and it could be held in another database linking it to the patient pseudonym (Patient 23456).

Note that in the example, the pseudonym (Patient 23456) refers to several pieces of information on the person. It’s also possible for a pseudonym to refer to a single piece of information. For example, you can use one pseudonym for a first name and another pseudonym for a last name. The key is to have another resource (such as another database) that allows you to identify the original data using the pseudonym.

The doctor’s office can release pseudonymized data to medical researchers without compromising patients’ privacy information. However, the doctor’s office can still reverse the process to discover the original data if necessary.

The GDPR refers to pseudonymization as replacing data with artificial identifiers. These artificial identifiers are pseudonyms.

##### GDPR 中的 Pseudonymization 要点

欧盟通用数据保护条例（GDPR）中提到：

- 假名化可以作为**降低数据处理风险**的一种技术措施；
- 如果数据处理过程包括假名化，则某些GDPR义务可适当减轻；
- 假名化数据依然被视为**个人数据**，因为其可以被还原。

##### Pseudonymization 的优势

| 优势                       | 解释                       |
| -------------------------- | -------------------------- |
| 🔐 提高隐私保护             | 避免直接暴露个人身份信息   |
| 📉 降低合规风险             | 符合GDPR、HIPAA等法规要求  |
| 🤝 有利于数据共享与研究使用 | 在不暴露身份前提下共享数据 |
| 🔁 可逆（可重新识别）       | 可在授权情况下恢复原始数据 |

##### Pseudonymization vs Anonymization

| 特点     | Pseudonymization (假名化) | Anonymization (匿名化)   |
| -------- | ------------------------- | ------------------------ |
| 可逆性   | 是（可还原）              | 否（不可还原）           |
| GDPR分类 | 属于个人数据处理          | 不再属于个人数据         |
| 典型用途 | 医疗研究、隐私保护等      | 统计、报告等匿名数据使用 |

#### Tokenization

Tokenization is the use of a token, typically a random string of characters, to replace other data. It is often used with credit card transactions.

**Tokenization** 是一种将敏感数据（如信用卡号）替换为**随机生成的“Token”字符串**的过程。Token 在系统中作为代表原始数据的“代理”，但本身**不具备任何意义或可推断性**。

As an example, imagine Becky Smith has associated a credit card with her smartphone. Tokenization with a credit card typically works like this:

1. **Registration** When she first associated the credit card with her smartphone, an app on the phone securely sent the credit card number to a credit card processor. The credit card processor sent the credit card to a tokenization vault controlled by the credit card processor. The vault creates a token (a string of characters) and records the token along with the encrypted credit card number, and associates it with the user’s phone.
2. **Usage** Later, Becky goes to a Starbucks and buys some coffee with her smartphone. Her smartphone passes the token to the point-of-sale (POS) system. The POS system sends the token to the credit card processor to authorize the charge.
3. **Validation** The credit card processor sends the token to the tokenization vault. The vault answers with the unencrypted credit card data, and the credit card processor then processes the charge.
4. **Completing the Sale** The credit card processor sends a reply to the POS system indicating the charge is approved and credits the seller for the purchase.

##### 🏦 应用示例：信用卡支付流程

1. **注册阶段**：用户的信用卡号传给支付处理商，进入“Token Vault”（代币金库），生成 Token 并与加密后的信用卡号关联。
2. **消费阶段**：用户使用 Token 进行支付，POS 机不接触原始信用卡号。
3. **验证阶段**：支付处理商在 Vault 中验证 Token，取回解密后的信用卡号并完成交易。

📌 **核心特性：**

- POS系统从未接触信用卡号 → 降低攻击面
- Token 无法单独完成交易 → 限定绑定场景

In the past, credit card data has been intercepted and stolen at the POS system. However, when tokenization is used, the credit card number is never used or known to the POS system. The user transfers it once to the credit card processor, and the credit card processor stores an encrypted copy of the credit card data along with a token matched to this credit card. Later the user presents the token, and the credit card processor validates the token through the tokenization vault.

Ecommerce sites that have recurring charges also use tokenization. Instead of the ecommerce site collecting and storing credit card data, the site obtains a token from the credit card processor. The credit card processor creates the token, stores an encrypted copy of the credit card data, and processes charge the same way as it does for a POS system. However, the ecommerce site doesn’t hold any sensitive data. Even if an attacker obtained a token and tried to make a charge with it, it would fail because the charges are only accepted from the ecommerce site.

**🎯 用途扩展**

- **电子商务（e-commerce）定期支付**：Token 用于重复计费，但只有该电商平台有效。
- **数据隔离**：Token 只有生成它的系统知道其真实意义。

Tokenization is similar to pseudonymization. Pseudonymization uses pseudonyms to represent other data. Tokenization uses tokens to represent other data. Neither the pseudonym nor the token has any meaning or value outside the process that creates them and links them to the other data. Pseudonymization is most useful when releasing a dataset to a third party (such as researchers aggregating data) without releasing any privacy data to the third party. Tokenization allows a third party (such as a credit card processor) to know the token and the original data. However, no one else knows both the token and the original data.

#### Anonymization（匿名化）

**Anonymization** 是彻底删除或修改所有能识别个人身份的数据，**不可逆**，即数据不能被还原回原始状态。

If you don’t need personal data, another option is to use anonymization. Anonymization is the process of removing all relevant data so that it is theoretically impossible to identify the original subject or person. If done effectively, the GDPR is no longer relevant for the anonymized data. However, it can be difficult to truly anonymize the data. Data inference techniques may be able to identify individuals, even if personal data is removed. This is sometimes referred to as reidentification of anonymized data.

##### GDPR 中的应用

- **合规优势**：数据被匿名化后，**不再受GDPR监管**；
- **高风险点**：如果匿名化不足，可能被**重识别（reidentification）**。

**Randomized masking** can be an effective method of anonymizing data. Masking swaps data in individual data columns so that records no longer represent the actual data. However, the data still maintains aggregate values that can be used for other purposes, such as scientific purposes.

##### 技术方法示例

- **随机掩码（Randomized Masking）**：打乱数据但保留统计特性；
- **泛化（Generalization）**：如将“35岁”改为“30-40岁”；
- **扰动（Perturbation）**：加入噪声以隐藏真实值。

Unlike pseudonymization and tokenization, anonymization cannot be reversed. After the data is randomized using an anonymization process, it cannot be returned to the original state.

| 特性                   | **Pseudonymization** | **Tokenization**        | **Anonymization**    |
| ---------------------- | -------------------- | ----------------------- | -------------------- |
| 可逆性                 | ✅ 是                 | ✅ 是                    | ❌ 否                 |
| 关键工具/元素          | 假名 + 映射表        | Token + Vault           | 无（彻底删除或扰动） |
| 使用者是否能恢复原数据 | 数据持有者可以       | Token系统可以           | 无法恢复             |
| GDPR适用性             | 是（仍为个人数据）   | 是（仍为个人数据）      | 否（若无法再识别）   |
| 应用场景               | 数据共享、研究等     | 支付处理、认证系统等    | 研究、统计、AI建模等 |
| 安全性（泄露后后果）   | 需要映射表才可识别   | 需要Token Vault支持识别 | 无法识别，最安全     |

### Understanding Data Roles

Many people within an organization manage, handle, and use data, and they have different requirements based on their roles. Different documentation refers to these roles a little differently. Some of the terms you may see match the terminology used in some NIST documents, and other terms match some of the terminology used in the EU GDPR. When appropriate, we’ve listed the source so that you can dig into these terms a little deeper if desired.

One of the most important concepts here is ensuring that personnel know who owns information and assets. The owners have a primary responsibility of protecting the data and assets.

#### Data Owners

Data owners identify the classification of data and ensure that it is labeled properly. They also ensure that it has adequate security controls based on the classification and the organization’s security policy requirements. Owners may be liable for negligence if they fail to perform due diligence in establishing and enforcing security policies to protect and sustain sensitive data.

NIST SP 800-18 outlines the following responsibilities for the information owner, which can be interpreted the same as the data owner:

- Establishes the rules for appropriate use and protection of the subject data/information (rules of behavior)
- Provides input to information system owners regarding the security requirements and security controls for the information system(s) where the information resides
- Decides who has access to the information system and with what types of privileges or access rights
- Assists in the identification and assessment of the common security controls where the information resides

#### Asset Owners

The asset owner (or system owner) is the person who owns the asset or system that processes sensitive data. NIST SP 800-18 outlines the following responsibilities for the system owner:

Develops a system security plan in coordination with information owners, the system administrator, and functional end users

- Maintains the system security plan and ensures that the system is deployed and operated according to the agreed-upon security requirements
- Ensures that system users and support personnel receive appropriate security training, such as instruction on rules of behavior (or an AUP)
- Updates the system security plan whenever a significant change occurs
- Assists in the identification, implementation, and assessment of the common security controls

The system owner is responsible for ensuring that data processed on the system remains secure. This includes identifying the highest level of data that the system processes. The system owner then ensures that the system is labeled accurately and that appropriate security controls are in place to protect the data. System owners interact with data owners to ensure that the data is protected while at rest on the system, in transit between systems, and in use by applications operating on the system.

System and data owners are senior personnel within an organization. As a result, management teams typically include system and data owners. This is especially useful when a system has one owner for the system and another owner for the data.

#### Business/Mission Owners

The business/mission owner role is viewed differently in different organizations. NIST SP 800-18 refers to the business/mission owner as a program manager or an information system owner. As such, the responsibilities of the business/mission owner can overlap with the responsibilities of the system owner or be the same role.

Business owners might own processes that use systems managed by other entities. As an example, the sales department could be the business owner, but the IT department and the software development department could be the system owners for systems used in sales processes. Imagine that the sales department focuses on online sales using an ecommerce website, and the website accesses a back-end database server. As in the previous example, the IT department manages the web server as its system owner, and the software development department maintains the database server as its system owner. Even though the sales department doesn’t own these systems, it does own the business processes that generate sales using these systems.

In businesses, business owners are responsible for ensuring that systems provide value to the organization. This sounds obvious. However, compare this with IT departments. If there are any successful attacks or data breaches, the fault is likely to fall on them. IT departments often recommend security controls or systems that don’t add immediate value to the organization but reduce overall risks. The business owner is responsible for evaluating these recommendations and may decide that the potential loss related to the risks they eliminate is less than the loss of revenue they’ll cause.

Another way of looking at this is by comparing the conflict between cost centers and profit centers. The IT department doesn’t generate revenue. Instead, it is a cost center generating costs. In contrast, the business side generates revenue as a profit center. Costs generated by the IT department may reduce risks, but they eat up profits generated by the business side. The business side may view the IT department as spending money, reducing profits, and making it more difficult for the business to generate profits. Similarly, the IT department may think that the business side isn’t interested in reducing risks, at least until a costly security incident occurs.

Organizations often implement IT governance methods such as Control Objectives for Information and Related Technology (COBIT). These methods help business owners and mission owners balance security control requirements with business or mission needs. The overall goal is to provide a common language that all stakeholders can use to meet security and business needs.

#### Data Processors and Data Controllers

Generically, a data processor is any system used to process data. However, in the context of the GDPR, data processor has a more specific meaning. The GDPR defines a data processor as “a natural or legal person, public authority, agency, or other body, which processes personal data solely on behalf of the data controller.”

In this context, the data controller is the person or entity that controls the processing of the data. The data controller decides what data to process, why this data should be processed, and how it is processed.

As an example, a company that collects personal information on employees for payroll is a data controller. If they pass this information to a third-party company to process payroll, the payroll company is the data processor. In this example, the payroll company (the data processor) must not use the data for anything other than processing payroll at the direction of the data controller.

The GDPR restricts data transfers to countries outside the EU. Companies that violate privacy rules in the GDPR may face fines of up to 4 percent of their global revenue. Unfortunately, it is filled with legalese, presenting many challenges for organizations.

As a result, many organizations have created dedicated roles, such as a data privacy officer, to oversee the control of data and ensure the organization follows all relevant laws and regulations. The GDPR has mandated the role of a data protection officer for any organization that must comply with the GDPR. The person in this role is responsible for ensuring the organization applies the laws to protect individuals’ private data.

#### Data Custodians

Data owners often delegate day-to-day tasks to a data custodian. A custodian helps protect the integrity and security of data by ensuring that it is properly stored and protected. For example, custodians would ensure that the data is backed up by following guidelines in a backup policy. If administrators have configured auditing on the data, custodians would also maintain these logs.

In practice, personnel within an IT department or system security administrators would typically be the custodians. They might be the same administrators responsible for assigning permissions to data.

#### Administrators

You’ll often hear the term administrator(s). However, the term means different things in different contexts. If Sally logs onto the Administrator account in a Windows system, she is an administrator. Similarly, anyone added to an Administrators group in Windows is also an administrator.

However, many organizations view anyone with elevated privileges as administrators, even if they don’t have full administrative privileges. For example, help desk employees are granted some elevated privileges to perform their job but aren’t granted full administrative privileges. In this context, they are sometimes referred to as administrators. In the context of data roles, a data administrator may be a data custodian or someone in another data role.

#### Users and Subjects

A user is any person who accesses data via a computing system to accomplish work tasks. Users should have access only to the data they need to perform their work tasks. You can also think of users as employees or end users.

Users fall into a broader category of subjects, which are discussed further in Chapter 8, “Principles of Security Models, Design, and Capabilities,” and Chapter 13. A subject is any entity that accesses an object such as a file or folder. Subjects can be users, programs, processes, services, computers, or anything else that can access a resource.

The GDPR defines a data subject (not just a subject) as a person who can be identified through an identifier, such as a name, identification number, or other means. As an example, if a file includes PII on Sally Smith, Sally Smith is the data subject.

##### 核心数据角色一览（对比表）

| 角色                                          | 主要职责                                   | 来源标准/法规            | 可否直接控制数据？   |
| --------------------------------------------- | ------------------------------------------ | ------------------------ | -------------------- |
| **Data Owner**（数据所有者）                  | 决定数据分类、访问控制、合规要求           | NIST SP 800-18、GDPR隐含 | ✅ 是                 |
| **Asset Owner**（资产/系统所有者）            | 负责系统安全配置、系统生命周期管理         | NIST SP 800-18           | ✅ 是（系统层面）     |
| **Business/Mission Owner**（业务/使命所有者） | 保证系统或流程为业务增值，权衡安全与利润   | NIST SP 800-18、COBIT    | ✅ 是（流程层面）     |
| **Data Processor**（数据处理者）              | 按照Data Controller指示处理数据            | GDPR                     | ❌ 否                 |
| **Data Controller**（数据控制者）             | 决定为何、如何处理数据                     | GDPR                     | ✅ 是                 |
| **Data Custodian**（数据保管者）              | 实施Data Owner策略，如备份、审计、权限分配 | NIST隐含                 | ❌ 否（执行者）       |
| **Administrator**（管理员）                   | 具备系统权限，可能执行多种角色职责         | 通用术语                 | 部分可控（视权限）   |
| **User/Subject**（用户/主体）                 | 使用数据完成业务任务                       | 全域                     | ❌ 否                 |
| **Data Subject**（数据主体）                  | 被识别的个人                               | GDPR                     | ❌ 否（数据涉及对象） |

##### 各角色职责详解

✅ **Data Owner**

- 指定数据的**分类（敏感性级别）**；
- 决定谁可以访问、可访问何种级别；
- 确保数据有适当的安全措施；
- 对失职可能**承担法律/管理责任**。

> 例如：人力资源总监是员工数据的Data Owner。

------

✅ **Asset Owner / System Owner**

- 对系统本身负责（如Web服务器）；
- 配合Data Owner制定系统安全策略；
- **维护系统安全计划**；
- 管理人员安全培训与系统安全变更。

> 例如：IT部门的服务器管理员是Asset Owner。

------

✅ **Business/Mission Owner**

- 负责**业务价值最大化**；
- 权衡安全投入与利润回报；
- 可能影响或主导风险决策；
- 可通过COBIT等治理模型与IT合作。

> 例如：销售总监负责在线商城的业务流程，是商城系统的Business Owner。

------

✅ **Data Controller（GDPR术语）**

- 决定处理什么数据、如何处理；
- **对数据处理负最终法律责任**；
- 可委托Data Processor执行处理任务；
- 需要任命Data Protection Officer（DPO）。

> 例如：公司自己处理员工薪酬数据，它是Data Controller。

------

✅ **Data Processor（GDPR术语）**

- 按照Controller要求处理数据；
- 不得擅自改变用途或二次使用数据；
- 需签订Data Processing Agreement（DPA）。

> 例如：第三方薪资平台是Data Processor。

------

✅ **Data Custodian**

- IT团队中执行者角色；
- 实施备份、恢复、日志审计；
- 管理权限，但不决定策略；
- 对数据操作负**技术责任**。

------

✅ **Administrators**

- 广义指**拥有特权访问权**的技术人员；
- 可执行权限变更、系统配置、用户支持等；
- CISSP关注其应遵循**最小权限原则**和AUP（可接受使用政策）。

------

✅ **Users / Subjects / Data Subjects**

- **Users** 是合法员工使用数据完成任务；
- **Subjects** 是更广义访问者，可为进程、服务等；
- **Data Subjects** 是数据所**关联的自然人**（GDPR术语）。

总结

**Owner 决策，Custodian 执行**

**Controller 控流程，Processor 做操作**

**Business Owner 重价值，System Owner 重系统**

**User 用数据，Subject 是访问者，Data Subject 是对象人**

### Using Security Baselines

“**Baseline = 最低要求 + 持续应用 + 分级保护**”

Once an organization has identified and classified its assets, it will typically want to secure them. That’s where security baselines come in. Baselines provide a starting point and ensure a minimum security standard. One common baseline that organizations use is imaging.

**Security Baseline（安全基线）** 是一套**最小安全标准配置**，用于保护信息系统的机密性、完整性和可用性（CIA）。它作为一个**起点**，确保所有系统在部署和运行时都符合最基本的安全要求。

Baseline ≠ Best Practice，但它是一个“最低可接受的安全标准”。

Administrators configure a single system with desired settings, capture it as an image, and then deploy the image to other systems. This ensures that systems are deployed in a similar secure state, which helps to protect the privacy of data.

After deploying systems in a secure state, auditing processes periodically check the systems to ensure they remain in a secure state. As an example, Microsoft Group Policy can periodically check systems and reapply settings to match the baseline.

**NIST SP 800-53 Rev. 5,** 定义了各种 **安全控制（security controls）**，可用于创建安全基线。 “Security and Privacy Controls for Information Systems and Organizations,” mentions security control baselines and identifies them as a set of minimum security controls defined for an information system. It stresses that a single set of security controls does not apply to all situations. Still, any organization can select a set of baseline security controls and tailor the baseline to its needs.

**NIST SP 800-53B,** 专门列出了 **四种类型的基线**，用于根据系统的风险级别来选择合适的控制集合：“Control Baselines for Information Systems and Organizations,” includes a comprehensive list of security controls and has identified many of them to include in various baselines. Specifically, they present four baselines based on the potential impact to an organization’s mission if there is a loss of confidentiality, integrity, or availability of a system. The four baselines are as follows:

1. **Low-Impact Baseline** Controls in this baseline are recommended if a loss of confidentiality, integrity, or availability will have a low impact on the organization’s mission.
2. **Moderate-Impact Baseline** Controls in this baseline are recommended if a loss of confidentiality, integrity, or availability will have a moderate impact on the organization’s mission.
3. **High-Impact Baseline** Controls in this baseline are recommended if a loss of confidentiality, integrity, or availability will have a high impact on the organization’s mission.
4. **Privacy Control Baseline** This baseline provides an initial baseline for any systems that process PII. Organizations may combine this baseline with one of the other baselines.

| 基线名称                     | 适用场景                              | 举例                   |
| ---------------------------- | ------------------------------------- | ---------------------- |
| **Low-Impact Baseline**      | 损失对组织影响较低                    | 打印服务器             |
| **Moderate-Impact Baseline** | 损失有中等影响                        | HR系统                 |
| **High-Impact Baseline**     | 损失对组织影响严重                    | 医疗记录系统、金融系统 |
| **Privacy Control Baseline** | 处理**个人身份信息（PII）**的数据系统 | 员工档案数据库         |

NIST 提出“按需裁剪（tailoring）”的理念 —— 所有控制可基于具体环境进行调整。

**部署阶段** → 镜像部署 + 标准配置；

**运行阶段** → Group Policy、自动检查等持续保障；

**审计阶段** → 确保基线未被破坏，防止配置漂移；

**应急阶段** → 快速恢复到受控状态。

These refer to the worst-case potential impact if a system is compromised and a data breach occurs. As an example, imagine a system is compromised. You would try to predict the impact of the compromise on the confidentiality, integrity, or availability of the system and any data it holds:

■✓ If the compromise would cause privacy data to be compromised, you would consider adding the security controls identified as privacy control baseline items to your baseline.

■✓ If the impact is low, you would consider adding the security controls identified as low-impact controls to your baseline.

■✓ If the impact of this compromise is moderate, you would consider adding the security controls identified as moderate-impact, in addition to the low-impact controls.

■✓ If the impact is high, you would consider adding all the controls listed as high-impact in addition to the low-impact and moderate-impact controls.

##### 如何为系统选择合适的基线？

1. **评估潜在威胁影响（CIA）**：
   - 如果系统泄露、篡改或不可用，对业务影响是低/中/高？
2. **确定是否处理PII或敏感数据**：
   - 是 → 加上**Privacy Control Baseline**
3. **选择匹配影响等级的基线控制**：
   - 高影响 → 包括高、中、低影响控制
   - 中影响 → 包括中、低影响控制
   - 低影响 → 仅低影响控制

##### CISSP 的核心原则配合基线使用

- **最小权限原则（Least Privilege）**：强制用户和系统仅获得完成任务所需的最小权限；
- **默认拒绝原则（Default Deny）**：未明确允许的行为一律拒绝；
- **持续监控（Continuous Monitoring）**：对基线偏差的持续审计和修复。

It’s worth noting that many of the items in these lists are basic security practices. Additionally, implementing basic security principles such as the least privilege principle shouldn’t surprise anyone studying for the CISSP exam. Of course, just because these are basic security practices, it doesn’t mean organizations implement them. Unfortunately, many organizations have yet to discover or enforce the basics.

应用原则：

- **合规优先**：法律规定必须遵守；
- **行业最佳实践次之**：参考通用标准提升安全性；
- **组织策略优先级**：匹配业务目标，增强安全实践效果。

#### Comparing Tailoring and Scoping **安全控制基线的个性化过程**

After selecting a control baseline, organizations fine-tune it with tailoring and scoping processes. A big part of the tailoring process is aligning the controls with an organization’s specific security requirements. As a comparison, think of a clothes tailor who alters or repairs clothes. If a person buys a suit at a high-end retailer, a tailor modifies the suit to fit the person perfectly. Similarly, tailoring a baseline ensures it is a good fit for the organization.

##### **Tailoring** 

**定义**：在选定基线后，对控制进行微调，使其适配组织的业务需求、环境条件和合规目标。类比：就像你买了一件标准号西装，但还要请裁缝调整肩宽、袖长，让它“合身”。

It refers to modifying the list of security controls within a baseline to align with the organization’s mission. NIST SP 800-53B formally defines it as “part of an organization-wide risk management process that includes framing, assessing, responding to, and monitoring information security and privacy risks” and indicates it includes the following activities:

1. Identifying and designating **common controls** 识别共通控制： 如防火墙规则、身份验证机制适用于多个系统。
2. Applying **scoping considerations 应用范围考量**： 决定某个控制是否**适用于目标系统**。
3. Selecting **compensating controls 选择补偿控制**：如果某个推荐控制不可行，则用**等效或更优控制**替代。
4. **Assigning control values 分配控制值：**如：账户锁定次数由 5 改为 3，以增强安全性。

A selected baseline may not include commonly implemented controls. However, just because a security control isn’t included in the baseline doesn’t mean it should be removed. As an example, imagine that a data center includes video cameras covering the external entry, the internal exit, and every row of servers, but the baseline only recommends a video camera cover the external entry. During the tailoring process, personnel will evaluate these extra cameras and determine if they are needed. They may decide to remove some to save costs or keep them.

An organization might decide that a set of baseline controls applies perfectly to computers in their central location, but some controls aren’t appropriate or feasible in a remote office location. In this situation, the organization can select compensating security controls to tailor the baseline to the remote site. As another example, imagine the account lockout policy is set to lock out users if they enter an incorrect password five times. In this example, the control value is 5, but the tailoring process may change it to 3.

| 控制           | 标准设置       | Tailoring 修改后                    |
| -------------- | -------------- | ----------------------------------- |
| 视频监控控制   | 只覆盖外部入口 | 扩展为所有机房通道                  |
| 密码尝试次数   | 5 次锁定       | 调整为 3 次锁定                     |
| 多用户会话限制 | 默认启用       | 目标系统不支持并发登录 → 删除该控制 |

##### **Scoping** 

**定义**：在 Tailoring 的过程中，根据**系统特性**，评估每一个基线控制的适用性，并决定是否排除。

✍️ 组织需对**排除某控制的每一项决定做书面记录**（非常重要！CISSP 考点）

**Scoping 属于 Tailoring 的一部分**，但专注在“控制是否适用”的问题。

It is a part of the tailoring process and refers to reviewing a list of baseline security controls and selecting only those controls that apply to the IT systems you’re trying to protect. Or, in the simplest terms, scoping processes eliminate controls that are recommended in a baseline. For example, if a system doesn’t allow any two people to log on to it simultaneously, there’s no need to apply a concurrent session control. During this part of the tailoring process, the organization looks at every control in the baseline and vigorously defends (in writing) any decision to omit a control from the baseline.

| 概念                            | 要点                           | 注意事项                     |
| ------------------------------- | ------------------------------ | ---------------------------- |
| **Tailoring**                   | 调整安全控制，使其适配组织需求 | 控制值、控制替换、强化控制   |
| **Scoping**                     | 判断哪些控制适用于目标系统     | 可剔除控制，但需**文档说明** |
| **Compensating Controls**       | 替代不可行控制                 | 功能必须等效或更优           |
| **标准选择 Standard Selection** | 根据业务类型与法规确定控制要求 | PCI、HIPAA、GDPR等有强制性   |

#### Standards Selection（标准选择）

**标准选择**在建立和裁剪安全控制基线时，组织必须**对照外部法规、行业标准**，选出适用于自身业务和数据类型的安全标准，从而确保：

1. **法律合规（Legal Compliance）**
2. **行业认可（Industry Best Practice）**
3. **风险最小化（Risk Reduction）**

When selecting security controls within a baseline, or otherwise, organizations need to ensure that the controls comply with external security standards. External elements typically define compulsory requirements for an organization. As an example, the Payment Card Industry Data Security Standard (PCI DSS) defines requirements that businesses must follow to process major credit cards. Similarly, organizations that collect or process data belonging to EU citizens must abide by the requirements in the GDPR.

Obviously, not all organizations have to comply with these standards. Organizations that don’t process credit card transactions do not need to comply with PCI DSS. Similarly, organizations that do not collect or process EU citizens’ data do not need to comply with GDPR requirements. Organizations need to identify the standards that apply and ensure that the security controls they select fully comply with these standards.

Even if your organization isn’t legally required to comply with a specific standard, using a well-designed community standard can be helpful. As an example, U.S. government organizations are required to comply with many of the standards published by NIST SP 800 documents. These same documents are used by many organizations in the private sector to help them develop and implement their own security standards.

| 标准/法规            | 应用场景                 | 关键内容                         | 是否强制                       |
| -------------------- | ------------------------ | -------------------------------- | ------------------------------ |
| **PCI DSS**          | 处理信用卡支付           | 加密、访问控制、漏洞管理         | ✅ 强制                         |
| **GDPR**             | 收集/处理欧盟公民数据    | 透明性、数据主体权利、DPO职责    | ✅ 强制                         |
| **HIPAA**            | 医疗保健领域             | 保护PHI、技术/行政安全措施       | ✅ 强制                         |
| **SOX**              | 上市公司财务数据         | 数据完整性、可审计性             | ✅ 强制（对美上市公司）         |
| **NIST SP 800 系列** | 美国政府系统，或私企借鉴 | 控制基线、安全控制框架、风险管理 | ⚠️ 强制（对政府）；推荐（私营） |
| **ISO/IEC 27001**    | 通用信息安全管理体系     | ISMS架构、持续改进模型           | ⚠️ 可选，但广泛使用             |
| **COBIT**            | IT治理与控制             | IT与业务对齐，流程控制           | ⚠️ 推荐使用                     |

##### 标准选择的三步流程

① **法规识别（Identify Applicable Regulations）**

- 是否收集信用卡信息？→ **PCI DSS**
- 是否收集欧盟数据？→ **GDPR**
- 是否存储医疗记录？→ **HIPAA**

② **业务模型评估（Assess Business Operations）**

- 是否涉及政府合同？→ **FISMA / NIST**
- 是否需要获得信息安全认证？→ **ISO 27001**
- 是否存在IT与业务流程割裂？→ **COBIT治理模型**

③ **匹配安全控制（Map Controls to Standards）**

- 控制项必须满足法规要求；
- 控制裁剪不能低于标准规定的最低控制集；
- 所有控件变更必须文档化，并经合规团队或DPO评估。

小结助记

> **标准选择三要素：合规 + 适配 + 映射控制**

- **必须合规**的：法律强制如 GDPR / PCI / HIPAA；
- **建议遵循**的：如 ISO 27001 / COBIT / NIST；
- **选择标准后要映射控制** → 用 Tailoring/Scoping 方法调整控制集；
- **记录每项调整理由**，以备合规审查。

### Summary

Asset security focuses on **collecting**, **handling**, and **protecting** information throughout its **lifecycle**. This includes sensitive information stored or processed on computing systems or transferred over a network and the assets used in these processes. **Sensitive information** is any information that an organization keeps private and can include multiple levels of classifications. Proper destruction methods ensure that data can’t be retrieved after destruction.

**Data protection methods** include digital rights management **(DRM)** and using cloud access security brokers **(CASBs)** when using cloud resources. DRM methods attempt to protect copyrighted materials. A CASB is software placed logically between users and cloudbased resources. It can ensure that cloud resources have the same protections as resources within a network. Entities that must comply with the EU GDPR use additional data protection methods such as pseudonymization, tokenization, and anonymization.

Personnel can fulfill many different roles when handling data. **Data owners** are ultimately responsible for classifying, labeling, and protecting data. **System owners** are responsible for the systems that process the data. The GDPR defines **data controllers, data processors,** and **data custodians.** Data controllers decide what data to process and how to process it. A data controller can hire a third party to process data, and in this context, the third party is the data processor. Data processors have a responsibility to protect the privacy of the data and not use it for any purpose other than directed by the data controller. A custodian is delegated day-to-day responsibilities for properly storing and protecting data.

**Security baselines** provide a set of security controls that an organization can implement as a **secure starting point**. Some publications (such as NIST SP 800-53B) identify security control baselines. However, these baselines don’t apply equally to all organizations. Instead, organizations use **scoping and tailoring** techniques to identify the security controls to implement after selecting baselines. Additionally, organizations ensure that they implement security controls mandated by external standards that apply to their organization.

### Exam Essentials

- **Understand the importance of data and asset classifications.** Data owners are responsible for defining data and asset classifications and ensuring that data and systems are properly marked. Additionally, data owners define requirements to protect data at different classifications, such as encrypting sensitive data at rest and in transit. Data classifications are typically defined within security policies or data policies.
- **Define PII and PHI.** Personally identifiable information (PII) is any information that can identify an individual. Protected health information (PHI) is any health-related information that can be related to a specific person. Many laws and regulations mandate the protection of PII and PHI.
- **Know how to manage sensitive information.** Sensitive information is any type of classified information, and proper management helps prevent unauthorized disclosure resulting in a loss of confidentiality. Proper management includes marking, handling, storing, and destroying sensitive information. The two areas where organizations often miss the mark are adequately protecting backup media holding sensitive information and sanitizing media or equipment when it is at the end of its lifecycle.
- **Describe the three data states.** The three data states are at rest, in transit, and in use. Data at rest is any data stored on media such as hard drives or external media. Data in transit is any data transmitted over a network. Encryption methods protect data at rest and in transit. Data in use refers to data in memory and used by an application. Applications should flush memory buffers to remove data after it is no longer needed.
- **Define DLP.** Data loss prevention (DLP) systems detect and block data exfiltration attempts by scanning unencrypted files and looking for keywords and data patterns. Network-based systems (including cloud-based systems) scan files before they leave the network. Endpoint-based systems prevent users from copying or printing some files.
- **Compare data destruction methods.** Erasing a file doesn’t delete it. Clearing media overwrites it with characters or bits. Purging repeats the clearing process multiple times and removes data so that the media can be reused. Degaussing removes data from tapes and magnetic hard disk drives, but it does not affect optical media or SSDs. Destruction methods include incineration, crushing, shredding, and disintegration.
- **Describe data remanence.** Data remanence is the data that remains on media after it should have been removed. Hard disk drives sometimes retain residual magnetic flux that can be read with advanced tools. Advanced tools can read slack space on a disk, which is unused space in clusters. Erasing data on a disk leaves data remanence.
- **Understand record retention policies.** Record retention policies ensure that data is kept in a usable state while it is needed and destroyed when it is no longer needed. Many laws and regulations mandate keeping data for a specific amount of time, but in the absence of formal regulations, organizations specify the retention period within a policy. Audit trail data needs to be kept long enough to reconstruct past incidents, but the organization must identify how far back they want to investigate. A current trend in many organizations is to reduce legal liabilities by implementing short retention policies with email.
- **Know the difference between EOL and EOS.** End-of-life (EOL) is the date announced by a vendor when sales of a product stop. However, the vendor still supports the product after EOL. End-of-support (EOS) identifies the date when a vendor will no longer support a product.
- **Explain DRM.** Digital rights management (DRM) methods provide copyright protection for copyrighted works. The purpose is to prevent the unauthorized use, modification, and distribution of copyrighted works.
- **Explain CASB.** A cloud access security broker (CASB) is placed logically between users and cloud resources. It can apply internal security controls to cloud resources. The CASB component can be placed on-premises or in the cloud.
- **Define pseudonymization.** Pseudonymization is the process of replacing some data elements with pseudonyms or aliases. It removes privacy data so that a dataset can be shared. However, the original data remains available in a separate dataset.
- **Define tokenization.** Tokenization replaces data elements with a string of characters or a token. Credit card processors replace credit card data with a token, and a third party holds the mapping to the original data and the token.
- **Define anonymization.** Anonymization replaces privacy data with useful but inaccurate data. The dataset can be shared and used for analysis purposes, but anonymization removes individual identities. Anonymization is permanent.
- **Know the responsibilities of data roles.** The data owner is the person responsible for classifying, labeling, and protecting data. System owners are responsible for the systems that process the data. Business and mission owners own the processes and ensure that the systems provide value to the organization. Data controllers decide what data to process and how to process it. Data processors are often the third-party entities that process data for an organization at the direction of the data controller. Administrators grant access to data based on guidelines provided by the data owners. A user, or subject, accesses data while performing work tasks. A custodian has day-to-day responsibilities for protecting and storing data.
- **Know about security control baselines.** Security control baselines provide a listing of controls that an organization can apply as a baseline. Not all baselines apply to all organizations. Organizations apply scoping and tailoring techniques to adapt a baseline to their needs.
