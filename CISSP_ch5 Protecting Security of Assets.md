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

#### Digital Rights Management

Digital rights management (DRM) methods attempt to provide copyright protection for copyrighted works. The purpose is to prevent the unauthorized use, modification, and distribution of copyrighted works such as intellectual property. Here are some methods associated with DRM solutions:


