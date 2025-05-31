# Cryptography and Symmetric Key Algorithms

- Domain 3.0: Security Architecture and Engineering

Cryptography is an extremely important security technology that is embedded in many of the controls used to protect information from unauthorized visibility and use. While cryptographers spent time developing strong encryption algorithms, malicious hackers and governments alike devoted significant resources to undermining them. This led to an “arms race” in cryptography and resulted in the development of the extremely sophisticated algorithms in use today.

## Cryptographic Foundations

Review of the goals of cryptography, an overview of the basic concepts of cryptographic technology, and a look at the major mathematical principles used by cryptographic systems.

### Goals of Cryptography

Security practitioners use cryptographic systems to meet four fundamental goals: confidentiality, integrity, authentication, and nonrepudiation. Achieving each of these goals requires the satisfaction of a number of design requirements, and not all cryptosystems are intended to achieve all four goals. 

#### Confidentiality

Confidentiality ensures that data remains private in three different situations: when it is at rest, when it is in transit, and when it is in use.

Two main types of cryptosystems enforce confidentiality:

- Symmetric cryptosystems use a shared secret key available to all users of the cryptosystem.
- Asymmetric cryptosystems use individual combinations of public and private keys for each user of the system.

When developing a cryptographic system for the purpose of providing confidentiality, you must think about the three different types of data

- Data at rest, or stored data, resides in a permanent location awaiting access. Examples of data at rest include data stored on hard drives, backup tapes, cloud storage services, USB devices, and other storage media.
- Data in motion, or data on the wire, is data being transmitted across a network between two systems. Data in motion might be traveling on a corporate network, a wireless network, or the internet.
- Data in use is data that is stored in the active memory of a computer system, where it may be accessed by a process running on that system.

Each of these situations poses different types of confidentiality risks that cryptography can protect against. For example, data in motion may be susceptible to eavesdropping attacks, whereas data at rest is more susceptible to the theft of physical devices. Data in use may be accessed by unauthorized processes if the operating system does not properly implement process isolation.

#### Integrity

Integrity ensures that data is not altered without authorization. If integrity mechanisms are in place, the recipient of a message can be certain that the message received is identical to the message that was sent. Similarly, integrity checks can ensure that stored data was not altered between the time it was created and the time it was accessed. Integrity controls protect against all forms of alteration, including intentional alteration by a third party attempting to insert false information, intentional deletion of portions of the data, and unintentional alteration by faults in the transmission process.

Message integrity is enforced through the use of encrypted message digests, known as digital signatures, created upon transmission of a message. The recipient of the message simply verifies that the message’s digital signature is valid, ensuring that the message was not altered in transit. Integrity can be enforced by both public and secret key cryptosystems.

#### Authentication

Authentication verifies the claimed identity of system users and is a major function of cryptosystems. 

#### Nonrepudiation

Nonrepudiation provides assurance to the recipient that the message was originated by the sender and not someone masquerading as the sender. It also prevents the sender from claiming that they never sent the message in the first place (also known as repudiating the message). Secret key, or symmetric key, cryptosystems (such as simple substitution ciphers) do not provide this guarantee of nonrepudiation. Nonrepudiation is offered only by public key, or asymmetric, cryptosystems.

### Cryptography Concepts

Before a message is put into a coded form, it is known as a **plaintext** message and is represented by the letter P when encryption functions are described. The sender of a message uses a cryptographic algorithm to encrypt the plaintext message and produce a **ciphertext** message, represented by the letter C. This message is transmitted by some physical or electronic means to the recipient. The recipient then uses a predetermined algorithm to decrypt the ciphertext message and retrieve the plaintext version.

All cryptographic algorithms rely on **keys** to maintain their security. For the most part, a key is nothing more than a number. It’s usually a **very large binary number**, but it’s a number nonetheless. 

Every algorithm has a specific key space. The key space is the range of values that are valid for use as a key for a specific algorithm. A **key space** is defined by its bit size. Bit size is nothing more than the number of binary bits (0s and 1s) in the key. The key space is the range between the key that has all 0s and the key that has all 1s. Or to state it another way, the key space is the range of numbers from 0 to 2^n , where n is the bit size of the key. So, a 128-bit key can have a value from 0 to 2^128

It is absolutely critical to protect the security of secret keys. In fact, all of the security you gain from cryptography rests on your ability to keep the keys used private.

- In private key (or secret key) cryptosystems, all participants use a single shared key.

- In public key cryptosystems, each participant has their own pair of keys. Cryptographic keys are sometimes referred to as cryptovariables, particularly in U.S. government applications.

##### Kerckhoffs’s Principle

**Kerckhoffs's Principle** 的核心思想是：**“一个加密系统应该即使在系统全部公开的情况下，仍然保持安全，只要密钥是保密的。”**

The system must be secure even if everything about it, except the key, is public knowledge.

只保密密钥，不保密算法。保证加密系统在算法公开的情况下仍然安全。反对Security through Obscurity（安全靠隐藏）

“敌人知道你的加密算法，但只要不知道密钥，就无法破解。”

AES、RSA、TLS 都是遵循该原则

The art of creating and implementing secret codes and ciphers is known as cryptography. This practice is paralleled by the art of crypt analysis—the study of methods to defeat codes and ciphers. Together, cryptography and cryptanalysis are commonly referred to as cryptology. Specific implementations of a code or cipher in hardware and software are known as cryptosystems.

**Federal Information Processing Standard (FIPS) 140–2,** “Security Requirements for Cryptographic Modules,” defines the hardware and software requirements for cryptographic modules that the federal government uses.

### Cryptographic Mathematics

#### Boolean Mathematics

AND, OR, NOT, Exclusive OR （XOR）

#### Modulo Function

8 mod 6 = 2

6 mod 8 = 6

10 mod 3 = 1

10 mod 2 = 0

32 mod 8 = 0

32 mod 26 = 6

#### One-Way Functions

A one-way function is a mathematical operation that easily produces output values for each possible combination of inputs but makes it impossible to retrieve the input values. Public key cryptosystems are all based on some sort of one-way function.

#### Nonce

**once** 是 “**number used once**” 的缩写，意思是：**一次性使用的数字**。

它在密码学中是一种临时随机数或计数值，用于**保证操作的唯一性**，防止重放攻击，并增加加密的随机性。

Cryptography often gains strength by adding randomness to the encryption process. One method by which this is accomplished is through the use of a nonce. A nonce is a random number that acts as a placeholder variable in mathematical functions. When the function is executed, the nonce is replaced with a random number generated at the moment of processing for one-time use. The nonce must be a unique number each time it is used. 

#### Zero-Knowledge Proof（零知识证明）

你能向对方证明“你知道一个秘密”，但又不泄露这个秘密本身。

One of the benefits of cryptography is found in the mechanism to prove your knowledge of a fact to a third party without revealing the fact itself to that third party. This is often done with passwords and other secret authenticators.

Zero-knowledge proofs appear in cryptography in cases where one individual wants to demonstrate knowledge of a fact (such as a password or key) without actually disclosing that fact to the other individual. This may be done through complex mathematical operations, such as discrete logarithms and graph theory.

##### Zero-Knowledge 的三大特性（CISSP 考点）

| 特性                           | 说明                                     |
| ------------------------------ | ---------------------------------------- |
| **完备性（Completeness）**     | 如果陈述是真的，验证者总能被说服         |
| **可靠性（Soundness）**        | 如果陈述是假的，骗子说服验证者的概率极低 |
| **零知识性（Zero-Knowledge）** | 验证过程不泄露任何有关“秘密”的信息       |

**Zero-Knowledge Proof = 证明你知道“什么”，但不告诉别人“是什么”**

- 应用于：身份验证、隐私保护、加密货币等；
- 不传递秘密，只传递**可以验证的“证明”**；
- 安全性高，不怕泄露、监听或重放攻击。

#### Split Knowledge

**Split Knowledge** 是一种控制方法：将执行敏感操作所需的信息或权限，**分配给多个人**，以确保**没有任何一个人可以单独完成任务或破坏安全性**。

No single individual has sufficient privileges to perform a sensitive action

它结合了：

- **职责分离（Separation of Duties）**
- **双人控制（Two-Person Control）**

When the information or privilege required to perform an operation is divided among multiple users, no single person has sufficient privileges to compromise the security of an environment. This separation of duties and two-person control contained in a single solution is called split knowledge.

The best example of split knowledge is seen in the concept of key escrow. In a key escrow arrangement, a cryptographic key is stored with a third party for safekeeping. When certain circumstances are met, the third party may use the escrowed key to either restore an authorized user’s access or decrypt the material themselves. This third party is known as the recovery agent.

In arrangements that use only a single key escrow recovery agent exists, there is opportunity for fraud and abuse of this privilege, as the single recovery agent could unilaterally decide to decrypt the information. **M of N Control** requires that a minimum number of agents ( M ) out of the total number of agents ( N ) work together to perform high-security tasks. So, implementing three of eight controls would require three people out of the eight with the assigned work task of key escrow recovery agent to work together to pull a single key out of the key escrow database (thereby also illustrating that M is always less than or equal to N).

#### Work Function

The effort required to perform a brute-force attack

**Work Function** 是指**破解一个加密系统所需的时间、计算资源和成本**，通常衡量为对该系统进行**暴力破解（brute-force attack）所需的最小代价**。它衡量的是：**“攻击者要多大努力才能破解这个加密？”**

You can measure the strength of a cryptography system by measuring the effort in terms of cost and/or time using a work function or work factor. Usually the time and effort required to perform a complete brute-force attack against an encryption system is what the work function represents. The security and protection offered by a cryptosystem is directly proportional to the value of the work function/factor. The size of the work function should be matched against the relative value of the protected asset. The work function need be only slightly greater than the time value of that asset. In other words, all security, including cryptography, should be cost-effective and cost-efficient. Spend no more effort to protect an asset than it warrants, but be sure to provide sufficient protection. Thus, if information loses its value over time, the work function needs to be only large enough to ensure protection until the value of the data is gone.

In addition to understanding the length of time that the data will have value, security professionals selecting cryptographic systems must understand how emerging technologies may impact cipher-cracking efforts. For example, researchers may discover a flaw in a cryptographic algorithm next year that renders information protected with that algorithm insecure. Similarly, technological advancements in cloud-based parallel computing and quantum computing may make brute-force efforts much more feasible down the road.

##### Work Function 的实际意义

| 项目           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 📊 衡量单位     | 时间（秒、年）、计算资源（CPU/GPU）、资金（美元）等          |
| 📈 越高越安全   | Work function 越大，攻击越不切实际                           |
| 💰 安全成本平衡 | 不应为无关紧要的数据投入极高的加密成本                       |
| ⏳ 数据价值关联 | 如果数据的保密期只有 1 周，那保护它不被破解超过 1 周就足够了 |
| 🚀 技术演进影响 | 云计算、量子计算等新技术会降低 work function，因此加密算法要及时更新 |

##### 经典原则：**加密强度 vs 数据价值** 

Work Function 应该略大于数据的有效期 + 数据的敏感性。

Enough to resist decryption attempts

| 数据类型         | 数据保密期     | 建议 Work Function       |
| ---------------- | -------------- | ------------------------ |
| 网上点餐记录     | 24 小时        | 足够抵抗普通脚本攻击     |
| 个人银行账户密码 | 若干年         | 抵抗暴力破解数年甚至更长 |
| 国家军事机密     | 数十年甚至永久 | 极高强度的加密和物理保护 |

### Ciphers

Cipher systems have long been used by individuals and governments interested in preserving the confidentiality of their communications. In the following sections, we’ll cover the definition of a cipher and explore several common cipher types that form the basis of modern ciphers. It’s important to remember that these concepts seem somewhat basic, but when used in combination, they can be formidable opponents and cause cryptanalysts many hours of frustration.

#### Codes vs. Ciphers

codes work on words and phrases, whereas ciphers work on individual characters, bits, and blocks.

Semaphores and Morse code are also examples of codes. These **codes are commonly known by the public and provide for ease of communication**. Some codes are secret. They may convey confidential information using a secret codebook where the meaning of the code is known only to the sender and recipient. For example, a spy might transmit the sentence “The eagle has landed” to report the arrival of an enemy aircraft.

**Ciphers**, on the other hand, are always meant to **hide the true meaning of a message.** They use a variety of techniques to alter and/or rearrange the characters or bits of a message to achieve confidentiality. Ciphers convert messages from plaintext to ciphertext on a bit basis (that is, a single digit of a binary code), character basis (that is, a single character of an ASCII message), or block basis (that is, a fixed-length segment of a message, usually expressed in number of bits). The following sections cover several common ciphers in use today.

#### Transposition Ciphers（置换密码）

Transposition ciphers use an encryption algorithm to rearrange the letters of a plaintext message, forming the ciphertext message. The decryption algorithm simply reverses the encryption transformation to retrieve the original message.

核心特性：

- 不改变字母本身，只是换位置；
- 解密过程就是**按照特定规则“逆置换”**；
- 保留了原文的字符统计特性。

#### Substitution Ciphers （Caesar cipher）

Substitution ciphers use the encryption algorithm to replace each character or bit of the plaintext message with a different character.

**替代密码**通过**替换明文字符**为其他字符（按规则）来生成密文。

核心特性：

- 每个字符变成另一个字符；
- 不改变顺序，但字符被“换掉”；
- 可使用简单映射表或复杂数学函数。

经典示例：**Caesar Cipher（凯撒密码）**

- 把每个字母替换为**向后移动固定数量**的字母；
- 例如：向右移动3位
  - A → D
  - B → E
  - …
  - Z → C

明文：`HELLO`
密文：`KHOOR`

##### One-Time Pads（Vernam ciphers）：OTP，一次性密码本

One-Time Pad 是一种使用“完全随机、一次性使用、与明文等长”的密钥来进行替代加密的系统。

A one-time pad is an extremely powerful type of substitution cipher. One-time pads use a different substitution alphabet for each letter of the plaintext message. They can be represented by the following encryption function, where K is the encryption key used to encrypt the plaintext letter P into the ciphertext letter C:

C = (P + K) mod 26

`P` 是明文字母的数值（A=0, B=1, ..., Z=25）

`K` 是密钥中相应位置的字母数值

`C` 是密文字母的数值

明文（P）： `HELLO`
密钥（K）： `XMCKL`
（将字母转换为数字：A=0, ..., Z=25）

| 字母 | H(7)  | E(4)  | L(11) | L(11) | O(14) |
| ---- | ----- | ----- | ----- | ----- | ----- |
| 密钥 | X(23) | M(12) | C(2)  | K(10) | L(11) |
| 运算 | 30→4  | 16    | 13    | 21    | 25    |
| 密文 | E     | Q     | N     | V     | Z     |

结果密文为：**EQNVZ**

Usually, one-time pads are written as a very long series of numbers to be plugged into the function.

The great advantage of one-time pads is that, when used properly, they are an unbreakable encryption scheme. There is no repeating pattern of alphabetic substitution, rendering cryptanalytic efforts useless. 

##### One-Time Pad 的使用要求（非常严格）

| 条件                                    | 原因                           |
| --------------------------------------- | ------------------------------ |
| ✅ 密钥必须**完全随机**                  | 否则可预测，暴露规律           |
| ✅ 密钥必须**等长**                      | 否则部分明文无法加密           |
| ✅ 密钥必须**只使用一次**                | 否则重复部分可被统计分析破解   |
| ✅ 密钥必须**严密保管**                  | 一旦密钥泄露 → 完全破译        |
| ✅ 加密 & 解密双方必须**提前共享密钥本** | 通信前必须安全交换大量密钥材料 |

⚠️ 因此 OTP 实用性差，但安全性极高，适用于**军事、政府绝密通信**

However, several requirements must be met to ensure the integrity of the algorithm:

- The one-time pad must be **randomly generated.** Using a phrase or a passage from a book would introduce the possibility that cryptanalysts could break the code.
- The one-time pad must be **physically protected against disclosure.** If the enemy has a copy of the pad, they can easily decrypt the enciphered messages.
- **Each one-time pad must be used only once.** If pads are reused, cryptanalysts can compare similarities in multiple messages encrypted with the same pad and possibly determine the key values used. In fact, a common practice when using paper pads is to destroy the page of keying material after it is used to prevent reuse.
- **The key must be at least as long as the message to be encrypted.** This is because each character of the key is used to encode only one character of the message.

| 特性           | 描述                                     |
| -------------- | ---------------------------------------- |
| ✅ 完全随机密钥 | 保证加密不可预测                         |
| ✅ 等长密钥     | 明文每个字符都有对应密钥位               |
| ✅ 仅用一次     | 不能复用，防止模式重现                   |
| ✅ 密钥保密     | 密钥泄露 = 系统失效                      |
| 🧠 优点         | 信息论上的**绝对安全**                   |
| ⚠️ 缺点         | 不实用，密钥管理困难，密钥分发需线下完成 |

#### Running Key Ciphers （连续密钥密码）**Book Cipher（书本密码）**

是一种替代密码，其密钥为一段**与明文等长的文本片段**（通常选自书籍、文章、杂志等公开材料）。

与 One-Time Pad 相似：

- 每个明文字母与对应位置的密钥字符进行加密；
- 但密钥不是随机生成，而是从已有文本中选取。

Many cryptographic vulnerabilities surround the limited length of the cryptographic key. one-time pads avoid these vulnerabilities by using a key that is at least as long as the message. However, one-time pads are awkward to implement because they require the physical exchange of pads.

C = (P + K) mod 26

One common solution to this dilemma is the use of a running key cipher (also known as a book cipher). In this cipher, the encryption key is as long as the message itself and is often chosen from a common book, newspaper, or magazine. For example, the sender and recipient might agree in advance to use the text of a chapter from Moby-Dick, beginning with the third paragraph, as the key. They would both simply use as many consecutive characters as necessary to perform the encryption and decryption operations.

| 记忆点             | 内容                                             |
| ------------------ | ------------------------------------------------ |
| 🔐 密钥来自哪？     | Book / Newspaper / Agreed text                   |
| 🔄 每字符用新密钥？ | 是，每字符配一个字母（等长）                     |
| 📉 不如 OTP 安全？  | 对，因为密钥非随机，可预测                       |
| 🧠 类似但不等于 OTP | OTP = 真正随机 & 完美加密；Running Key ≠ Perfect |

#### Block Ciphers（分组加密）

Block Cipher 是一种加密方式，将明文**分成固定长度的块（如 64 或 128 位）**，并**每块独立或链式加密**。

| 特性     | 描述                                     |
| -------- | ---------------------------------------- |
| 块长     | 常见有 64 位、128 位（如 AES）           |
| 处理方式 | 一次加密一个“块”                         |
| 密钥使用 | 同一个密钥用于多个块                     |
| 常见模式 | ECB, CBC, CFB, OFB, CTR                  |
| 安全优势 | 结合模式后可实现高强度加密和错误传播控制 |

Block ciphers operate on “chunks,” or blocks, of a message and apply the encryption algorithm to an entire message block at the same time. The transposition ciphers are examples of block ciphers. The simple algorithm used in the challenge-response algorithm takes an entire word and reverses its letters. The more complicated columnar transposition cipher works on an entire message (or a piece of a message) and encrypts it using the transposition algorithm and a secret keyword. Most modern encryption algorithms implement some type of block cipher.

举例：

- **AES（Advanced Encryption Standard）**：最常用的对称分组加密算法（块大小：128 位，密钥长度可为 128/192/256 位）；
- **DES、3DES**：早期的分组加密标准（现已过时）；
- **列置换（Columnar Transposition）**：古典密码的“块级”操作示例。

#### Stream Ciphers（流加密）

Stream Cipher 是一种**逐位或逐字节**处理明文的加密方式，通常使用密钥流生成器（keystream generator）产生与明文等长的伪随机序列。

Stream ciphers operate on one character or bit of a message (or data stream) at a time. The Caesar cipher is an example of a stream cipher. The **one-time pad** is also a stream cipher because the algorithm operates on each letter of the plaintext message independently. Stream ciphers can also function as a type of block cipher. In such operations there is a buffer that fills up to real-time data that is then encrypted as a block and transmitted to the recipient.

| 特性       | 描述                              |
| ---------- | --------------------------------- |
| 处理单位   | 单个位或字节                      |
| 加密方式   | 明文 bit/byte 与 keystream 做 XOR |
| 实时性强   | 可用于流媒体、语音加密            |
| 错误传播小 | 单个比特错误不影响整个消息        |

举例：

- **One-Time Pad（理论完美的流加密）**
- **RC4**：经典流加密（现不推荐使用）
- **TLS 中的某些加密套件（如 ChaCha20）**

##### Block vs Stream Ciphers

| 比较项   | Block Cipher                  | Stream Cipher                         |
| -------- | ----------------------------- | ------------------------------------- |
| 加密单位 | 数据块（如 128 位）           | 每位/每字节                           |
| 常见用途 | 文件、数据库、磁盘加密        | 网络通信、视频/音频流、VoIP等         |
| 模式要求 | 需选择 ECB/CBC/CTR 等加密模式 | 通常不需要，直接处理每一位            |
| 性能     | 更适合批量加密                | 更适合实时、低延迟场景                |
| 安全控制 | 易于结构化管理                | 需要避免密钥流重用（keystream reuse） |

#### Confusion（混淆） and Diffusion（扩散）

**Cryptographic** ：混淆指的是使密文与密钥之间的关系变得非常复杂，无法通过简单分析得出**密钥**。

Confusion occurs when the relationship between the **plaintext** and the **key** is so complicated that an attacker can’t merely continue altering the plaintext and analyzing the resulting ciphertext to determine the key. 

**Diffusion**：扩散是指明文中的每一个比特变化都会影响到多个密文比特。明文改一点，密文变一片

Diffusion occurs when a change in the **plaintext** results in multiple changes spread throughout the **ciphertext**. Consider, for example, a cryptographic algorithm that first performs a complex substitution and then uses transposition to rearrange the characters of the substituted ciphertext. In this example, the substitution introduces confusion, and the transposition introduces diffusion.

### Modern Cryptography

Modern cryptosystems use computationally complex algorithms and long cryptographic keys to meet the cryptographic goals of confidentiality, integrity, authentication, and nonrepudiation. The following sections cover the roles cryptographic keys play in the world of data security and examine three types of algorithms commonly used today: 

- symmetric encryption algorithms,
- asymmetric encryption algorithms,
- hashing algorithms.

#### Cryptographic Keys

Modern cryptosystems do not rely on the secrecy of their algorithms. In fact, the algorithms for most cryptographic systems are widely available for public review in the accompanying literature and on the internet. Opening algorithms to public scrutiny actually improves their security. Widespread analysis of algorithms by the computer security community allows practitioners to discover and correct potential security vulnerabilities and ensure that the algorithms they use to protect their communications are as secure as possible.

Instead of relying on secret algorithms, modern cryptosystems rely on the secrecy of one or more cryptographic keys used to personalize the algorithm for specific users or groups of users. Recall from the discussion of transposition ciphers that a keyword is used with the columnar transposition to guide the encryption and decryption efforts. The algorithm used to perform columnar transposition is well known. However, columnar transposition can be used to securely communicate between parties as long as a keyword is chosen that would not be guessed by an outsider. As long as the security of this keyword is maintained, it doesn’t matter that third parties know the details of the algorithm.

In the discussion of one-time pads earlier in this chapter, you learned that the main strength of the one-time pad algorithm is derived from the fact that it uses an extremely long key. In fact, **for that algorithm, the key is at least as long as the message itself.** Most modern cryptosystems do not use keys quite that long, but the length of the key is still an extremely important factor in determining the strength of the cryptosystem and the likelihood that the encryption will not be compromised through cryptanalytic techniques. **Longer keys provide higher levels of security by increasing the size of the key space, rendering brute-force attacks more difficult.**

it’s essential that you outpace adversaries by using sufficiently long keys that will defeat contemporary cryptanalysis efforts. Additionally, if you want to improve the chance that your data will remain safe from cryptanalysis some time into the future, you must strive to use keys that will outpace the projected increase in cryptanalytic capability during the entire time period the data must be kept safe. For example, the advent of quantum computing may transform cryptography, rendering current cryptosystems insecure.

Modern cryptographic systems use at least a 128-bit key to protect data against prying eyes. Remember, the length of the key directly relates to the work function of the cryptosystem: the longer the key, the harder it is to break the cryptosystem.

In addition to choosing keys that are long and will remain secure for the expected length of time that the information will remain confidential, you should also implement some other key management practices:

- Always store secret keys securely and, if you must transmit them over a network, do so in a manner that protects them from unauthorized disclosure.
- Select keys using an approach that has as much randomness as possible, taking advantage of the entire key space.
- Destroy keys securely when they are no longer needed.

#### Symmetric Key Algorithms

Symmetric key algorithms rely on a “shared secret” encryption key that is distributed to all members who participate in the communications. This key is used by all parties to both encrypt and decrypt messages, so the sender and the receiver both possess a copy of the shared key. The sender encrypts with the shared secret key and the receiver decrypts with it. When large-sized keys are used, symmetric encryption is very difficult to break. It is primarily employed to perform bulk encryption and provides only for the security service of confidentiality. Symmetric key cryptography can also be called secret key cryptography and private key cryptography.

![image-20250531021927775](/Users/leiwang/Library/Application Support/typora-user-images/image-20250531021927775.png)

In some cases, symmetric cryptography may be used with temporary keys that exist only for a single session. In those cases, the secret key is known as an **ephemeral key**. The most common example of this is the Transport Layer Security (TLS) protocol, which uses asymmetric cryptography to set up an encrypted channel and then switches to symmetric cryptography using an ephemeral key. 

##### Symmetric key cryptography has several weaknesses:

1. **Key distribution is a major problem.** Parties must have a secure method of exchanging the secret key before establishing communications with a symmetric key protocol. If a secure electronic channel is not available, an offline key distribution method must often be used (that is, out-of-band exchange).

2. **Symmetric key cryptography does not implement nonrepudiation.** Because any communicating party can encrypt and decrypt messages with the shared secret key, there is no way to prove where a given message originated.
3. **The algorithm is not scalable.** It is extremely difficult for large groups to communicate using symmetric key cryptography. Secure private communication between individuals in the group could be achieved only if each possible combination of users shared a private key.
4. **Keys must be regenerated often.** Each time a participant leaves the group, all keys known by that participant must be discarded. In automated encryption systems, keys may be regenerated based on the length of time that has passed, the amount of data exchanged, or the fact that a session goes idle or is terminated.

The major strength of symmetric key cryptography is the great speed at which it can operate. Symmetric key encryption is very fast, often 1,000 to 10,000 times faster than asymmetric algorithms. By nature of the mathematics involved, symmetric key cryptography also naturally lends itself to hardware implementations, creating the opportunity for even higher-speed operations and bulk encryption tasks.

#### Asymmetric Key Algorithms

Asymmetric key algorithms provide a solution to the weaknesses of symmetric key encryption. Public key algorithms are the most common example of asymmetric algorithms. In these systems, each user has two keys: a public key, which is shared with all users, and a private key, which is kept secret and known only to the user. But here’s a twist: opposite and related keys must be used in tandem to encrypt and decrypt. In other words, if the public key encrypts a message, then only the corresponding private key can decrypt it, and vice versa.

![image-20250531145125759](/Users/leiwang/Library/Application Support/typora-user-images/image-20250531145125759.png)

If Alice wants to send a message to Bob using public key cryptography, she creates the message and then encrypts it using Bob’s public key. The only possible way to decrypt this ciphertext is to use Bob’s private key, and the only user with access to that key is Bob. Therefore, Alice can’t even decrypt the message herself after she encrypts it. If Bob wants to send a reply to Alice, he simply encrypts the message using Alice’s public key, and then Alice reads the message by decrypting it with her private key.

Asymmetric key algorithms also provide support for digital signature technology. Basically, if Bob wants to assure other users that a message with his name on it was actually sent by him, he first creates a message digest by using a hashing algorithm (you’ll find more on hashing algorithms in the next section). Bob then encrypts that digest using his private key. Any user who wants to verify the signature simply decrypts the message digest using Bob’s public key and then verifies that the decrypted message digest is accurate.

The following is a list of the major strengths of asymmetric key cryptography:

- **The addition of new users requires the generation of only one public-private key pair.** This same key pair is used to communicate with all users of the asymmetric cryptosystem. This makes the algorithm extremely scalable.
- **Users can be removed far more easily from asymmetric systems.** Asymmetric cryptosystems provide a key revocation mechanism that allows a key to be canceled, effectively removing a user from the system.
- **Key regeneration is required only when a user’s private key is compromised.** If a user leaves the community, the system administrator simply needs to invalidate that user’s keys. No other keys are compromised and therefore key regeneration is not required for any other user.
- **Asymmetric key encryption can provide integrity, authentication, and nonrepudiation.** If a user does not share their private key with other individuals, a message signed by that user can be shown to be accurate and from a specific source and cannot be later repudiated. Asymmetric cryptography may be used to create digital signatures that provide nonrepudiation。
- **Key distribution is a simple process.** Users who want to participate in the system simply make their public key available to anyone with whom they want to communicate. There is no method by which the private key can be derived from the public key.
- **No preexisting communication link needs to exist.** Two individuals can begin communicating securely from the moment they start communicating. Asymmetric cryptography does not require a preexisting relationship to provide a secure mechanism for data exchange.

The major weakness of public key cryptography is its slow speed of operation. For this reason, many applications that require the secure transmission of large amounts of data **use public key cryptography to establish a connection** and **then exchange a symmetric secret key**. The **remainder of the session then uses symmetric cryptography.** This approach of combining symmetric and asymmetric cryptography is known as **hybrid cryptography**.

#### Hashing Algorithms

In the previous section, you learned that public key cryptosystems can provide digital signature capability when used in conjunction with a message digest. 

**Message digests** (also known as hash values or fingerprints) are summaries of a message’s content (not unlike a file checksum) produced by a hashing algorithm. It’s extremely difficult, if not impossible, to derive a message from an ideal hash function, and it’s very unlikely that two messages will produce the same hash value. Cases where a hash function produces the same value for two different methods are known as collisions, and the existence of collisions typically leads to the deprecation of a hashing algorithm.

### Symmetric Cryptography

#### Cryptographic Modes of Operation（**加密模式**）

加密模式定义了**如何将块加密算法应用于超过一个块的数据**，以及如何使其安全有效。它决定了**每一块的加密方式是否依赖前一块**，是否可以并行处理，是否支持完整性校验等特性。

The cryptographic modes of operation describe the different ways that cryptographic algorithms may transform data to achieve sufficient complexity that offers protection against attack. The major modes of operation are Electronic Code Book **(ECB**) mode, Cipher Block Chaining (**CBC**) mode, Cipher Feedback (**CFB**) mode, Output Feedback (**OFB**) mode, Counter (**CTR**) mode, Galois Counter Mode (**GCM**), and Counter with Cipher Block Chaining Message Authentication Code (**CCM**) mode.

##### 1. ECB：Electronic Code Book Mode

- **机制**：每个数据块**独立**加密；
- **特点**：
  - 相同明文块 → 相同密文块；
  - **没有随机性、容易被模式分析**；
- ✅ **用途**：非常小的数据（如密钥、参数）；数据库的单元格。

**不推荐用于一般数据加密**！

Electronic Code Book (ECB) mode is the simplest mode to understand and the least secure. Each time the algorithm processes a 64-bit block, it simply encrypts the block using the chosen secret key. This means that if the algorithm encounters the same block multiple times, it will produce the same encrypted block. If an enemy were eavesdropping on the communications, they could simply build a “code book” of all the possible encrypted values. After a sufficient number of blocks were gathered, cryptanalytic techniques could be used to decipher some of the blocks and break the encryption scheme.

This vulnerability makes it impractical to use ECB mode on any but the shortest transmissions. In everyday use, ECB is used only for exchanging small amounts of data, such as keys and parameters used to initiate other cryptographic modes as well as the cells in a database.

##### 2. CBC：Cipher Block Chaining Mode

**机制**：每个明文块先与前一个密文块 **XOR**，再加密；

第一个块用 **IV（Initialization Vector）**；

**特点**：

- 增加随机性；
- 出现传输错误 → 影响本块 + 下一块（错误传播）；

✅ 用于：文件、磁盘加密、TLS（部分版本）

In Cipher Block Chaining (CBC) mode, each block of unencrypted text is XORed with the block of ciphertext immediately preceding it before it is encrypted. The decryption process simply decrypts the ciphertext and reverses the XOR operation. CBC implements an IV and XORs it with the first block of the message, producing a unique output every time the operation is performed. The IV must be sent to the recipient, perhaps by tacking the IV onto the front of the completed ciphertext in plain form or by protecting it with ECB mode encryption using the same key used for the message. One important consideration when using CBC mode is that errors propagate—if one block is corrupted during transmission, it becomes impossible to decrypt that block and the next block as well.

##### 3. CFB：Cipher Feedback Mode

**机制**：基于 CBC 的**流加密版本**；

每次只处理部分数据（如每个字节），适合**实时数据加密**；

使用 IV + 加密前一段密文，生成伪随机流；

✅ 用于：音频流、实时通讯加密；

Cipher Feedback (CFB) mode is the streaming cipher version of CBC. In other words, CFB operates against data produced in real time. However, instead of breaking a message into blocks, it uses memory buffers of the same block size. As the buffer becomes full, it is encrypted and then sent to the recipients. Then the system waits for the next buffer to be filled as the new data is generated before it is in turn encrypted and then transmitted. Other than the change from preexisting data to real-time data, CFB operates in the same fashion as CBC. It uses an IV, and it uses chaining.

##### 4. OFB：Output Feedback Mode

**机制**：和 CFB 类似，但生成密钥流不依赖密文，而是**不断加密前一轮输出值**；

优点：**错误不会传播**；

适合高容错要求的场景（如卫星通信）；

✅ 用于：无线通讯、串口设备

In Output Feedback (OFB) mode, ciphers operate in almost the same fashion as they do in CFB mode. However, instead of XORing an encrypted version of the previous block of ciphertext, OFB XORs the plaintext with a seed value. For the first encrypted block, an initialization vector is used to create the seed value. Future seed values are derived by running the algorithm on the previous seed value. The major advantages of OFB mode are that there is no chaining function and transmission errors do not propagate to affect the decryption of future blocks.

##### 5. CTR：Counter Mode

**机制**：使用一个**递增的计数器**作为输入，每个块独立生成密钥流；

特点：

- 支持**并行加解密**（性能高）；
- 不会出现错误传播；

✅ 用于：云存储、大规模加密、快速数据流

Counter (CTR) mode uses a stream cipher similar to that used in CFB and OFB modes. However, instead of creating the seed value for each encryption/decryption operation from the results of the previous seed values, it uses a simple counter that increments for each operation. As with OFB mode, errors do not propagate in CTR mode.

CTR mode allows you to break an encryption or decryption operation into multiple independent steps. This makes CTR mode well suited for use in parallel computing.

##### 6. GCM：Galois/Counter Mode

- = CTR + **认证（Integrity）**
- 特点：
  - 提供**机密性 + 完整性**；
  - 使用 **认证标签（Auth Tag）** 来验证数据是否被篡改；
  - 高速加密 + 认证 → **广泛用于 TLS、IPSec、SSH**

✅ 现代标准加密模式，推荐！

Galois/Counter Mode (GCM) takes the standard CTR mode of encryption and adds data authenticity controls to the mix, providing the recipient assurances of the integrity of the data received. This is done by adding authentication tags to the encryption process.

##### 7. CCM：Counter with Cipher Block Chaining Message Authentication Code Mode

**CCM = CTR + CBC-MAC**

- **机制**：使用 CTR 提供加密，使用 CBC-MAC 提供认证；
- 要求：
  - 只适用于**128-bit 块加密算法（如 AES）**；
  - **必须使用唯一的 nonce（随机数）**；
- ✅ 用于：物联网加密、无线协议（如 ZigBee）

Similar to GCM, the Counter with Cipher Block Chaining Message Authentication Code Mode (CCM) combines a confidentiality mode with a data authenticity process. In this case, CCM ciphers combine the Counter (CTR) mode for confidentiality with the Cipher Block Chaining Message Authentication Code (CBC-MAC) algorithm for data authenticity.

CCM is used only with block ciphers that have a 128-bit block length and require the use of a nonce that must be changed for each transmission.

GCM and CCM modes both include data authenticity in addition to confidentiality. They are, therefore, known as authenticated modes of encryption. ECB, CBC, CFB, OFB, and CTR mode only provide confidentiality and are, therefore, known as unauthenticated modes.

##### 模式分类：是否具备认证能力

| 模式    | 是否提供完整性认证？ | 是否推荐使用？         |
| ------- | -------------------- | ---------------------- |
| **ECB** | ❌ 无                 | 🚫 极不安全，避免使用   |
| **CBC** | ❌ 无                 | ✅ 可用（需结合 MAC）   |
| **CFB** | ❌ 无                 | ✅ 流加密场景可用       |
| **OFB** | ❌ 无                 | ✅ 用于高容错场景       |
| **CTR** | ❌ 无                 | ✅ 并行性能好，需加 MAC |
| **GCM** | ✅ 有                 | ✅ 推荐，现代首选       |
| **CCM** | ✅ 有                 | ✅ 轻量加密认证方案     |

##### 总结

| 模式 | 一句话记忆                     |
| ---- | ------------------------------ |
| ECB  | 每块独立 → 重复明文 = 重复密文 |
| CBC  | 链式 XOR，带随机性，但错误传播 |
| CFB  | CBC 的流加密版本，适合实时     |
| OFB  | 流式加密，错误不传播           |
| CTR  | 用计数器并行处理，性能高       |
| GCM  | CTR + 校验码，**现代首选**     |
| CCM  | CTR + MAC，轻量级完整性加密    |

#### DES：Data Encryption Standard

| 项目       | 内容说明                                            |
| ---------- | --------------------------------------------------- |
| ⏱️ 发布时间 | 1977，美国政府标准                                  |
| 🔢 块大小   | 64 位                                               |
| 🔐 密钥长度 | 64 位中有效密钥为 **56 位**（其余 8 位是奇偶校验）  |
| 🔁 加密轮数 | 16 轮 Feistel 结构                                  |
| ⚠️ 安全性   | **已不安全**，易被暴力破解（如 EFF 的 DES Cracker） |
| 📦 使用场景 | 已淘汰，仅在 3DES 中作为基础                        |

The U.S. government published the Data Encryption Standard in 1977，Advanced Encryption Standard in December 2001; It is still important to understand DES because it is the building block of Triple DES (3DES), a stronger (but still not strong enough) encryption algorithm.

DES is a 64-bit block cipher that has five modes of operation: Electronic Code Book (ECB) mode, Cipher Block Chaining (CBC) mode, Cipher Feedback (CFB) mode, Output Feedback (OFB) mode, and Counter (CTR) mode. All of the DES modes operate on 64 bits of plaintext at a time to generate 64-bit blocks of ciphertext. The key used by DES is 56 bits long.

DES uses a long series of exclusive OR (XOR) operations to generate the ciphertext. This process is repeated 16 times for each encryption/decryption operation. Each repetition is commonly referred to as a round of encryption, explaining the statement that DES performs 16 rounds of encryption. Each round generates a new key that is then used as the input to subsequent rounds.

The DES specification calls for a 64-bit key. However, of those 64 bits, only 56 actually contain keying information. The remaining 8 bits are supposed to contain parity information to ensure that the other 56 bits are accurate. In practice, however, those parity bits are rarely used. You should commit the 56-bit figure to memory.

#### Triple DES

为延长 DES 使用寿命而设计：**多次运行 DES 算法**

| 变体         | 加密过程                                      | 密钥数量 | 有效安全性 |
| ------------ | --------------------------------------------- | -------- | ---------- |
| **DES-EDE3** | E(K1, D(K2, E(K3, P)))                        | 3 个     | ~112 位    |
| **DES-EEE3** | E(K1, E(K2, E(K3, P)))                        | 3 个     | ~112 位    |
| **DES-EDE2** | 使用 K1, K2（K3=K1）                          | 2 个     | 不安全     |
| ⚠️ 安全性     | 所有变体现已被 NIST **弃用（2023 年后禁用）** |          |            |

📌 **总结**：**3DES 不推荐使用**，但部分旧系统仍兼容。

Data Encryption Standard’s (DES) 56-bit key is no longer considered adequate in the face of modern cryptanalytic techniques and supercomputing power. However, an adapted version of DES, Triple DES (3DES), uses the same algorithm to produce encryption that is stronger but that is no longer considered adequate to meet modern requirements. For this reason, 3DES encryption should be avoided, although it is still supported by many products.

There are several different variants of 3DES that each use different numbers of independent keys. The first two, DES-EDE3 and DES EEE-3, use three independent keys: K1 , K2 , and K3 . The difference between the two are the operations used, which are represented by the letter E for encryption and D for decryption. DES-EDE3 encrypts the data with K1, decrypts the resulting ciphertext with K2, and then encrypts that text with K3. 

**DES-EDE3** can be expressed using the following notation, where E(K,P) represents the encryption of plaintext P with key K, and D(K,P) represents the decryption of ciphertext C with key K:

- E(K1,D(K2,E(K3,P)))

**DES-EEE3** encrypts the data with all three keys in sequential order, and may be represented as follows:

- E(K1,E(K2,E(K3,P)))

Mathematically, DES-EEE3 and DES-EDE3 should have an effective key length of 168 bits. However, known attacks against this algorithm reduce the effective strength to 112 bits.

DES-EEE3 is the only variant of 3DES that is currently considered secure by NIST. The other variants, DES-EDE1, DES-EEE2, and DES-EDE2, use either one or two keys, repeating the same key multiple times, but these modes are no longer considered secure. It is also important to note that NIST recently deprecated the use of all 3DES variants and will disallow their use in federal government applications at the end of 2023.

#### IDEA：International Data Encryption Algorithm (Used in PGP)

| 项目       | 内容说明                           |
| ---------- | ---------------------------------- |
| 🇨🇭 开发者  | 瑞士，回应 DES 的密钥强度不足问题  |
| 🔢 块大小   | 64 位                              |
| 🔐 密钥长度 | **128 位**                         |
| 🔧 加密结构 | 非 Feistel；用异或 + 模运算        |
| 📑 模式     | 支持 ECB、CBC、CFB、OFB、CTR       |
| 🔓 使用许可 | 2012 年专利过期，现免费使用        |
| 📦 实例应用 | PGP（Pretty Good Privacy）早期版本 |

The International Data Encryption Algorithm (IDEA) block cipher was developed in response to complaints about the insufficient key length of the DES algorithm. Like DES, IDEA operates on 64-bit blocks of plaintext/ciphertext. However, it begins its operation with a 128-bit key. This key is broken up in a series of operations into 52 16-bit subkeys. The subkeys then act on the input text using a combination of XOR and modulus operations to produce the encrypted/decrypted version of the input message. IDEA is capable of operating in the same five modes used by DES: ECB, CBC, CFB, OFB, and CTR.

The IDEA algorithm was patented by its Swiss developers. However, the patent expired in 2012, and it is now available for unrestricted use. One popular implementation of IDEA is found in Phil Zimmerman’s popular Pretty Good Privacy (PGP) secure email package.

#### Blowfish (often used in SSH) , Bruce Schneier

| 项目       | 内容说明                             |
| ---------- | ------------------------------------ |
| ⏱️ 发布时间 | 1993 年                              |
| 🔢 块大小   | 64 位                                |
| 🔐 密钥长度 | **32~448 位（可变）**                |
| 🏎️ 性能     | 高效、速度快（比 IDEA、DES 快）      |
| 📑 模式     | 支持所有标准块加密模式               |
| 🆓 许可     | 无版权限制，开放使用                 |
| 📦 应用     | 多个商业系统、开源库、操作系统中集成 |

Bruce Schneier’s Blowfish block cipher is another alternative to DES and IDEA. Like its predecessors, Blowfish operates on 64-bit blocks of text. However, it extends IDEA’s key strength even further by allowing the use of variable-length keys ranging from a relatively insecure 32 bits to an extremely strong 448 bits. Obviously, the longer keys will result in a corresponding increase in encryption/decryption time. However, time trials have established Blowfish as a much faster algorithm than both IDEA and DES. Also, Schneier released Blowfish for public use with no license required. Blowfish encryption is built into a number of commercial software products and operating systems. A number of Blowfish libraries are also available for software developers.

#### Skipjack（美国政府专属加密）

| 项目       | 内容说明                               |
| ---------- | -------------------------------------- |
| 🛠️ 支持芯片 | Clipper / Capstone                     |
| 🔢 块大小   | 64 位                                  |
| 🔐 密钥长度 | 80 位                                  |
| 🛡️ 特殊机制 | **密钥托管/政府回收（escrow）机制**    |
| 🏛️ 管理单位 | NIST + 美国财政部                      |
| ⚠️ 问题     | 社区不信任政府介入加密，被拒绝广泛使用 |

The Skipjack algorithm was approved for use by the U.S. government in Federal Information Processing Standard (FIPS) 185, the Escrowed Encryption Standard (EES). Like many block ciphers, Skipjack operates on 64-bit blocks of text. It uses an 80-bit key and supports the same four modes of operation supported by DES. Skipjack was quickly embraced by the U.S. government and provides the cryptographic routines supporting the Clipper and Capstone encryption chips.

However, Skipjack has an added twist—it supports the escrow of encryption keys. Two government agencies, the National Institute of Standards and Technology (NIST) and the Department of the Treasury, hold a portion of the information required to reconstruct a Skipjack key. When law enforcement authorities obtain legal authorization, they contact the two agencies, obtain the pieces of the key, and are able to decrypt communications between the affected parties.

Skipjack and the Clipper chip were not embraced by the cryptographic community at large because of its mistrust of the escrow procedures in place within the U.S. government.

#### Rivest Ciphers（RC 系列算法）

Ron Rivest, of Rivest-Shamir-Adleman (RSA) Data Security, created a series of symmetric ciphers over the years known as the Rivest Ciphers (RC) family of algorithms. Several of these, RC4, RC5, and RC6, have particular importance today.

##### Rivest Cipher 4 (RC4)

| 项目     | 内容说明                  |
| -------- | ------------------------- |
| 类型     | **流加密**                |
| 密钥长度 | 40 ~ 2048 位              |
| 应用     | 曾用于 WEP、WPA、SSL、TLS |
| 安全性   | 已被完全攻破，不推荐使用  |

RC4 is a stream cipher developed by Rivest in 1987 and very widely used during the decades that followed. It uses a single round of encryption and allows the use of variable-length keys ranging from 40 bits to 2,048 bits. RC4’s adoption was widespread because it was integrated into the Wired Equivalent Privacy (WEP), Wi-Fi Protected Access (WPA), Secure Sockets Layer (SSL), and Transport Layer Security (TLS) protocols.

A series of attacks against this algorithm render it insecure for use today. WEP, WPA, and SSL no longer meet modern security standards for both this and other reasons. TLS no longer allows the use of RC4 as a stream cipher.

##### Rivest Cipher 5 (RC5)

| 项目     | 内容说明                         |
| -------- | -------------------------------- |
| 特性     | 结构灵活（块大小/轮数/密钥可变） |
| 块大小   | 可设为 32/64/128 位              |
| 密钥长度 | 0 ~ 2040 位                      |
| 安全性   | 64 位密钥已被破解（耗时4年）     |

RC5 is a block cipher of variable block sizes (32, 64, or 128 bits) that uses key sizes between 0 (zero) length and 2,040 bits. It is important to note that RC5 is not simply the next version of RC4. In fact, it is completely unrelated to the RC4 cipher. Instead, RC5 is an improvement on an older algorithm called RC2 that is no longer considered secure.

RC5 is the subject of brute-force cracking attempts. A large-scale effort leveraging massive community computing resources cracked a message encrypted using RC5 with a 64-bit key, but this effort took more than four years to crack a single message.

##### Rivest Cipher 6 (RC6)

| 项目     | 内容说明           |
| -------- | ------------------ |
| 特性     | RC5 的改进         |
| 块大小   | 128 位             |
| 密钥长度 | 128/192/256 位     |
| 安全性   | 强，但未被选为 AES |
| 当前用途 | 很少见，未广泛采用 |

RC6 is a block cipher that was developed as the next version of RC5. It uses a 128-bit block size and allows the use of 128-, 192-, or 256-bit symmetric keys. This algorithm was one of the candidates for selection as the Advanced Encryption Standard (AES) discussed in the next section, but it was not selected and is not widely used today.

##### 总结

| 算法     | 类型     | 块大小 | 密钥强度      | 安全性     | 应用状态             |
| -------- | -------- | ------ | ------------- | ---------- | -------------------- |
| DES      | 对称分组 | 64位   | 56 位         | ❌ 不安全   | 已淘汰               |
| 3DES     | 对称分组 | 64位   | 112~168 位    | ⚠️ 被弃用   | 向后兼容             |
| IDEA     | 对称分组 | 64位   | 128 位        | ✅ 安全     | PGP 等               |
| Blowfish | 对称分组 | 64位   | 可变至 448 位 | ✅ 安全     | 快速，广泛使用       |
| Skipjack | 对称分组 | 64位   | 80 位         | ❌ 不受欢迎 | 政府特用，带回收机制 |
| RC4      | 流加密   | N/A    | 40–2048 位    | ❌ 不安全   | 已废弃               |
| RC5      | 分组加密 | 可变   | 可变          | ⚠️ 部分破解 | 教学/试验性用途      |
| RC6      | 分组加密 | 128位  | 128~256 位    | ✅ 安全     | 少用                 |

#### Advanced Encryption Standard

The U.S. government published Advanced Encryption Standard in December 2001; NIST released FIPS 197, which mandated the use of AES/Rijndael for the encryption of all sensitive but unclassified data by the U.S. government.

The Advanced Encryption Standard (AES) cipher allows the use of three key strengths: 128 bits, 192 bits, and 256 bits. AES only allows the processing of 128-bit blocks, but Rijndael exceeded this specification, allowing cryptographers to use a block size equal to the key length. The number of encryption rounds depends on the key length chosen:

- 128-bit keys require 10 rounds of encryption.
- 192-bit keys require 12 rounds of encryption.
- 256-bit keys require 14 rounds of encryption.

#### CAST

The CAST algorithms are another family of symmetric key block ciphers that are integrated into some security solutions. The CAST algorithms use a Feistel network and come in two forms:

- CAST-128 uses either 12 or 16 rounds of Feistel network encryption with a key size between 40 and 128 bits on 64-bit blocks of plaintext.
- CAST-256 uses 48 rounds of encryption with a key size of 128, 160, 192, 224, or 256 bits on 128-bit blocks of plaintext.

The CAST-256 algorithm was a candidate for the Advanced Encryption Standard but was not selected for that purpose.

##### Twofish

The Twofish algorithm developed by Bruce Schneier (also the creator of Blowfish) was another one of the AES finalists. Like Rijndael, Twofish is a block cipher. It operates on 128-bit blocks of data and is capable of using cryptographic keys up to 256 bits in length.

Twofish uses two techniques not found in other algorithms:

- Prewhitening involves XORing the plaintext with a separate subkey before the first round of encryption.
- Postwhitening uses a similar operation after the 16th round of encryption.

#### Comparison of Symmetric Encryption Algorithms

There are many symmetric encryption algorithms you need to be familiar with. Table 6.9 lists several common and well-known symmetric encryption algorithms along with their block size and key size.

| 算法名称     | Block Size（块大小） | Key Size（密钥长度）    | 类型/备注                      |
| ------------ | -------------------- | ----------------------- | ------------------------------ |
| **AES**      | 128                  | 128, 192, 256           | 标准分组加密，最常用           |
| **Rijndael** | Variable             | 128, 192, 256           | AES 原始算法，可变块           |
| **Blowfish** | 64                   | 32–448                  | 快速，自由授权，用于 SSH 等    |
| **DES**      | 64                   | 56                      | 已淘汰，构建了 3DES 基础       |
| **3DES**     | 64                   | 112 或 168              | 已被 NIST 弃用                 |
| **IDEA**     | 64                   | 128                     | 曾用于 PGP，已过专利保护       |
| **RC4**      | N/A（流加密）        | 40–2048                 | 流加密，已不安全               |
| **RC5**      | 32, 64, 128          | 0–2040                  | 块加密，结构灵活               |
| **RC6**      | 128                  | 128, 192, 256           | RC5 的扩展，AES 竞争者之一     |
| **Skipjack** | 64                   | 80                      | 政府用途，支持密钥托管         |
| **CAST-128** | 64                   | 40–128                  | 被多种协议使用（如 PGP）       |
| **CAST-256** | 128                  | 128, 160, 192, 224, 256 | CAST 系列增强版                |
| **Twofish**  | 128                  | 1–256                   | AES 竞标算法，支持任意密钥长度 |

##### 特殊注意点

- **AES 与 Rijndael 区别**：
  - AES 是 Rijndael 的一个固定配置版本；
  - AES 只支持 128-bit 块，而 Rijndael 可支持 128、192、256 位块。
- **RC4 是流加密算法**，**无块大小**，使用的是 Keystream（密钥流）。
- **3DES 的有效密钥长度为 112 位**，即使使用了 3 个 56 位密钥，也会被 Meet-in-the-Middle 攻击降低有效性。
- **Twofish 支持任意长度密钥（1–256 位）**，极具灵活性，是 Blowfish 的后继者。

##### 考试记忆技巧

**📊 分类记忆法（Block Size）**

- 64 位块：DES, 3DES, IDEA, Blowfish, CAST-128, Skipjack
- 128 位块：AES, Rijndael, RC6, CAST-256, Twofish
- 可变块：RC5（32/64/128）

**🔐 记住代表性密钥长度**

- **AES 类算法** → **128/192/256** 位（包括 AES、RC6、CAST-256、Rijndael）
- **DES/3DES** → 56（有效）或 112/168（3DES）
- **RC 系列** → 非常灵活，RC4（最大到 2048），RC5（0–2040）
- **Blowfish** → 上限最高：448 位

#### Symmetric Key Management（对称加密的密钥管理）

Because cryptographic keys contain information essential to the security of the cryptosystem, it is incumbent upon cryptosystem users and administrators to take extraordinary measures to protect the security of the keying material. These security measures are collectively known as key management practices. They include safeguards surrounding the creation, distribution, storage, destruction, recovery, and escrow of secret keys.

##### 1.Creation and Distribution of Symmetric Keys（对称密钥的创建与分发）

三种主要密钥分发方式

| 方法                      | 描述                                       | 适用场景                   | 风险点                                        |
| ------------------------- | ------------------------------------------ | -------------------------- | --------------------------------------------- |
| **Offline Distribution**  | 物理手段（如U盘、纸条、硬件Token）传输密钥 | 高安全要求、无网络前提     | 易丢失、窃听、麻烦                            |
| **Public Key Encryption** | 用接收者公钥加密对称密钥，再发送过去       | 混合加密架构（如 TLS）     | 依赖PKI或密钥验证机制                         |
| **Diffie–Hellman (DH)**   | 协议动态协商密钥，无需提前共享             | 无法预先建立信任的对等通信 | 不验证身份 → 可能被中间人攻击（需加认证机制） |

**关键词记忆**：

- DH：无 PKI 时解决密钥协商问题；
- 公钥加密：为对称密钥传输**加上一层包装**。

The three main methods used to exchange secret keys securely are offline distribution, public key encryption, and the Diffie–Hellman key exchange algorithm.

1. **Offline Distribution** The most technically simple (but physically inconvenient) method involves the physical exchange of key material. One party provides the other party with a sheet of paper or piece of storage media containing the secret key. In many hardware encryption devices, this key material comes in the form of an electronic device that resembles an actual key that is inserted into the encryption device. However, every offline key distribution method has its own inherent flaws. If keying material is sent through the mail, it might be intercepted. Telephones can be wiretapped. Papers containing keys might be inadvertently thrown in the trash or lost. The use of offline distribution is cumbersome for end users, particularly when they are located in geographically distant locations.
2. **Public Key Encryption** Many communicators want to obtain the speed benefits of secret key encryption without the hassles of key distribution. For this reason, many people use public key encryption to set up an initial communications link. Once the link is successfully established and the parties are satisfied as to each other’s identity, they exchange a secret key over the secure public key link. They then switch communications from the public key algorithm to the secret key algorithm and enjoy the increased processing speed. In general, secret key encryption is thousands of times faster than public key encryption.
3. **Diffie–Hellman** In some cases, neither public key encryption nor offline distribution is sufficient. Two parties might need to communicate with each other, but they have no physical means to exchange key material, and there is no public key infrastructure in place to facilitate the exchange of secret keys. In situations like this, key exchange algorithms like the Diffie–Hellman algorithm prove to be extremely useful mechanisms.

##### 2. Storage and Destruction of Symmetric Keys（密钥的存储与销毁）

存储原则

| 原则                             | 说明                                          |
| -------------------------------- | --------------------------------------------- |
| ❌ 不应和加密数据存放在同一个位置 | 否则攻击者拿到数据也能解密                    |
| ✅ 关键密钥可拆分交由多人持有     | **Split Knowledge** 机制                      |
| 🔁 密钥轮换                       | 人员离职或权限变更时，必须更换密钥 & 重新加密 |

Another major challenge with the use of symmetric key cryptography is that all of the keys used in the cryptosystem must be kept secure. This includes following best practices surrounding the storage of encryption keys:

- Never store an encryption key on the same system where encrypted data resides. This just makes it easier for the attacker!
- For sensitive keys, consider providing two different individuals with half of the key. They then must collaborate to re-create the entire key. This is known as the principle of split knowledge.

When a user with knowledge of a secret key leaves the organization or is no longer permitted access to material protected with that key, the keys must be changed, and all encrypted materials must be reencrypted with the new keys.

存储方式

| 类型           | 描述                                | 特点             |
| -------------- | ----------------------------------- | ---------------- |
| **软件型存储** | 本地文件系统、应用加密存储等        | 成本低，风险高   |
| **硬件型存储** | 如 HSM（硬件安全模块）、智能卡、TPM | 成本高，安全性高 |

When choosing a key storage mechanism, you have two major options available to you:

1. **Software-based storage mechanisms** store keys as digital objects on the system where they are used. For example, this might involve storing the key on the local filesystem. More advanced software-based mechanisms may use specialized applications to protect those keys, including the use of secondary encryption to prevent unauthorized access to the keys. Software-based approaches are generally simple to implement but introduce the risk of the software mechanism being compromised.
2. **Hardware-based storage mechanisms** are dedicated hardware devices used to manage cryptographic keys. These may be personal devices, such as flash drives or smartcards that store a key used by an individual, or they may be enterprise devices, called hardware security modules (HSMs), that manage keys for an organization. Hardware approaches are more complex and expensive to implement than software approaches, but they offer added security.

##### 3.Key Escrow（密钥托管） and Recovery（密钥恢复）

如果密钥丢失或用户无法访问，**关键数据将永久无法访问**。为防止这种情况，组织可能采用密钥托管与恢复机制。

Cryptography is a powerful tool. Like most tools, it can be used for a number of beneficent purposes, but it can also be used with malicious intent. To gain a handle on the explosive growth of cryptographic technologies, governments around the world have floated ideas to implement key escrow systems. These systems allow the government, under limited circumstances such as a court order, to obtain the cryptographic key used for a particular communication from a central storage facility.

**Key Escrow（密钥托管）**

| 机制                                    | 描述                                          | 风险                           |
| --------------------------------------- | --------------------------------------------- | ------------------------------ |
| **Fair Cryptosystems**                  | 把密钥分成几份分别给第三方 → 法律授权后可重组 | 比较可信，但复杂               |
| **Escrowed Encryption Standard（EES）** | 政府可以解密，如 Clipper 芯片                 | **严重隐私争议，不被公众接受** |

Two major approaches to key escrow have been proposed over the past decade:

1. **Fair Cryptosystems** In this escrow approach, the secret keys used in a communication are divided into two or more pieces, each of which is given to an independent third party. Each of these pieces is useless on its own but they may be recombined to obtain the secret key. When the government obtains legal authority to access a particular key, it provides evidence of the court order to each of the third parties and then reassembles the secret key.
2. **Escrowed Encryption Standard** This escrow approach provides the government or another authorized agent with a technological means to decrypt ciphertext. It was the approach proposed for the Clipper chip.

**公众普遍不接受**政府托管密钥的主张（Clipper、Skipjack 被广泛反对）

It’s highly unlikely that government regulators will ever overcome the legal and privacy hurdles necessary to implement key escrow on a widespread basis. The technology is certainly available, but the general public will likely never accept the potential government intrusiveness it facilitates.

**Key Recovery（密钥恢复）机制**

- 用于组织内部管理；
- 例如员工离职后恢复其加密数据；
- 由 **Recovery Agent（RA）** 操作；
- 具有高度权限，风险极大！

There are, however, legitimate uses for key escrow within an organization. Key escrow and recovery mechanisms prove useful when an individual leaves the organization and other employees require access to their encrypted data, or when a key is simply lost. In these approaches, key recovery agents (RAs) have the ability to recover the encryption keys assigned to individual users. This is, of course, an extremely powerful privilege, as an RA could gain access to any user’s encryption key. For this reason, many organizations choose to adopt a mechanism known as M of N control for key recovery. In this approach, there is a group of individuals of size N in an organization who are granted RA privileges. If they wish to recover an encryption key, a subset of at least M of them must agree to do so. For example, in an M-of-N control system where M=12 and N=3, there are 12 authorized recovery agents, of whom 3 must collaborate to retrieve an encryption key.

**M-of-N 控制机制**：为限制 RA 权力，组织可要求**M人中必须至少有N人同意**才允许恢复密钥。

总结

| 模块                   | 关键词                  |
| ---------------------- | ----------------------- |
| 分发方法               | Offline, Public Key, DH |
| 存储方式               | 软件易用，硬件更安全    |
| 销毁策略               | 离职或权限变动时需更换  |
| Split Knowledge        | 多人各掌握部分密钥      |
| Key Escrow（密钥托管） | 法律授权恢复机制        |
| M-of-N 控制            | 多人授权才能恢复密钥    |

### Cryptographic Lifecycle

With the exception of the one-time pad, all cryptographic systems have a limited life span. Moore’s law, a commonly cited trend in the advancement of computing power, states that the processing capabilities of a state-of-the-art microprocessor will double approximately every two years. This means that, eventually, processors will reach the amount of strength required to simply guess the encryption keys used for a communication.

Security professionals must keep this cryptographic lifecycle in mind when selecting an encryption algorithm and have appropriate governance controls in place to ensure that the algorithms, protocols, and key lengths selected are sufficient to preserve the integrity of a cryptosystem for however long it is necessary to keep the information it is protecting secret. Security professionals can use the following algorithm and protocol governance controls:

- Specifying the cryptographic algorithms (such as AES, 3DES, and RSA) acceptable for use in an organization
- Identifying the acceptable key lengths for use with each algorithm based on the sensitivity of information transmitted
- Enumerating the secure transaction protocols (such as TLS) that may be used

For example, if you’re designing a cryptographic system to protect the security of business plans that you expect to execute next week, you don’t need to worry about the theoretical risk that a processor capable of decrypting them might be developed a decade from now. On the other hand, if you’re protecting the confidentiality of information that could be used to construct a nuclear bomb, it’s virtually certain that you’ll still want that information to remain secret 10 years in the future!

### Summary

Cryptographers and cryptanalysts are in a never-ending race to develop more secure cryptosystems and advanced cryptanalytic techniques designed to circumvent those systems.

Cryptography dates back as early as Caesar and has been an ongoing topic of study for many years. In this chapter, you learned some of the fundamental concepts underlying the field of cryptography and gained a basic understanding of the terminology used by cryptographers.

This chapter also examined the similarities and differences between symmetric key cryptography (where communicating parties use the same key) and asymmetric key cryptography (where each communicator has a pair of public and private keys). You learned how hashing may be used to guarantee integrity and how hashes play a role in the digital signature process that guarantees nonrepudiation.

We then analyzed some of the symmetric algorithms currently available and their strengths and weaknesses. We wrapped up the chapter by taking a look at the cryptographic lifecycle and the role of algorithm/protocol governance in enterprise security.

The next chapter expands this discussion to cover contemporary public key cryptographic algorithms. Additionally, some of the common cryptanalytic techniques used to defeat both types of cryptosystems will be explored.

### Exam Essentials

- **Understand the role that confidentiality, integrity, and nonrepudiation play in cryptosystems.** Confidentiality is one of the major goals of cryptography. It protects the secrecy of data while it is both at rest and in transit. Integrity provides the recipient of a message with the assurance that data was not altered (intentionally or unintentionally) between the time it was created and the time it was accessed. Nonrepudiation provides undeniable proof that the sender of a message actually authored it. It prevents the sender from subsequently denying that they sent the original message.
- **Know how cryptosystems can be used to achieve authentication goals.** Authentication provides assurances as to the identity of a user. One possible scheme that uses authentication is the challenge-response protocol, in which the remote user is asked to encrypt a message using a key known only to the communicating parties. Authentication can be achieved with both symmetric and asymmetric cryptosystems.
- **Be familiar with the basic terminology of cryptography.** When a sender wants to transmit a private message to a recipient, the sender takes the plaintext (unencrypted) message and encrypts it using an algorithm and a key. This produces a ciphertext message that is transmitted to the recipient. The recipient then uses a similar algorithm and key to decrypt the ciphertext and re-create the original plaintext message for viewing.
- **Understand the difference between a code and a cipher and explain the basic types of ciphers.** Codes are cryptographic systems of symbols that operate on words or phrases and are sometimes secret but don’t always provide confidentiality. Ciphers, however, are always meant to hide the true meaning of a message. Know how the following types of ciphers work: transposition ciphers, substitution ciphers (including one-time pads), stream ciphers, and block ciphers.
- **Know the requirements for successful use of a one-time pad.** For a one-time pad to be successful, the key must be generated randomly without any known pattern. The key must be at least as long as the message to be encrypted. The pads must be protected against physical disclosure, and each pad must be used only one time and then discarded.
- **Understand split knowledge.** Split knowledge means that the information or privilege required to perform an operation is divided among multiple users. This ensures that no single person has sufficient privileges to compromise the security of the environment. M of N Control is an example of split knowledge used in key recovery and other sensitive tasks.
- **Understand work function (work factor).** Work function, or work factor, is a way to measure the strength of a cryptography system by measuring the effort in terms of cost and/or time to decrypt messages. Usually the time and effort required to perform a complete bruteforce attack against an encryption system is what a work function rating represents. The security and protection offered by a cryptosystem is directly proportional to the value of its work function/factor.
- **Understand the importance of key security.** Cryptographic keys provide the necessary element of secrecy to a cryptosystem. Modern cryptosystems utilize keys that are at least 128 bits long to provide adequate security.
- **Know the differences between symmetric and asymmetric cryptosystems.** Symmetric key cryptosystems (or secret key cryptosystems) rely on the use of a shared secret key. They are much faster than asymmetric algorithms, but they lack support for scalability, easy key distribution, and nonrepudiation. Asymmetric cryptosystems use public-private key pairs for communication between parties but operate much more slowly than symmetric algorithms.
- **Be able to explain the basic operational modes of symmetric cryptosystems.** Symmetric cryptosystems operate in several discrete modes: Electronic Code Book (ECB) mode, Cipher Block Chaining (CBC) mode, Cipher Feedback (CFB) mode, Output Feedback (OFB) mode, Counter (CTR) mode, Galois/Counter mode (GCM), and Counter with Cipher Block Chaining Message Authentication Code mode (CCM). ECB mode is considered the least secure and is used only for short messages. 3DES uses three iterations of DES with two or three different keys to increase the effective key strength to 112 or 168 bits, respectively.
- **Know the Advanced Encryption Standard (AES).** The Advanced Encryption Standard (AES) uses the Rijndael algorithm and is the U.S. government standard for the secure exchange of sensitive but unclassified data. AES uses key lengths of 128, 192, and 256 bits and a fixed block size of 128 bits to achieve a much higher level of security than that provided by the older DES algorithm.
