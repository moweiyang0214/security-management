#  PKI and Cryptographic Applications

- Domain 3:0 Security Architecture and Engineering

This chapter explores the world of asymmetric (or public key) cryptography and the public key infrastructure (PKI) that supports secure communication between individuals who don’t necessarily know each other prior to the communication. Asymmetric algorithms provide convenient key exchange mechanisms and are scalable to very large numbers of users, addressing the two most significant challenges for users of symmetric cryptosystems.

This chapter also explores several practical applications of asymmetric cryptography: securing portable devices, email, web communications, and networking. The chapter concludes with an examination of a variety of attacks malicious individuals might use to compromise weak cryptosystems.

## Asymmetric Cryptography

Three of the more common asymmetric cryptosystems in use today: **Rivest–Shamir–Adleman (RSA), Diffie–Hellman, ElGamal, and elliptic curve cryptography (ECC)**. We’ll also explore the emerging world of quantum cryptography.

### Public and Private Keys

public key cryptosystems assign each user a pair of keys: a public key and a private key. As the names imply, public key cryptosystem users make their public keys freely available to anyone with whom they want to communicate. The mere possession of the public key by third parties does not introduce any weaknesses into the cryptosystem. The private key, on the other hand, is reserved for the sole use of the individual who owns the keys. Users should not normally share their private keys with any other cryptosystem user, outside of key escrow and recovery arrangements.

Once the sender encrypts the message with the recipient’s public key, no user (including the sender) can decrypt that message without knowing the recipient’s private key (the second half of the public-private key pair used to generate the message). This is the beauty of public key cryptography—public keys can be freely shared using unsecured communications and then used to create secure communications channels between users previously unknown to each other.

Keys used within public key systems must be longer than those used in private key systems to produce cryptosystems of equivalent strengths.

### 1. RSA

The RSA algorithm depends on the computational difficulty inherent in factoring the product of large prime numbers. Each user of the cryptosystem generates a pair of public and private keys using the algorithm described in the following steps:

1. Choose two large prime numbers (approximately 200 digits each), labeled p and q.

2. Compute the product of those two numbers: n = p * q.

3. Select a number, e, that satisfies the following two requirements:
   1. e is less than n.
   2. e and (p – 1)(q – 1) are relatively prime—that is, the two numbers have no common factors other than 1.


3. Find a number, d, such that ed = 1 mod ((p – 1)(q – 1)).

4. Distribute e and n as the public key to all cryptosystem users. Keep d secret as the private key.

If Alice wants to send an encrypted message to Bob, she generates the ciphertext (C) from the plaintext (P) using the following formula (where e is Bob’s public key and n is the product of p and q created during the key generation process):

C = P<sup>e</sup> mod n

When Bob receives the message, he performs the following calculation to retrieve the plaintext message:

P = C<sup>d</sup> mod n

#### Importance of Key Length

The length of the cryptographic key is perhaps the most important security parameter that can be set at the discretion of the security administrator. It’s important to understand the capabilities of your encryption algorithm and choose a key length that provides an appropriate level of protection. This judgment can be made by weighing the difficulty of defeating a given key length (measured in the amount of processing time required to defeat the cryptosystem) against the importance of the data.

Generally speaking, the more critical your data, the stronger the key you should use to protect that data. Timeliness of the data is also an important consideration. You must take into account the rapid growth of computing power.

Also, as attackers are now able to leverage cloud computing resources, they are able to more efficiently attack encrypted data. The cloud allows attackers to rent scalable computing power, including powerful graphic processing units (GPUs) on a per-hour basis, and offers significant discounts when using excess capacity during nonpeak hours. This brings powerful computing well within the reach of many attackers.

The key lengths shown in the following table for three cryptosystems all provide equal protection because of differences in the way that the algorithms use the keying material:

| Cryptosystem   | Key length |
| -------------- | ---------- |
| Symmetric      | 128 bits   |
| RSA            | 3,072 bits |
| Elliptic curve | 256 bits   |

### 2. ElGamal

We learned how the Diffie–Hellman algorithm uses large integers and modular arithmetic to facilitate the secure exchange of secret keys over insecure communications channels. In **1985**, Dr. Taher Elgamal published an article describing how the mathematical principles behind the Diffie–Hellman key exchange algorithm could be extended to support an entire public key cryptosystem used for encrypting and decrypting messages.

However, ElGamal also has a major disadvantage—the algorithm doubles the size of any message that it encrypts. This presents a major hardship when encrypting large amounts of data that must be sent over a network.

### 3. ECC：Elliptic Curve

The same year that Elgamal published his algorithm, two other mathematicians, Neal Koblitz from the University of Washington and Victor Miller from IBM, independently proposed the application of **elliptic curve cryptography (ECC).**

Any elliptic curve can be defined by the following equation:

y<sup>2</sup> = x<sup>3</sup> + ax + b

**A 3,072-bit RSA key is cryptographically equivalent to a 256bit elliptic curve cryptosystem key.**

### 4. Diffie–Hellman Key Exchange

they use the DiffieHellman algorithm, following this process:

1. Richard and Sue agree on two large numbers: p (which is a prime number) and g (which is an integer), such that 1 < g < p.

2. Richard chooses a large random integer r and performs the following calculation:

   R = g^r mod p


3. Sue chooses a large random integer s and performs the following calculation:

   S = g^s mod p

4. Richard sends R to Sue and Sue sends S to Richard.

5. Richard then performs this calculation:

   K = S^r mod p

6. Sue then performs this calculation:

   K = R^s mod p

It is important to note that Diffie–Hellman is not an encryption protocol in and of itself. It is technically a **key exchange protocol.** However, it is commonly used to create a shared secret key for use in Transport Layer Security (TLS), where it is referred to as either DHE or EDH. 

The Diffie–Hellman key exchange algorithm relies on the use of large prime numbers. The ECDHE key exchange algorithm is a variant of this approach that uses the elliptic curve problem to perform a similar key agreement process.

### Quantum Cryptography

The most significant impact of quantum computing on the world of cryptography resides in the potential that quantum computers may be able to solve problems that are not possible to solve on contemporary computers. This concept is known as quantum supremacy and, if achieved, may be able to easily solve the factorization problems upon which many classical asymmetric encryption algorithms rely. If this occurs, it could render popular algorithms such as RSA and Diffie–Hellman insecure.

However, quantum computers may also be used to create newer, more complex cryptographic algorithms. These quantum cryptography systems may be more resistant to quantum attacks and could usher in a new era of cryptography. Researchers have already developed lab implementations of quantum key distribution (QKD), an approach to use quantum computing to create a shared secret key between two users, similar to the goal of the DiffieHellman algorithm. Like quantum cryptography in general, QKD has not yet reached the stage of practical use.

## Hash Functions

| 项目     | 内容                                                         |
| -------- | ------------------------------------------------------------ |
| 功       | 将任意长度的消息输入压缩成固定长度的摘要值（Message Digest）。 |
| 主要用途 | ✅ 完整性校验（消息未被修改）<br>✅ **数字签名机制**（散列值被签名加密） |
| 本质特点 | ✔ 一致性：同一输入总得到同一输出<br>✔ 不可逆性：无法从输出反推出输入<br/>✔ 高敏感性：哪怕一位输入改动，输出也完全不同 |
| 经典对比 | 哈希 ≠ 加密：哈希是单向的、不可逆；加密是可逆的。<br>哈希提供完整性，**不**提供机密性或不可否认性。<br>典型使用场景：消息校验码、签名验证、密码验证（哈希+加盐）等。 |

Hash functions have a very simple purpose—they take a potentially long message and generate a unique output value derived from the content of the message. This value is commonly referred to as the **message digest**. Message digests can be generated by the sender of a message and transmitted to the recipient along with the full message for two reasons.

First, the recipient can use the same hash function to recompute the message digest from the full message. They can then compare the computed message digest to the transmitted one to ensure that the message sent by the originator is the same one received by the recipient. If the message digests do not match, that means the message was somehow modified while in transit. It is important to note that the messages must be exactly identical for the digests to match. If the messages have even a slight difference in spacing, punctuation, or content, the message digest values will be completely different. It is not possible to tell the degree of difference between two messages by comparing the digests. Even a slight difference will generate totally different digest values.

Second, the message digest can be used to implement a digital signature algorithm.

哈希长度与安全性关系

- **摘要越长，抗碰撞性越强**；
- 但摘要过长 → 处理性能下降；
- 通常选择平衡方案，如 SHA-256、SHA-384。

In most cases, a message digest is 128 bits or larger. However, a single-digit value can be used to perform the function of parity, a low-level or single-digit checksum value used to provide a single individual point of verification. In most cases, the longer the message digest, the more reliable its verification of integrity.

#### RSA's Five Basic Requirements（RSA 对加密哈希函数的五大要求）

| 要求                               | 解释                             |
| ---------------------------------- | -------------------------------- |
| 1️⃣ 输入可以是任意长度               | 无论消息多长，算法都能处理       |
| 2️⃣ 输出是固定长度                   | SHA-1：160 位；SHA-256：256 位等 |
| 3️⃣ 易于计算                         | 哈希计算速度快，适合大规模验证   |
| 4️⃣ 单向性（One-way）                | 不能从输出反推输入               |
| 5️⃣ 抗碰撞性（Collision Resistance） | 极难找到两个不同输入产生相同输出 |

According to RSA Security, there are five basic requirements for a cryptographic hash function:

- The input can be of any length.
- The output has a fixed length.
- The hash function is relatively easy to compute for any input.
- The hash function is one-way (meaning that it is extremely hard to determine the input when provided with the output).
- The hash function is collision resistant (meaning that it is extremely hard to find two messages that produce the same hash value).

The bottom line is that **hash functions create a value that uniquely represents the data in the original message but cannot be reversed**, or “de-hashed.” Access to the hashed value does not allow someone to determine what the original message actually contained. **Access to both the original message and the original hashed value allows someone to verify that the message hasn’t changed** since the first hash was created by generating a new hash and comparing the two. If the hashes match, the hash function was run on the same input data, so the input data has not changed.

应试要点：

- 📌 “不可逆”是哈希和加密的本质区别。
- 📌 抗碰撞 ≠ 无碰撞，但在设计上要“极难发生”。
- ⚠️ CISSP 会用伪造摘要、Birthday Attack 来考碰撞特性。

Common hashing algorithms: Secure Hash Algorithm **(SHA)**, Message Digest 5 **(MD5),** and the RIPE Message Digest **(RIPEMD)**.

### 1. SHA: Secure Hash Algorithm

| 算法    | 摘要长度 | 输入块大小 | 状态               |
| ------- | -------- | ---------- | ------------------ |
| SHA-1   | 160 bits | 512 bits   | ❌ 已弃用（不安全） |
| SHA-256 | 256 bits | 512 bits   | ✅                  |
| SHA-224 | 224 bits | 512 bits   | ✅（SHA-256 截断）  |
| SHA-512 | 512 bits | 1024 bits  | ✅                  |
| SHA-384 | 384 bits | 1024 bits  | ✅（SHA-512 截断）  |
| SHA-3   | 可变长   | -          | ✅ 更抗量子攻击     |

The Secure Hash Algorithm (SHA) and its successors, SHA-1, SHA-2, and SHA-3, are government standard hash functions promoted by the National Institute of Standards and Technology (NIST) and are specified in an official government publication—the Secure Hash Standard (SHS), also known as Federal Information Processing Standard (FIPS) 180.

SHA-1 takes an input of virtually any length (in reality, there is an upper bound of approximately 2,097,152 terabytes on the algorithm) and produces a 160-bit message digest. The SHA-1 algorithm processes a message in 512-bit blocks. Therefore, if the message length is not a multiple of 512, the SHA algorithm pads the message with additional data until the length reaches the next highest multiple of 512.

Cryptanalytic attacks demonstrated that there are weaknesses in the SHA-1 algorithm, and therefore, NIST deprecated SHA-1 and no longer recommends its use for any purpose, including digital signatures and digital certificates. Web browsers dropped support for SHA-1 in 2017.

As a replacement, NIST announced the SHA-2 standard, which has four major variants:

- SHA-256 produces a 256-bit message digest using a 512-bit block size.

- SHA-224 uses a truncated version of the SHA-256 hash that drops 32 bits to produce a 224-bit message digest using a 512-bit block size.
- SHA-512 produces a 512-bit message digest using a 1,024-bit block size.
- SHA-384 uses a truncated version of the SHA-512 hash that drops 128 bits to produce a 384-bit digest using a 1,024-bit block size.

**应试要点：**

- 🔥 SHA-1 被 NIST、浏览器、CA 机构全面弃用。
- ⚠️ SHA 系列与 AES 一样，是 NIST/FIPS 推广的政府标准。
- SHA-3 并非 SHA-2 的升级版，而是独立算法（使用 Keccak 函数）。

### 2. MD5: Message Digest Algorithm

概要：

- 长度：128 bits；
- 快速但已被证明容易碰撞（2005 年被 Arjen Lenstra 破解）；
- 仍有历史系统中出现（如旧证书、哈希校验工具）。

📘 应试要点：

- CISSP 会问你“哪个算法不能用于完整性校验”：选 MD5。
- 若题干涉及“生成两个具有相同摘要的文件”，考的是“碰撞攻击”。

The Message Digest 2 (MD2) hash algorithm was developed by Ronald Rivest (the same Rivest of Rivest, Shamir, and Adleman fame) in 1989 to provide a secure hash function for 8-bit processors. In 1990, Rivest enhanced his message digest algorithm to support 32-bit processors and increase the level of security with a version called MD4.

In 1991, Rivest released the next version of his message digest algorithm, which he called MD5. It also processes 512-bit blocks of the message, but it uses four distinct rounds of computation to produce a digest of the same length as the MD2 and MD4 algorithms (128 bits). MD5 has the same padding requirements as MD4—the message length must be 64 bits less than a multiple of 512 bits.

MD5 implements additional security features that reduce the speed of message digest production significantly. Unfortunately, cryptanalytic attacks demonstrated that the MD5 protocol is subject to collisions, preventing its use for ensuring message integrity. Specifically, Arjen Lenstra and others demonstrated in 2005 that it is possible to create two digital certificates from different public keys that have the same MD5 hash.

Some tools and systems still rely on MD5, so you may see it in use today, but it is now far better to rely on more secure hashing algorithms, such as SHA-2.

### 3. RIPEMD: （RIPE Message Digest）

| 算法           | 摘要长度 | 状态                       |
| -------------- | -------- | -------------------------- |
| RIPEMD         | 128 bits | ❌ 不安全                   |
| RIPEMD-128     | 128 bits | ❌ 不推荐                   |
| **RIPEMD-160** | 160 bits | ✅ 推荐                     |
| RIPEMD-256     | 256 bits | ❌ 仅摘要变长，无安全性提升 |
| RIPEMD-320     | 320 bits | ❌ 同上                     |

The RIPE Message Digest (RIPEMD) series of hash functions is an alternative to the SHA family that is used in some applications, such as Bitcoin cryptocurrency implementations. The family contains a series of increasingly sophisticated functions:

- RIPEMD produced a 128-bit digest and contained some structural flaws that rendered it insecure.
- RIPEMD-128 replaced RIPEMD, also producing a 128-bit digest, but it is also no longer considered secure.
- RIPEMD-160 is the replacement for RIPEMD-128 that remains secure today and is the most commonly used of the RIPEMD variants. It produces a 160-bit hash value.

You may also see references to RIPEMD-256 and RIPEMD-320. These functions are actually based on RIPEMD-128 and RIPEMD-160, respectively. They do not add any security; they simply create longer hash values for cases where a longer value is needed. RIPEMD-256 has the same level of security as RIPEMD-128, while RIPEMD-320 has the same level of security as RIPEMD-160. This leads to the unusual-sounding situation where RIPEMD-160 is secure, but RIPEMD-256 is not.

应试要点：

- **RIPEMD-160 是唯一本章中仍安全使用的版本**；
- RIPEMD-256 ≠ 更安全，仅摘要变长用于兼容格式要求；
- 比特币部分场景中使用 RIPEMD-160。

#### Comparison of Hash Algorithm Value Lengths

Table 7.1 – Hash Algorithm Memorization Chart

| **Name**          | **Hash Value Length**                     |
| ----------------- | ----------------------------------------- |
| HAVAL             | 128, 160, 192, 224, and 256 bits          |
| HMAC              | Variable                                  |
| MD5               | 128                                       |
| SHA-1             | 160                                       |
| SHA2-224/SHA3-224 | 224                                       |
| SHA2-256/SHA3-256 | 256                                       |
| SHA2-384/SHA3-384 | 384                                       |
| SHA2-512/SHA3-512 | 512                                       |
| RIPEMD-128        | 128                                       |
| RIPEMD-160        | 160                                       |
| RIPEMD-256        | 256 (but with equivalent security to 128) |
| RIPEMD-320        | 320 (but with equivalent security to 160) |

**总结**

| 模块               | 高频点                                 |
| ------------------ | -------------------------------------- |
| ✅ 哈希作用         | 完整性、签名                           |
| ✅ 五大要求         | 任意输入、固定输出、易算、单向、抗碰撞 |
| ❌ 不等同于加密     | 无法解码，非机密性工具                 |
| ❌ SHA-1/MD5 不安全 | 必须用 SHA-2 或 SHA-3                  |
| ✅ 哈希 + 签名      | 提供认证与不可否认性                   |

## Digital Signatures

Once you have chosen a cryptographically sound hash function and cryptographic algorithm, you can use it to implement a digital signature system. Digital signature infrastructures have two distinct goals:

1. Digitally signed messages assure the recipient that the message truly came from the claimed sender. They enforce nonrepudiation (that is, they preclude the sender from later claiming that the message is a forgery).
2. Digitally signed messages assure the recipient that the message was not altered while in transit between the sender and recipient. This protects against both malicious modification (a third party altering the meaning of the message) and unintentional modification (because of faults in the communications process, such as electrical interference).

**Digital signature** algorithms rely on a combination of **public key cryptograph**y and **hashing functions.**

If Alice wants to digitally sign a message she’s sending to Bob, she performs the following actions:

1. Alice generates a **message digest** (i.e., hash) of the original plaintext message using one of the cryptographically sound hashing algorithms, such as SHA2-512.

2. Alice then **encrypts only the message digest** using **owned private key**. This encrypted message digest is the **digital signature.**

3. Alice appends the signed message digest to the plaintext message.

4. Alice transmits the appended message to Bob.

When Bob receives the digitally signed message, he reverses the procedure, as follows:

1. Bob **decrypts the digital signature** using **Alice’s public key**.

2. Bob uses the **same hashing function to create a message digest of the full plaintext message** received from Alice.

3. Bob then **compares the decrypted message digest** he received from Alice with the message digest he computed himself. If the two digests match, he can be assured that the message he received was sent by Alice. If they do not match, either the message was not sent by Alice or the message was modified while in transit.

Note that the digital signature process does not provide confidentiality in and of itself. It only ensures that the cryptographic goals of integrity, authentication, and nonrepudiation are met. Let’s break that down. If the hash generated by the sender and the hash generated by the recipient match, then we know that the two hashed messages are identical and we have integrity. If the digital signature was verified with the public key of the sender, then we know that it was created using that sender’s private key. That private key should only be known to the sender, so the verification proves to the recipient that the signature came from the sender, providing origin authentication. The recipient (or anyone else) can then demonstrate that process to a third party, providing nonrepudiation.

However, if Alice also wanted to ensure the confidentiality of her message to Bob, she could add a step to the message creation process. After appending the signed message digest to the plaintext message, Alice could encrypt the entire message with Bob’s public key. When Bob received the message, he would decrypt it with his own private key before following the steps just outlined.

### 1. HMAC: hashed message authentication code

The hashed message authentication code (HMAC) algorithm implements a partial digital signature—it guarantees the integrity of a message during transmission, but it does not provide for nonrepudiation.

Because HMAC relies on a shared secret key, it does not provide any nonrepudiation functionality. However, it operates in a more efficient manner than the digital signature standard and may be suitable for applications in which symmetric key cryptography is appropriate. In short, it represents a halfway point between unencrypted use of a message digest algorithm and computationally expensive digital signature algorithms based on public key cryptography.

**Which Key Should I Use?**

1. If you want to encrypt a confidential message, use the recipient’s public key.
2. If you want to decrypt a confidential message sent to you, use your private key.
3. If you want to digitally sign a message you are sending to someone else, use your private key.
4. If you want to verify the signature on a message sent by someone else, use the sender’s public key.

These four rules are the core principles of public key cryptography and digital signatures.

### 2. Digital Signature Standard

**DSS 是专门用于“数字签名”的一套标准，规定了哪些非对称算法可以用于签名用途。**

NIST specifies the digital signature algorithms acceptable for federal government use in Federal Information Processing Standard (FIPS) 186-4, also known as the **Digital Signature Standard (DSS)**. This document specifies that all federally approved digital signature algorithms must use the **SHA-3 hashing** functions.

DSS also specifies the encryption algorithms that can be used to support a digital signature infrastructure. There are three currently approved **standard encryption algorithms**:

1. The Digital Signature Algorithm **(DSA)** as specified in FIPS 186-4. This algorithm is a variant of an algorithm developed by Dr. Taher Elgamal, the creator of the ElGamal asymmetric cryptosystem discussed earlier in this chapter.

2. The Rivest–Shamir–Adleman **(RSA)** algorithm, as specified in ANSI X9.31.

3. The Elliptic Curve DSA **(ECDSA)**, as specified in ANSI X9.62.

总结DSS的三大标准加密算法**standard encryption algorithms**

| 算法      | 全称                        | 描述                                         |
| --------- | --------------------------- | -------------------------------------------- |
| **DSA**   | Digital Signature Algorithm | 基于 ElGamal 改进，适用于签名，不能加密      |
| **RSA**   | Rivest–Shamir–Adleman       | 通用算法，可用于加密和签名（取决于密钥用途） |
| **ECDSA** | Elliptic Curve DSA          | ECC 变种，用于高性能数字签名                 |

| 算法               | 类型                      | 可用于签名？    | DSS 支持？        | 备注                         |
| ------------------ | ------------------------- | --------------- | ----------------- | ---------------------------- |
| **RSA**            | 加密/签名通用             | ✅               | ✅                 | 在 DSS 和加密场景都常用      |
| **ECC**            | 曲线密码学                | ✅（通过 ECDSA） | ✅（ECDSA 是子集） | 性能高，适合移动设备         |
| **DSA**            | 仅签名                    | ✅               | ✅                 | 不支持加密功能               |
| **ElGamal**        | 加密/签名通用（基础原型） | ⚠️ 限制较多      | ❌（非标准）       | DSS 不接受直接使用           |
| **Diffie–Hellman** | 密钥协商                  | ❌ 不可签名      | ❌                 | 不是签名算法，只能做密钥交换 |

**常考点：**

- DSA 和 ECDSA：✅ 只用于签名；❌ 不可用于加密；
- RSA：✅ 通用算法，可签名也可加密，是唯一“全能型”；
- DSS：✅ 签名标准，必须用 SHA-3 哈希算法生成MD，并限定可用于签名的公钥算法包括：DSA、RSA 和 ECDSA。
- Diffie–Hellman：❌ DSS 不支持；它用于密钥交换，不做签名；

## Public Key Infrastructure（PKI）

The major strength of public key encryption is its ability to facilitate communication between parties previously unknown to each other. This is made possible by the public key infrastructure (PKI) hierarchy of trust relationships. These trusts permit combining **asymmetric cryptography** with **symmetric cryptography** along with **hashing** and **digital certificates**, giving us **hybrid cryptography.**

| 提到的概念                  | 涵盖内容/含义                                                |
| --------------------------- | ------------------------------------------------------------ |
| **Asymmetric cryptography** | 公钥/私钥机制（如 RSA、ECC）                                 |
| **Symmetric cryptography**  | 快速的机密数据加密（如 AES）                                 |
| **Hashing**                 | 实质上就是**message digest**的生成方式                       |
| **Digital certificates**    | 内部就包含了**digital signatures**（由 CA 对用户公钥及身份信息的签名） |

所以在 PKI 系统中：

- **Hashing** → 生成 **Message Digest**
- **Private key** → 对 Digest 签名 → 生成 **Digital Signature**
- **Digital Certificate** = 签名 + 公钥 + 身份信息

### Digital Certificates 证书

**Digital certificates provide communicating parties with the assurance that the people they are communicating with truly are who they claim to be.** 

Digital certificates are essentially endorsed copies of an individual’s public key. When users verify that a certificate was signed by a trusted certificate authority (CA), they know that the public key is legitimate.

**Digital certificates** contain specific identifying information, and their construction is governed by an international standard—X.509. Certificates that conform to X.509 contain the following data:

- Version of X.509 to which the certificate conforms
- Serial number (from the certificate creator)
- Signature algorithm identifier (specifies the technique used by the certificate authority to digitally sign the contents of the certificate)
- Issuer name (identification of the certificate authority that issued the certificate)
- Validity period (specifies the dates and times—a starting date and time and an expiration date and time—during which the certificate is valid)
- Subject’s name (contains the common name [CN] of the certificate as well as the distinguished name [DN] of the entity that owns the public key contained in the certificate)
- Subject’s public key (the meat of the certificate—the actual public key the certificate owner used to set up secure communications) 

Certificates may be issued for a variety of purposes. These include providing assurance for the public keys of

- Computers/machines
- Individual users
- Email addresses
- Developers (code-signing certificates) 

The subject of a certificate may include a wildcard in the certificate name, indicating that the certificate is good for subdomains as well. The wildcard is designated by an asterisk character. For example, a wildcard certificate issued to *.example.org would be valid for all of the following domains:

- example.org
- www.example.org
- mail.example.org
- secure.example.org

### Digital Certificate Authorities

#### **Certificate Authorities (CAs)** 

- 作用：签发、吊销证书；建立信任根

- 常见厂商：DigiCert、GlobalSign、GoDaddy、Entrust、AWS 等

- **CA 本质是一种“可信第三方”**

CA 自身使用私钥对其他实体的公钥进行签名

**Certificate authorities (CAs)** are the glue that binds the public key infrastructure together. These neutral organizations offer notarization services for digital certificates. To obtain a digital certificate from a reputable CA, you must prove your identity to the satisfaction of the CA. The following list includes some of the major CAs who provide widely accepted digital certificates:

1. Symantec
2. IdenTrust
3. Amazon Web Services
4. GlobalSign
5. Comodo
6. Certum
7. GoDaddy
8. DigiCert
9. Secom
10. Entrust
11. Actalis
12. Trustwave

Nothing is preventing any organization from simply setting up shop as a CA. However, the certificates issued by a CA are only as good as the trust placed in the CA that issued them. This is an important item to consider when receiving a digital certificate from a third party. **If you don’t recognize and trust the name of the CA that issued the certificate, you shouldn’t place any trust in the certificate at all.** 

***PKI relies on a hierarchy of trust relationships.*** 

**重点考点：**

- CA 需要保护自己的私钥（通过**离线CA机制**等手段）
- 信任是**链式传递的**，一个被信任的 CA 发行的证书也会被信任

If you configure your browser to trust a CA, it will automatically trust all of the digital certificates issued by that CA. Browser developers preconfigure browsers to trust the major CAs to avoid placing this burden on users.

#### Registration authorities (RAs)

- **RA 是“辅助 CA”的身份验证机构**
- 自身不签发证书，只负责用户身份验证
- 分担 CA 的身份审查工作，支持远程办公场景

**Registration authorities (RAs)** assist CAs with the burden of verifying users’ identities prior to issuing digital certificates. They do not directly issue certificates themselves, but they play an important role in the certification process, allowing CAs to remotely validate user identities.

Certificate authorities must carefully protect their own private keys to preserve their trust relationships. To do this, they often use an offline CA to protect their root certificate, the top level certificate for their entire PKI. This offline CA is disconnected from networks and powered down until it is needed. The **offline CA** uses the root certificate to create subordinate intermediate CAs that serve as the online CAs used to issue certificates on a routine basis.

#### Chain of Trust

- **核心机制**：验证一个证书的合法性时，不是直接信任它，而是 **逐级追溯到信任的根CA**
- 每一层 CA 通过签名下一级 CA 的证书来建立信任链
- 根 CA 一般通过浏览器预装或操作系统信任

📌 **考试提示**：

- 信任链中，只有**根证书是自签名（self-signed）**的
- 中间 CA 的证书由**上级 CA 签发**

In the **CA trust model**, the use of a series of **intermediate CAs** is known as **certificate chaining.** To validate a certificate, the browser verifies the identity of the intermediate CA(s) first and then traces the path of **trust back to a known root CA**, verifying the identity of each link in the **chain of trust.**

Certificate authorities do not need to be third-party service providers. Many organizations operate **internal CAs that provide self-signed certificates for use inside an organization.** These certificates won’t be trusted by the browsers of external users, but internal systems may be configured to trust the internal CA, saving the expense of obtaining certificates from a third-party CA.

#### Internal vs. External CA

- **第三方 CA（External）**：用于公开互联网信任链，如 TLS 证书
- **企业内部 CA（Internal）**：用于内部系统，非公开信任，节约成本

📌 CISSP 常考点：

- **内部 CA 颁发的证书默认不会被浏览器信任**
- 需要通过浏览器手动导入 CA 根证书或设置受信策略

总结

| 类别         | 要点                                               |
| ------------ | -------------------------------------------------- |
| 数字证书目的 | 验证某个公钥是否属于声明者                         |
| X.509结构    | 版本、序列号、签名算法、颁发者、有效期、主题、公钥 |
| CA 作用      | 签名证书、建立信任                                 |
| RA 作用      | 验证用户身份，辅助 CA                              |
| 离线 CA      | 保护根私钥，避免密钥泄露                           |
| 信任链       | 通过逐层签名建立，从中间 CA 验证到根 CA            |
| 通配符证书   | 一个证书保护多个子域名（如 `*.example.com`）       |

### Digital Certificate Lifecycle

The technical concepts behind the public key infrastructure are relatively simple. In the following sections, we’ll cover the processes used by certificate authorities to create, validate, and revoke client certificates.

```css
[Enrollment] → [Verification] → [Revocation]
       ↓             ↓               ↓
   CSR 提交      签名验证       吊销列表/OCSP/Stapling
   身份认证      有效期检查       实时状态查询
   类型选择      信任链追溯       浏览器判断是否信任

```

#### 1.Enrollment

🎯 核心概念：

用户向 CA 申请数字证书时，必须首先完成身份验证（称为 enrollment）。

🌟 关键步骤：

1. 提交 **CSR（Certificate Signing Request）**，内含用户的 **公钥** 和 **身份信息**
2. CA 验证身份（可为人工、信用信息、组织渠道等）
3. CA 使用 **自己的私钥** 对信息签名，生成用户的 **X.509 证书**

When you want to obtain a digital certificate, you must first prove your identity to the CA in some manner; this process is called enrollment. This sometimes involves physically appearing before an agent of the certificate authority with the appropriate identification documents. Some certificate authorities provide other means of verification, including the use of credit report data and identity verification by trusted community leaders.

Once you’ve satisfied the certificate authority (CA) regarding your identity, you provide them with your public key in the form of a **certificate signing request (CSR).** The CA next creates an X.509 digital certificate containing your identifying information and a copy of your public key. The CA then digitally signs the certificate using the CA’s private key and provides you with a copy of your signed digital certificate. You may then safely distribute this certificate to anyone with whom you want to communicate securely.

Certificate authorities issue different types of certificates depending upon the level of identity verification that they perform. The simplest, and most common, certificates are **Domain Validation (DV)** certificates, where the CA simply verifies that the certificate subject has control of the domain name. 

**Extended Validation (EV)** certificates provide a higher level of assurance and the CA takes steps to verify that the certificate owner is a legitimate business before issuing the certificate.

| 类型                              | 验证级别 | 说明                                 |
| --------------------------------- | -------- | ------------------------------------ |
| **DV（Domain Validation）**       | 最低     | 仅验证域名控制权                     |
| **OV（Organization Validation）** | 中等     | 验证组织合法性和域名                 |
| **EV（Extended Validation）**     | 最高     | 严格验证法人身份与合法性，绿色地址栏 |

**考试要点提示：**

- CSR 是申请证书时提供的结构化请求，含 **公钥**，由用户生成
- CA 通过签名方式担保公钥与身份绑定关系

#### 2.Verification

🎯 核心概念：接收到证书后，通信方需要验证证书是否可信。

验证要素清单：

1. **CA 数字签名有效**（使用 CA 的公钥验证）
2. **CA 是否被信任**（在本地系统/浏览器信任列表中）
3. **证书未过期**（检查有效期起止时间）
4. **证书未被吊销**（通过 CRL 或 OCSP 检查）
5. **证书字段正确匹配用途**（例如是否包含所需的 Email、DNS、姓名等字段）

📌 **证书绑定的数据决定你信任的具体内容**：

- 如果证书只写了 email，则你只信任这个 email 地址
- 如果证书包括姓名、电话、地址，那你可信任这些信息已被 CA 验证过

When you receive a digital certificate from someone with whom you want to communicate, you verify the certificate by checking the CA’s digital signature using the CA’s public key. You then must check the validity period of the certificate to ensure that the current date is after the starting date of the certificate and that the certificate has not yet expired. Finally, you must check and ensure that the certificate was not revoked using a **certificate revocation list (CRL)** or the **Online Certificate Status Protocol (OCSP).** At this point, you may assume that the public key listed in the certificate is authentic, provided that it satisfies the following requirements:

- The digital signature of the CA is authentic.
- You trust the CA.
- The certificate is not listed on a CRL.
- The certificate actually contains the data you are trusting.

The last point is a subtle but extremely important item. Before you trust an identifying piece of information about someone, be sure that it is actually contained within the certificate. If a certificate contains the email address (billjones@foo.com) but not the individual’s name, you can be certain only that the public key contained therein is associated with that email address. The CA is not making any assertions about the actual identity of the billjones@foo.com email account. However, if the certificate contains the name Bill Jones along with an address and telephone number, the CA is vouching for that information as well.

Digital certificate verification algorithms are built into a number of popular web browsing and email clients, so you won’t often need to get involved in the particulars of the process. However, it’s important to have a solid understanding of the technical details taking place behind the scenes to make appropriate security judgments for your organization. It’s also the reason that, when purchasing a certificate, you choose a CA that is widely trusted. If a CA is not included in, or is later pulled from, the list of CAs trusted by a major browser, it will greatly limit the usefulness of your certificate.

**Certificate pinning** approaches instruct browsers to attach a certificate to a subject for an extended period of time. When sites use certificate pinning, the browser associates that site with their public key. This allows users or administrators to notice and intervene if a certificate unexpectedly changes.

#### 3. Revocation

##### 吊销原因（记忆口诀：**漏、错、变、离**）

1. **泄漏**（私钥被泄露）
2. **错误**（CA 错误签发）
3. **信息变更**（如姓名更改）
4. **关系中止**（持有者离职）

Occasionally, a certificate authority needs to revoke a certificate. This might occur for one of the following reasons:

1. The certificate was compromised (for example, the certificate owner accidentally gave away the private key).
2. The certificate was erroneously issued (for example, the CA mistakenly issued a certificate without proper verification).
3. The details of the certificate changed (for example, the subject’s name changed).
4. The security association changed (for example, the subject is no longer employed by the organization sponsoring the certificate).

##### CPS 与证书生命周期管理策略

- **CPS（Certificate Practice Statement）**：定义 CA 吊销响应时间、证书签发策略、验证流程等。
- **证书 Pinning**：绑定某网站与特定公钥，防止中间人攻击或证书伪造。
- **证书更新与续期**：通常在有效期结束前由持有人发起新的 enrollment 流程。

The revocation request grace period is the maximum response time within which a CA will perform any requested revocation. This is defined in the **Certificate Practice Statement (CPS).** The CPS states the practices a CA employs when issuing or managing certificates.

##### 吊销方式与机制

| 方式                         | 描述                                       | 优缺点                               |
| ---------------------------- | ------------------------------------------ | ------------------------------------ |
| **CRL**（证书吊销列表）      | 包含所有被吊销证书的序列号                 | 有延迟、需定期更新                   |
| **OCSP**（在线证书状态协议） | 实时查询证书状态（valid/invalid/unknown）  | 实时性好，服务器负担大               |
| **OCSP Stapling**            | 由服务器预取 OCSP 签名状态，附带发送给用户 | 大幅减少负载，提升性能，主流推荐方案 |

You can use three techniques to verify the authenticity of certificates and identify revoked certificates:

1. **Certificate Revocation Lists** Certificate revocation lists (CRLs) are maintained by the various certificate authorities and contain the serial numbers of certificates that have been issued by a CA and that have been revoked, along with the date and time the revocation went into effect. The major disadvantage to certificate revocation lists is that they must be downloaded and cross-referenced periodically, introducing a period of latency between the time a certificate is revoked and the time end users are notified of the revocation.
2. **Online Certificate Status Protocol (OCSP)** This protocol eliminates the latency inherent in the use of certificate revocation lists by providing a means for real-time certificate verification. When a client receives a certificate, it sends an OCSP request to the CA’s OCSP server. The server then responds with a status of valid, invalid, or unknown. The browser uses this information to determine whether the certificate is valid.
3. **Certificate Stapling** The primary issue with OCSP is that it places a significant burden on the OCSP servers operated by certificate authorities. These servers must process requests from every single visitor to a website or other user of a digital certificate, verifying that the certificate is valid and not revoked.

Certificate stapling is an extension to the Online Certificate Status Protocol that relieves some of the burden placed on certificate authorities by the original protocol. When a user visits a website and initiates a secure connection, the website sends its certificate to the end user, who would normally then be responsible for contacting an OCSP server to verify the certificate’s validity. In certificate stapling, the web server contacts the OCSP server itself and receives a signed and timestamped response from the OCSP server, which it then attaches, or staples, to the digital certificate. Then, when a user requests a secure web connection, the web server sends the certificate with the stapled OCSP response to the user. The user’s browser then verifies that the certificate is authentic and also validates that the stapled OCSP response is genuine and recent. Because the CA signed the OCSP response, the user knows that it is from the certificate authority, and the timestamp provides the user with assurance that the CA recently validated the certificate. From there, communication may continue as normal.

The time savings come when the next user visits the website. The web server can simply reuse the stapled certificate without recontacting the OCSP server. As long as the timestamp is recent enough, the user will accept the stapled certificate without needing to contact the CA’s OCSP server again. It’s common to have stapled certificates with a validity period of 24 hours. That reduces the burden on an OCSP server from handling one request per user over the course of a day, which could be millions of requests, to handling one request per certificate per day. That’s a tremendous reduction.

OCSP Stapling 是高频考试内容，**关键优势在于减轻 CA 的 OCSP 服务器负载，同时提升用户体验和验证效率。**

##### 总结：生命周期核心流程一图理解

| 阶段         | 内容                           | CISSP 考点提示                         |
| ------------ | ------------------------------ | -------------------------------------- |
| Enrollment   | 身份验证、提交 CSR、签名证书   | CSR 内含申请方公钥，CA 签名保证绑定    |
| Verification | 签名验证、有效性检查、吊销检测 | 需确认字段准确、有效期及信任链         |
| Revocation   | CRL、OCSP、Stapling            | OCSP Stapling 为推荐机制，减少性能消耗 |

### Certificate Formats

Digital certificates are stored in files, and those files come in a variety of different formats, both binary and text-based:

1. The most common binary format is the **Distinguished Encoding Rules (DER)** format. DER certificates are normally stored in files with the .der, .crt, or .cer extension.

   1. ✅ **编码方式**：**二进制格式**
   2. ✅ **标准**：ASN.1 的一种编码规范，用于传输结构化数据
   3. ✅ **文件扩展名**：`.der`, `.crt`, `.cer`
   4. ✅ **应用场景**：
      - 常见于 **Java 系统（JVM）和 Linux/Unix 服务器**
      - 不可直接查看内容（需使用工具如 `openssl` 解码）

   📌 **考点提示**：DER 是证书的原始二进制格式，PEM 是其 ASCII 编码形式。

2. The **Privacy Enhanced Mail (PEM)** certificate format is an ASCII text version of the DER format. PEM certificates are normally stored in files with the .pem or .crt extension.

   1. ✅ **编码方式**：**Base64 编码的文本格式**

   2. ✅ **格式内容**：-----BEGIN CERTIFICATE-----

      Base64 encoded content
      -----END CERTIFICATE-----

   3. ✅ **文件扩展名**：`.pem`, `.crt`, `.cer`

   4. ✅ **应用场景**：

      - **Apache** 和 **NGINX Web Server**
      - **OpenSSL 工具链**
      - 可通过文本编辑器打开并阅读
      - 📌 **记忆技巧**：PEM = Plain-text Encoded Message

3. The **Personal Information Exchange (PFX)** format is commonly used by Windows systems. PFX certificates may be stored in binary form, using either .pfx or .p12 file extensions.

   1. ✅ **编码方式**：**二进制格式**
   2. ✅ **扩展名**：`.pfx`, `.p12`
   3. ✅ **特点**：
      - 不仅包含证书，还能打包私钥和完整证书链（certificate chain）
      - 支持加密和密码保护
   4. ✅ **应用场景**：
      - **Windows 系统中的导入/导出证书和私钥**
      - 用于浏览器和 S/MIME 邮件加密场景

   📌 **考试重点**：PFX/P12 文件 **同时包含私钥 + 公钥证书**，使用密码保护。

4. Windows systems also use **P7B** certificates, which are stored in ASCII text format.

   1. ✅ **编码方式**：**ASCII文本格式**
   2. ✅ **扩展名**：`.p7b`
   3. ✅ **特点**：
      - 通常包含 **证书链**（中间证书 + 根证书 + 目标证书），**不包含私钥**
   4. ✅ **应用场景**：
      - 用于导入受信任的 CA 链
      - 常用于 **Windows 和 Java Keytool**

   📌 **考试点**：P7B 文件**不包含私钥**，通常用于传输完整的信任链。

#### Summary of digital certificate formats

Certificate Formats Comparison Table（应试速记表）

| 格式名      | 编码方式      | 扩展名           | 包含内容           | 常见平台        | 私钥支持 |
| ----------- | ------------- | ---------------- | ------------------ | --------------- | -------- |
| **DER**     | Binary        | .der, .crt, .cer | 单个证书           | Linux/Java      | ❌        |
| **PEM**     | Text (Base64) | .pem, .crt       | 单个或多个证书     | Apache/OpenSSL  | ❌        |
| **PFX/P12** | Binary        | .pfx, .p12       | 证书 + 私钥 + CA链 | Windows/Browser | ✅        |
| **P7B**     | Text          | .p7b             | 证书链（不含私钥） | Windows/Java    | ❌        |

**CISSP 典型考点总结：**

- DER 和 PEM 都可用于单个证书，但 PEM 可读性更好。
- PFX/P12 是唯一包含私钥的格式，**必须加密**以保证安全。
- P7B 用于携带证书链，适合用来建立 **信任路径**，**不包含私钥**。
- PEM、P7B 为文本格式；DER、PFX 为二进制格式。

## Asymmetric Key Management

When working within the public key infrastructure, you must comply with several best practice requirements to maintain the security of your communications.

1. First, choose your encryption system wisely. As you learned earlier, “security through obscurity” is not an appropriate approach. Choose an encryption system with an algorithm in the public domain that has been thoroughly vetted by industry experts. Be wary of systems that use a “black-box” approach and maintain that the secrecy of their algorithm is critical to the integrity of the cryptosystem.
2. You must also select your keys in an appropriate manner. Use a key length that balances your security requirements with performance considerations. Also, ensure that your key is truly random. Any patterns within the key increase the likelihood that an attacker will be able to break your encryption and degrade the security of your cryptosystem.
3. When using public key encryption, keep your private key secret! Do not, under any circumstances, allow anyone else to gain access to your private key. Remember, allowing someone access even once permanently compromises all communications that take place (past, present, or future) using that key and allows the third party to successfully impersonate you.
4. Retire keys when they’ve served a useful life. Many organizations have mandatory key rotation requirements to protect against undetected key compromise. If you don’t have a formal policy that you must follow, select an appropriate interval based on the frequency with which you use your key. You might want to change your key pair every few months, if practical.
5. Back up your key! If you lose the file containing your private key because of data corruption, disaster, or other circumstances, you’ll certainly want to have a backup available. You may want to either create your own backup or use a key escrow service that maintains the backup for you. In either case, ensure that the backup is handled in a secure manner. After all, it’s just as important as your primary key file!
6. Hardware security modules (HSMs) also provide an effective way to manage encryption keys. These hardware devices store and manage encryption keys in a secure manner that prevents humans from ever needing to work directly with the keys. Many of them are also capable of improving the efficiency of cryptographic operations, in a process known as hardware acceleration. HSMs range in scope and complexity from very simple devices, such as the YubiKey, that store encrypted keys on a USB drive for personal use, to more complex enterprise products that reside in a data center. HSMs include tamper-resistance mechanisms to prevent someone who gains physical access to the device from accessing the cryptographic material it maintains. Cloud providers, such as Amazon and Microsoft, also offer cloud-based HSMs that provide secure key management for infrastructure-as-a-service (IaaS) services.

## Hybrid Cryptography

You’ve now learned about the **two major categories of cryptographic systems**: 

1. symmetric algorithms
2. asymmetric algorithms

You’ve also learned about the major advantages and disadvantages of each. Chief among these are the facts that symmetric algorithms are fast but introduce key distribution challenges and, though asymmetric algorithms solve the key distribution problem, they are also computationally intensive and slow. If you’re choosing between these approaches, you’re forced to make a decision between convenience and speed.

**Hybrid cryptography** combines symmetric and asymmetric cryptography to **achieve the key distribution benefits of asymmetric cryptosystems with the speed of symmetric algorithms.** 

These approaches work by setting up an initial connection between two communicating entities using asymmetric cryptography. That connection is used for only one purpose: the exchange of a randomly generated shared secret key, known as an ephemeral key. 

The two parties then exchange whatever data they wish using the shared secret key with a symmetric algorithm. When the communication session ends, they discard the ephemeral key and then repeat the same process if they wish to communicate again later.

The beauty behind this approach is that it uses asymmetric cryptography for key distribution, a task that requires the encryption of only a small amount of data. Then it switches to the faster symmetric algorithm for the vast majority of data exchanged.

**Transport Layer Security (TLS)** is the most well-known example of hybrid cryptography.

## Applied Cryptography

Examine the use of cryptography to secure data at rest, such as that stored on portable devices, as well as data in transit, using techniques that include secure email, encrypted web communications, and networking.

### 1. Portable Devices

The now ubiquitous nature of laptop computers, smartphones, and tablets brings new risks to the world of computing. Those devices often contain highly sensitive information that, if lost or stolen, could cause serious harm to an organization and its customers, employees, and affiliates. For this reason, many organizations turn to encryption to protect the data on these devices in the event they are misplaced.

Full Disk Encryption (FDE) 工具和操作系统支持

| 平台               | 内建加密工具                             |
| ------------------ | ---------------------------------------- |
| **Windows**        | BitLocker、EFS（Encrypting File System） |
| **macOS**          | FileVault                                |
| **Linux / 跨平台** | VeraCrypt（开源）                        |

Current versions of popular operating systems now include disk encryption capabilities that make it easy to apply and manage encryption on portable devices. For example, Microsoft Windows includes the BitLocker and Encrypting File System (EFS) technologies, macOS includes FileVault encryption, and the VeraCrypt open source package allows the encryption of disks on Linux, Windows, and Mac systems.

**CISSP重点**：

- **BitLocker 与 TPM 配合使用**效果更佳（见下一节）。
- **EFS** 是文件级加密，不是整盘加密（FDE）。
- **FileVault** 是 Apple 原生的整盘加密方案。

#### Trusted Platform Module (TPM) – 可信平台模块

TPM 是集成在主板上的**专用硬件加密模块**，主要用于：

- **存储并保护密钥**（例如用于 FDE 的解密密钥）
- **系统启动完整性检查**
- **增强身份验证机制**（如仅用户验证成功后才释放密钥）
- **防止物理迁移攻击**（如将加密硬盘安装到其他设备中尝试破解）

✅ **考点提醒**：

- BitLocker 能够借助 TPM 自动管理加密密钥，提高安全性和用户体验。
- TPM 增强物理安全性，但一旦 TPM 芯片损坏，若无恢复密钥可能无法解密。

Modern computers often include a specialized cryptographic component known as a Trusted Platform Module (TPM). The TPM is a chip that resides on the motherboard of the device. The TPM serves a number of purposes, including the storage and management of keys used for full-disk encryption (FDE) solutions. The TPM provides the operating system with access to the keys only if the user successfully authenticates. This prevents someone from removing the drive from one device and inserting it into another device to access the drive’s data.

A wide variety of commercial tools are available that provide added features and management capability. The major differentiators between these tools are how they protect keys stored in memory, whether they provide full-disk or volume-only encryption, and whether they integrate with hardware-based Trusted Platform Modules (TPMs) to provide added security. Any effort to select encryption software should include an analysis of how well the alternatives compete on these characteristics.

Don’t forget about smartphones when developing your portable device encryption policy. Most major smartphone and tablet platforms include enterprise-level functionality that supports encryption of data stored on the phone.

##### 加密工具选型要素（软件 vs 硬件）

在选择企业级加密解决方案时，建议考虑以下因素：

- **是否支持 TPM 集成**
- **支持的加密范围**：整盘加密 vs 卷加密 vs 文件加密
- **密钥保护方式**：密钥存储是否安全（例如是否易被提取）
- **是否具备集中管理功能**：便于 IT 审计和策略实施

##### 移动设备（智能手机和平板）

不要忽视手机与平板的加密能力：

- **iOS 和 Android** 都支持内建的数据加密（如 iOS 默认在设备锁启用时加密整个存储）
- 企业可通过 **MDM（移动设备管理）策略** 强制开启设备加密
- 手机丢失时，可通过远程擦除保障数据安全（如 iCloud 的“Find My iPhone”）

✅ **考试高频点**：

- 企业移动策略应覆盖所有便携式设备，包括 **手机**、**USB**、**移动硬盘**。

##### CISSP考试总结

| 项目         | 要点                                         |
| ------------ | -------------------------------------------- |
| BitLocker    | Windows FDE，支持与 TPM 集成，提高密钥安全性 |
| FileVault    | macOS 原生整盘加密                           |
| VeraCrypt    | 免费开源跨平台 FDE 工具                      |
| TPM 芯片     | 存储加密密钥；提高防拆解物理安全性           |
| 移动设备加密 | 应通过 MDM 强制执行，支持远程擦除和锁定      |

### 2. Email

电子邮件是最常见的通信工具之一，必须针对其提供保密性、完整性、身份验证和不可否认性。下表总结了加密邮件时的常见需求与应对机制：

| **需求**                     | **安全机制**           |
| ---------------------------- | ---------------------- |
| 保密性（Confidentiality）    | 加密（对称加密）       |
| 完整性（Integrity）          | 哈希（如 SHA-256）     |
| 身份验证（Authentication）   | 数字签名（非对称加密） |
| 不可否认性（Nonrepudiation） | 数字签名               |
| 所有四项                     | 加密 + 数字签名        |

We have mentioned several times that security should be cost-effective. When it comes to email, simplicity is the most cost-effective option, but sometimes cryptography functions provide specific security services that you can’t avoid using. Since ensuring security is also cost-effective, here are some simple rules about encrypting email:

- If you need confidentiality when sending an email message, encrypt the message.
- If your message must maintain integrity, you must hash the message.
- If your message needs authentication, integrity, and/or nonrepudiation, you should digitally sign the message.
- If your message requires confidentiality, integrity, origin authentication, and nonrepudiation, you should encrypt and digitally sign the message.

It is always the responsibility of the sender to put proper mechanisms in place to ensure that the security (that is, confidentiality, integrity, authenticity, and nonrepudiation) of a message or transmission is maintained.

##### 加密邮件的核心原则

- ✅ **加密邮件**：确保只有指定接收者可以读取邮件内容（对称密钥加密，密钥用接收方公钥加密）
- ✅ **数字签名**：验证发件人身份、提供完整性和不可否认性（对消息摘要用私钥加密）
- ✅ **双重保障**：如需同时保障机密性与签名，应当**先签名再加密**

One of the most in-demand applications of cryptography is encrypting and signing email messages. Until recently, encrypted email required the use of complex, awkward software that in turn required manual intervention and complicated key exchange procedures. An increased emphasis on security in recent years resulted in the implementation of strong encryption technology in mainstream email packages. Next, we’ll look at some of the secure email standards in widespread use today.

#### 1. Pretty Good Privacy (PGP) 安全电子邮件协议

开发者：Phil Zimmerman（1991 年）

信任模型：**Web of Trust**

- 信任从某个已知用户传递到其信任的其他人
- 用户自行管理密钥信任关系

算法支持：支持多种加密算法、哈希函数、签名机制（如 RSA, AES, SHA 等）

常见实现：

- **OpenPGP**（开源）
- 商业版本（Symantec）

发送格式：通常使用**ASCII编码格式**发送（适配其他邮件系统）

优缺点：

| 优点                                        | 缺点                             |
| ------------------------------------------- | -------------------------------- |
| 用户可控性强、灵活性高                      | 密钥管理复杂，非技术用户不易操作 |
| 可通过插件或第三方服务简化（如 ProtonMail） | 不适合大规模组织部署             |

Phil Zimmerman’s Pretty Good Privacy (PGP) secure email system appeared on the computer security scene in 1991. It combines the CA hierarchy described earlier in this chapter with the “web of trust” concept—that is, you must become trusted by one or more PGP users to begin using the system. You then accept their judgment regarding the validity of additional users and, by extension, trust a multilevel “web” of users descending from your initial trust judgments.

PGP initially encountered a number of hurdles to widespread use. The most difficult obstruction was the U.S. government export regulations, which treated encryption technology as munitions and prohibited the distribution of strong encryption technology outside the United States. Fortunately, this restriction has since been repealed, and PGP may be freely distributed to most countries.

PGP is available in two versions: the commercial product that is now sold by Symantec and an open source variant called OpenPGP. These products allow for the use of modern encryption algorithms, hash functions, and signature standards within the PGP framework.

PGP messages are often sent in text-encoded format to facilitate compatibility with other email systems.

It is not possible to tell that this message is digitally signed until after it is decrypted.

Many commercial providers also offer PGP-based email services as web-based cloud email offerings, mobile device applications, or webmail plug-ins. These services appeal to administrators and end users because they remove the complexity of configuring and maintaining encryption certificates and provide users with a managed secure email service. Some products in this category include ProtonMail, StartMail, Mailvelope, SafeGmail, and Hushmail.

#### 2. S/MIME（Secure/Multipurpose Internet Mail Extensions） 安全电子邮件协议

- 标准支持：**RSA Security 主推**
- 加密机制：使用 **RSA 非对称加密 + X.509 证书**
- 支持功能：
  - 加密（保密性）
  - 数字签名（完整性、身份验证）
- 集成平台：
  - Microsoft Outlook / Office 365
  - Apple Mail
  - Google Workspace Enterprise

**密钥管理：**

- 通过 X.509 证书实现对称密钥交换（用于内容加密）
- 证书通常由受信任的 CA 签发
- 用户可通过证书验证邮件签名或进行邮件加密

**优缺点：**

| 优点                         | 缺点                                |
| ---------------------------- | ----------------------------------- |
| 更适合企业环境，整合 CA 架构 | 依赖证书基础设施（PKI）部署         |
| 融入常见桌面客户端较好       | 主流 Web 邮箱缺乏原生支持（需插件） |

The Secure/Multipurpose Internet Mail Extensions (S/MIME) protocol has emerged as a de facto standard for encrypted email. S/MIME uses the RSA encryption algorithm and has received the backing of major industry players, including RSA Security. S/MIME has already been incorporated in a large number of commercial products, including these:

- Microsoft Outlook and Office 365
- Apple Mail
- Google G Suite Enterprise edition

S/MIME relies on the use of X.509 certificates for exchanging cryptographic keys. The public keys contained in these certificates are used for digital signatures and for the exchange of symmetric keys used for longer communications sessions. Users who receive a message signed with S/MIME will be able to verify that message by using the sender’s digital certificate. Users who wish to use S/MIME for confidentiality or wish to create their own digitally signed messages must obtain their own certificates.

Despite strong industry support for the S/MIME standard, technical limitations have prevented its widespread adoption. Although major desktop mail applications support S/MIME email, mainstream web-based email systems do not support it out of the box (the use of browser extensions is required).

##### CISSP 应试提示

- PGP 使用 “Web of Trust”，用户自主管理信任；S/MIME 使用 CA 证书体系，适合组织部署。
- 使用 **数字签名** 提供完整性、身份验证与不可否认性（用发送者私钥签名消息摘要）。
- 邮件**加密 + 签名**时，必须**先签名再加密**：防止签名被篡改或伪造。
- Web-based 邮箱对 S/MIME 支持有限，是现实部署难点。

### 3. Web Applications

Encryption is widely used to protect web transactions. This is mainly because of the strong movement toward ecommerce and the desire of both ecommerce vendors and consumers to securely exchange financial information (such as credit card information) over the web. We’ll look at the two technologies that are responsible for the small lock icon within web browsers—Secure Sockets Layer (SSL) and Transport Layer Security (TLS).

#### 1. SSL（Secure Sockets Layer）- 已废弃

- **创建者**：Netscape
- **用途**：为 HTTP 通信提供安全加密，成为 HTTPS 的基础
- **问题**：存在**严重安全漏洞**（如 BEAST、POODLE），不支持现代加密算法（如 AES-GCM），如今已**被淘汰**
- **历史地位**：为 TLS 提供了设计基础，不再安全，TLS 已取代之

🛑 **考试重点提示**：

- SSL 是 **已废弃协议**，CISSP 会明确考你 TLS 替代了不安全的 SSL。
- 如果你听到“SSL”，**警惕是否实际上是 TLS**。

SSL was originally developed by Netscape to provide client/server encryption for web traffic sent using the Hypertext Transfer Protocol Secure (HTTPS). Over the years, security researchers discovered a number of critical flaws in the SSL protocol that render it insecure for use today. However, SSL serves as the technical foundation for its successor, Transport Layer Security (TLS), which remains widely used today.

Even though TLS has been in existence for more than a decade, many people still mistakenly call it SSL. When you hear people use the term SSL, that’s a red flag that you should further investigate to ensure that they’re really using the modern, secure TLS and not the outdated SSL.

#### 2. TLS（Transport Layer Security）– 主流安全协议

TLS 是现代网页安全通信协议的主力，它结合**非对称加密**和**对称加密**，兼顾安全与性能。

##### TLS 通信流程

1. **浏览器请求服务器** → 获取服务器的 **数字证书**
2. **提取公钥** → 浏览器生成**对称会话密钥（ephemeral key）**
3. **用公钥加密对称密钥** → 发送给服务器
4. **服务器用私钥解密** → 建立共享对称密钥
5. **接下来全部通信** → 使用对称加密完成（速度快）

📌 这叫做：**Hybrid Cryptosystem（混合加密系统）**

- 非对称加密（**RSA**/ECC）用来安全交换密钥
- 对称加密（**AES**）用来高速传输大量数据

##### 协议演进

| 版本        | 状态         | 特点                                                |
| ----------- | ------------ | --------------------------------------------------- |
| TLS 1.0/1.1 | 弃用         | 存在安全问题，不建议使用                            |
| TLS 1.2     | 广泛支持     | 强制弃用 SSL 3.0 fallback，推荐用于现代应用         |
| TLS 1.3     | 当前推荐标准 | 更快、更安全，取消了多个弱加密算法和 handshake 流程 |

TLS relies on the exchange of server digital certificates to negotiate encryption/decryption parameters between the browser and the web server. TLS’s goal is to create secure communications channels that remain open for an entire web browsing session. It depends on a combination of symmetric and asymmetric cryptography. The following steps are involved:

1. When a user accesses a website, the browser retrieves the web server’s certificate and extracts the server’s public key from it.
2. The browser creates a random symmetric key (known as the ephemeral key), uses the server’s public key to encrypt it, and sends the encrypted symmetric key to the server.
3. The server decrypts the symmetric key using its own private key, and the two systems exchange all future messages using the symmetric encryption key.

This approach allows TLS to leverage the advanced functionality of asymmetric cryptography while encrypting and decrypting the vast majority of the data exchanged using the faster symmetric algorithm.

When TLS was first proposed as a replacement for SSL, not all browsers supported the more modern approach. To ease the transition, early versions of TLS supported downgrading communications to SSL v3.0 when both parties did not support TLS. However, in 2011, TLS v1.2 dropped this backward compatibility.

In 2014, an attack known as the Padding Oracle On Downgraded Legacy Encryption (POODLE) demonstrated a significant flaw in the SSL 3.0 fallback mechanism of TLS. In an effort to remediate this vulnerability, many organizations completely dropped SSL support and now rely solely on TLS security.

##### Cipher Suites（密码套件）

TLS 并非一个具体算法，而是 **一个协议框架**，通过 Cipher Suite 指定使用哪些加密组件。

Each system supporting TLS provides a listing of the cipher suites that it supports. These are combinations of encryption algorithms that it is willing to use together, and these lists are used by two systems to identify a secure option that both systems support. The cipher suite consists of four components:

1. The key exchange algorithm that will be used to exchange the ephemeral key. For example, a server might support RSA, Diffie–Hellman (abbreviated DH) and Elliptic Curve Diffie Hellman (abbreviated ECDH).

2. The authentication algorithm that will be used to prove the identity of the server and/or client. For example, a server might support RSA, DSA, and ECDSA.

3. The bulk encryption algorithm that will be used for symmetric encryption. For example, a server might support multiple versions of AES and 3DES.

4. The hash algorithm that will be used to create message digests. For example, a server might support different versions of the SHA algorithm.

**Cipher suites are usually expressed in long strings that combine each of these four elements.** For example, the cipher suite: ```TLS_DH_RSA_WITH_AES_256_CBC_SHA384``` means that 

1. the server supports TLS using **Diffie–Hellman key exchange (DH).** 
2. It will perform authentication using the **RSA** protocol 
3. It will perform bulk encryption using **AES CBC mode with a 256-bit key**. 
4. **Hashing** will take place using the **SHA-384** **algorithm**.

一个 Cipher Suite 包含四个部分：

| 部分类型        | 举例                | 用途                                            |
| --------------- | ------------------- | ----------------------------------------------- |
| Key Exchange    | RSA, DH, ECDHE      | 共享交换对称加密密钥                            |
| Authentication  | RSA, DSA, ECDSA     | 身份验证（通常验证服务器）通过数字证书+数字签名 |
| Bulk Encryption | AES, 3DES（已弃用） | 对称加密大量传输数据                            |
| Hash Algorithm  | SHA-2, SHA-3        | 消息摘要，验证完整性                            |

示例解析：

```
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
```

- ECDHE：使用椭圆曲线 Diffie–Hellman 做密钥交换
- RSA：用于服务器身份认证
- AES_128_GCM：使用 AES 128 位密钥 + GCM 模式做对称加密
- SHA256：用于消息摘要（防篡改）

##### TLS 1.3 握手完整流程图解

```
Client                                          Server
  |                                                |
  |---------- 1. ClientHello (with key_share) ---->|
  |                                                |
  |<------ 2. ServerHello (with key_share) --------|
  |                                                |
  |<------- 3. Certificate + Signature ------------|
  |                                                |
  |<------- 4. Finished (with MAC) ----------------|
  |                                                |
  |------ 5. Finished (with MAC) ----------------->|
  |                                                |
  |================ Secure Encrypted Channel ======|

```

1. ClientHello（包含密钥协商参数）

   - 客户端生成一个 **Ephemeral Key（临时公钥）**

   - 使用 **椭圆曲线 Diffie–Hellman（ECDHE）** 算法

   - 发送自己的 **密钥共享参数（key_share）** 给服务器

   - 并告知支持的 **cipher suites、TLS 版本、支持的签名算法等**

​	📌 **这里尚未进行身份认证**，只是告诉服务器准备好协商密钥了。

2. ServerHello（密钥协商确认）

   - 服务器同样生成一个 ephemeral key

   - 回复自己的 **key_share**，用于完成 Diffie–Hellman 协商

   - 客户端和服务器此时可以用对方的 share 值与自己的私钥，完成计算出 **共享的 Pre-Master Secret**

​	💡 **这一步完成后，通信双方就有了相同的对称密钥**，但还没信任身份。

3. Certificate + Signature（身份认证）

   - 服务器发送它的 **X.509 证书**
   - 包含：
     - 服务器的 **RSA / ECDSA 公钥**
     - 被 **根 CA 用其私钥数字签名**
   - 同时附带 **签名(Signature)**
     - 签的是本次握手中的关键信息（包括之前协商的 ephemeral 参数）
     - 签名用的是 **服务器私钥**

   🧠 客户端执行三步认证流程：

   1. 用 **根 CA 公钥** 验证服务器证书是否合法
   2. 验证证书中的服务器身份信息是否与访问地址匹配
   3. 用服务器证书中的公钥，验证服务器发送的签名是否匹配内容

   ✅ 验证成功后，客户端确认服务器确实是“它声称的那个身份”。

4. Server Finished

   - 服务器用协商好的对称密钥（ephemeral key）发送一条加密的消息（包含 handshake transcript 的 HMAC 摘要）
   - 客户端解密并验证它与自己记录的 transcript 是否一致，确认协商内容未被篡改

5. Client Finished

   - 客户端也发送一条使用相同 key 加密的 MAC
   - 服务器验证后，完成双向确认

   ✅ 从这一刻起，**加密信道正式建立完成**

技术要点对照总结

| 功能             | 使用算法                         | 在哪一阶段                     |
| ---------------- | -------------------------------- | ------------------------------ |
| 密钥协商         | Ephemeral ECDHE                  | ClientHello & ServerHello      |
| 身份认证         | 证书 + RSA/ECDSA 签名验证        | Server Certificate & Signature |
| 建立对称密钥     | 基于双方 share 计算出 Pre-Master | After ServerHello              |
| 数据完整性验证   | MAC（HMAC + transcript hash）    | Finished                       |
| 双向加密通道建立 | 对称加密（如 AES-GCM）           | After Finished                 |

##### 为什么 TLS 1.3 更安全？

- 强制使用 Ephemeral DH（前向保密，避免历史数据泄露）
- 不支持不安全的 RSA 密钥交换（TLS 1.2 中支持）
- 只用一次 round-trip 握手即可建立安全通信通道（更快）
- 所有握手内容都加密，防止 metadata 泄露

##### 安全配置要求 & 常见漏洞提醒（CISSP 考点）

推荐设置：

- 最低支持：TLS 1.2（最佳为 1.3）
- 禁用：SSL、TLS 1.0、TLS 1.1
- 强制使用 SHA-2 或 SHA-3（禁止 MD5、SHA-1）
- 使用 GCM 模式代替 CBC（防止 Padding Oracle 攻击）

❌ 禁用弱算法：

| 弃用项      | 原因                       |
| ----------- | -------------------------- |
| SSL/SSL 3.0 | 已被严重漏洞利用（POODLE） |
| RC4         | 存在密钥泄露攻击           |
| MD5/SHA-1   | 容易发生 hash 碰撞         |
| 3DES        | 密钥长度短，易被暴力破解   |

**实际应用场景（HTTPS 实战）**

🔐 TLS 与 HTTPS 结合：

- 网站申请 TLS 证书（即 HTTPS 证书）
- 用户访问网站，浏览器进行 TLS 握手
- 若网站证书有效，浏览器显示 🔒 小锁图标
- 整个通信过程被加密，防止中间人窃听和篡改

📌 例子：

https://bank.example.com

浏览器通过 TLS 连接加密通信：

- 验证证书是否由受信 CA 签发
- 使用服务器公钥协商对称密钥
- 使用对称加密传输登录凭证、交易数据等

##### CISSP 考试记忆要点（Checklist）

- **TLS 使用对称加密传输数据，但对称密钥通过非对称方式协商交换**
- **SSL 已过时，不再安全**
- **TLS 通常用于 HTTPS，依赖服务器的 X.509 数字证书**
- **TLS handshake 的核心目标是协商一个共享对称密钥**
- **POODLE 漏洞考点**：暴露了 SSL fallback 的风险 → 强化 TLS-only 策略

| 项目              | 要掌握的知识点                                             |
| ----------------- | ---------------------------------------------------------- |
| TLS vs SSL        | SSL 已淘汰，必须使用 TLS 1.2 或更高版本                    |
| TLS 工作流程      | 握手阶段使用非对称加密建立会话密钥，之后对称加密传输数据   |
| Cipher Suite 结构 | 4 个组件必须掌握：Key Exchange, Authentication, Bulk, Hash |
| 安全算法推荐      | AES-GCM + SHA-2/SHA-3 + ECDHE 是现代最佳实践               |
| 协议弱点识别      | 知道 RC4、3DES、MD5、SHA-1 等被禁用原因                    |
| 常见漏洞          | POODLE、Downgrade 攻击、Padding Oracle                     |

#### Tor and the Dark Web - Tor 和暗网（Dark Web）

**Tor**（The Onion Router）是一种通过分布式网络 **实现匿名通信** 的协议和网络系统。

Tor, formerly known as The Onion Router, provides a mechanism for anonymously routing traffic across the internet using encryption and a set of relay nodes. 

主要机制：

- **多层加密**（Onion Routing）：就像洋葱一样，数据包在每一跳都被解密一层，逐层剥离，直到最终目的地。
- **三层节点结构**：
  - **入口节点（Guard/Entry Node）**
  - **中继节点（Relay Node）**
  - **出口节点（Exit Node）**

每个节点只能看到：

- 它之前的节点是谁（来源）
- 它要发送给谁（下一个目的地）
- **看不到完整的路径或内容**

##### Perfect Forward Secrecy（完全前向保密）

It relies on a technology known as perfect forward secrecy, where layers of encryption prevent nodes in the relay chain from reading anything other than the specific information they need to accept and forward the traffic. 

By using perfect forward secrecy in combination with a set of three or more relay nodes, Tor allows for both anonymous browsing of the standard internet, as well as the hosting of completely anonymous sites on the dark web.

**完美前向保密**确保即使某个密钥将来泄露，也无法解密过去的通信内容。

Tor 中的应用：

- 会话密钥是临时生成的（基于 Diffie-Hellman 等算法）
- 每条路径的加密密钥都是一次性的、不可复用
- 保护历史通信不被后续密钥泄露影响

##### Dark Web 是什么？

- 指那些通过标准浏览器无法访问的网站
- 必须使用如 **Tor 浏览器** 这样的特殊客户端访问
- 域名通常以 `.onion` 结尾
- 可以托管 **匿名站点（hidden services）**

❗️风险与用途并存：

- **合法用途**：新闻自由、隐私保护、人权工作
- **非法用途**：毒品、黑市、数据贩卖、恶意服务等

##### CISSP 考试相关考点

**“三跳加密，层层剥离，前向保密，匿名可依。”**
解释：Tor 路径三跳，每跳一层加密，历史通信不可追溯，保障匿名性。

| 考点主题                | 内容说明                                              |
| ----------------------- | ----------------------------------------------------- |
| **匿名性技术**          | Tor 是典型案例之一，考察匿名通信与 Onion Routing 原理 |
| **加密通信机制**        | 多层加密、对称与非对称结合，利用前向保密技术          |
| **隐私保护 vs 滥用**    | 考查对暗网合法用途与滥用风险的理解与平衡              |
| **前向保密机制（PFS）** | 与 TLS 结合考察，确认是否了解临时密钥生成及其意义     |

### 4. Steganography and Watermarking

#### 1. **Steganography** （隐写术）

隐写术是一种通过将信息嵌入其他“看似无害”的文件中来隐藏通信内容的**加密掩蔽技术**，让秘密消息看起来像普通文件，从而逃避侦测。

##### 实现方式

- **图像嵌入**（最常见）：
  - 利用图像中每个像素的 **Least Significant Bit（LSB）最不重要位**进行信息替换
  - 对人眼几乎无影响，如将 RGB 值 `Blue: 64` 改成 `65` 看不出差异
- **音频 / 视频**：改变音频波形的低位数据或帧间延迟等不可察觉部分
- **文本隐写（Concealment cipher）**：
  - 通过语法变化、空格、拼写差异、隐藏格式等手法在文本中嵌入信息
  - 示例：特定行首字母拼出一句话

##### 应用场景

| 场景       | 说明                                                     |
| ---------- | -------------------------------------------------------- |
| ✏️ 合法用途 | 嵌入数字水印以识别和保护文档版权；军事通信中传递机密数据 |
| ❌ 非法用途 | 网络犯罪（如恐怖主义、儿童色情、间谍活动）中的隐藏通信   |

Steganography is the art of using cryptographic techniques to embed secret messages within another message. Steganographic algorithms work by making alterations to the least significant bits of the many bits that make up image files. The changes are so minor that there is no appreciable effect on the viewed image. This technique allows communicating parties to conceal messages in plain sight—for example, they might embed a secret message within an illustration on an otherwise innocent web page.

It is also possible to embed messages inside larger excerpts of text. This approach is known as a concealment cipher.

Steganographers often embed their secret messages within images or WAV files because these files are often so large that the secret message would easily be missed by even the most observant inspector. Steganography techniques are often used for illegal activities, such as espionage and child pornography.

Steganography can also be used for legitimate purposes, however. Adding digital watermarks to documents to protect intellectual property is accomplished by means of steganography. The hidden information is known only to the file’s creator. If someone later creates an unauthorized copy of the content, the watermark can be used to detect the copy and (if uniquely watermarked files are provided to each original recipient) trace the offending copy back to the source.

Steganography commonly works by modifying the least significant bit (LSB) of a pixel value. For example, each pixel might be described by using three decimal numbers ranging from 0 to 255. One represents the degree of red color in the image, the second represents blue, and the third represents green. If a pixel has a blue value of 64, changing that value to 65 would result in an imperceptible change but does allow the encoding of a bit of steganographic data.

#### 2. Watermarking（水印技术）

**数字水印**是一种将拥有者信息或跟踪信息嵌入内容（如图像、音频、视频）的方法，目的在于标记版权、认证内容或追踪泄露源头。

特点

- 与隐写术不同的是**水印信息是已知或可被发现的**（虽然仍隐含在内容中）
- **防篡改目的**而不是隐藏目的
- 可用于**版权保护、媒体内容验证、防止伪造**

技术机制

- 常用隐写术（如 LSB）来植入水印
- 某些方案对每个用户发放独特水印副本，若泄露可**溯源**

#### Steganography vs. Cryptography vs. Watermarking

| 特性 / 技术 | Steganography（隐写术） | Cryptography（加密术）   | Watermarking（水印）   |
| ----------- | ----------------------- | ------------------------ | ---------------------- |
| 目的        | **隐藏通信的存在**      | **保护通信内容不被泄露** | **标识/验证内容来源**  |
| 内容可见性  | 不可察觉（隐于载体中）  | 可察觉（加密后明显变形） | 通常不影响可视内容     |
| 可追溯性    | 否                      | 否                       | 是（可用唯一水印追踪） |
| 易被检测性  | 低                      | 高                       | 低                     |

**CISSP 应试提示**

- ✅ 理解 **LSB 技术** 是隐写的常见手段
- ✅ 明确 **隐写术是隐藏存在**，而不是加密内容
- ✅ 数字水印更多用于**版权保护和内容追踪**
- ✅ 考题可能会考查：
  - 哪种方法最适合隐藏通信本身？
  - 哪种技术可以识别数据所有者？
  - 哪种方法会使用 LSB 嵌入技术？

### 5. Networking

#### Circuit Encryption

Security administrators use two types of encryption techniques to protect data traveling over networks.

"链路加密加密一切，慢但全面；端到端加密数据，快但留痕。"

##### 1. ***Link encryption*** （链路加密）

适用于**整条链路的数据保护**，包括路由信息，适合防止链路窃听，但每跳都需解密再加密 → 开销大。

It protects entire communications circuits by creating a secure tunnel between two points using either a hardware solution or a software solution that encrypts all traffic entering one end of the tunnel and decrypts all traffic entering the other end of the tunnel. For example, a company with two offices connected via a data circuit might use link encryption to protect against attackers monitoring at a point in between the two offices.

##### ***2. End-to-end encryption***（端到端加密）

加密**通信两端之间的实际内容**，路径中节点无法解密内容，但元信息（如地址）仍可被观察。

It protects communications between two parties (for example, a client and a server) and is performed independently of link encryption. An example of end-to-end encryption would be the use of TLS to protect communications between a user and a web server. This protects against an intruder who might be monitoring traffic on the secure side of an encrypted link or traffic sent over an unencrypted link.

##### **CISSP 常考点**

链路加密 vs. 端到端加密的加密内容对比

应用层 vs. 物理层

效率与安全性的权衡

##### Link Encryption vs. End-to-End Encryption

| 特征        | Link Encryption（链路加密）                  | End-to-End Encryption（端到端加密）               |
| ----------- | -------------------------------------------- | ------------------------------------------------- |
| 📍 加密位置  | 通信链路的每一跳（物理连接点之间）           | 通信的起点到终点（通常是应用层通信的两端）        |
| 📦 加密内容  | **包括报文头、地址、路由信息、数据**全部内容 | **只加密数据内容**（Header/Address 不加密）       |
| 🔁 解密频率  | 每跳都需解密 → 读取目的地址 → 再重新加密     | **仅起点加密，终点解密**                          |
| 🔓 路由效率  | 路由较慢（每跳需解密再加密）                 | 路由较快（头部不加密，路由器可直接处理）          |
| 🕵️‍♂️ 安全风险 | 防止**链路监听**攻击                         | 防止**内容泄露/篡改**（但路径上 Metadata 仍暴露） |
| ⬇ OSI 层    | 实现于 OSI 模型的**较低层**（如数据链路层）  | 实现于 OSI 模型的**较高层**（如会话层、应用层）   |
| 🧪 示例      | VPN、MPLS、Frame Relay、物理电路层加密       | TLS/SSL、PGP、S/MIME、SSH、IPSec End-to-End 模式  |

The critical difference between link and end-to-end encryption is that in link encryption, all the data, including the header, trailer, address, and routing data, is also encrypted. Therefore, each packet has to be decrypted at each hop so that it can be properly routed to the next hop and then reencrypted before it can be sent along its way, which slows the routing. End-to-end encryption does not encrypt the header, trailer, address, and routing data, so it moves faster from point to point but is more susceptible to sniffers and eavesdroppers.

When encryption happens at the higher OSI layers, it is usually end-to-end encryption, and if encryption is done at the lower layers of the OSI model, it is usually link encryption.

##### Secure Shell (SSH) - 端到端加密

**SSH = 端到端加密的代表性技术**

- **作用**：替代 Telnet、FTP、rlogin 等不安全协议，实现**加密的远程通信**
- **版本区别**：
  - **SSH1**（已废弃）：支持 DES、3DES、IDEA、Blowfish
  - **SSH2**（安全标准）：支持 Diffie–Hellman 密钥交换，增强多会话支持
    - 增强安全性，防止 Man-in-the-Middle、嗅探、IP/DNS 欺骗等攻击

It is a good example of an end-to-end encryption technique. This suite of programs provides encrypted alternatives to common internet applications such as the File Transfer Protocol (FTP), Telnet, and rlogin. There are actually two versions of SSH. SSH1 (which is now considered insecure) supports the Data Encryption Standard (DES), Triple DES (3DES), International Data Encryption Algorithm (IDEA), and Blowfish algorithms. SSH2 drops support for DES and IDEA but adds several security enhancements, including support for the Diffie–Hellman key exchange protocol and the ability to run multiple sessions over a single SSH connection. SSH2 provides added protection against man-in-themiddle (on-path) attacks, eavesdropping, and IP/DNS spoofing.

**CISSP考试注意点**

- SSH 属于 **端到端加密**
- SSH2 优于 SSH1，使用更强的加密机制并支持多会话
- SSH 常与远程登录、文件传输（SFTP、SCP）绑定考察

**相关补充：结合 OSI 模型理解**

| OSI 层                        | 加密实现方式                     | 类型                  |
| ----------------------------- | -------------------------------- | --------------------- |
| 第1–2层（物理 / 数据链路）    | VPN、链路层加密、Frame Relay     | Link Encryption       |
| 第5–7层（会话 / 表示 / 应用） | TLS、PGP、S/MIME、SSH、IPSec E2E | End-to-End Encryption |

#### IPsec（Internet Protocol Security）

**IPsec** 是由 IETF 定义的一套完整的协议架构，**用于在 IP 层实现安全通信**。它可以：

- 提供机密性（Confidentiality）
- 完整性（Integrity）
- 认证（Authentication）
- 防重放攻击（Anti-Replay）

**使用场景：** VPN、加密隧道、主机到主机加密、远程接入等。

Various security architectures are in use today, each one designed to address security issues in different environments. One such architecture that supports secure communications is the Internet Protocol security (IPsec) standard. IPsec is a standard architecture set forth by the Internet Engineering Task Force (IETF) for setting up a secure channel to exchange information between two entities.

IPsec 的核心组成

The IP security (IPsec) protocol provides a complete infrastructure for secured network communications. IPsec has gained widespread acceptance and is now offered in a number of commercial operating systems out of the box. IPsec relies on security associations, and there are two main components:

IPsec 的安全性建立在两个核心协议组件上：

1. **Authentication Header（AH）**

   1. It assurances of message integrity and nonrepudiation. AH also provides authentication and access control and prevents replay attacks.

      | 特性           | 描述                                                      |
      | -------------- | --------------------------------------------------------- |
      | ✅ **提供**     | 完整性、认证、访问控制、防重放                            |
      | ❌ **不提供**   | 机密性（不加密数据）                                      |
      | 📦 **保护范围** | IP 头 + 数据内容（除 IP 中某些字段）                      |
      | 📌 用法         | AH 适用于需要强认证、不加密内容的场景（如完整性保护日志） |

2. **Encapsulating Security Payload（ESP）**

   1. It provides confidentiality and integrity of packet contents. It provides encryption and limited authentication and prevents replay attacks.

      | 特性           | 描述                                                     |
      | -------------- | -------------------------------------------------------- |
      | ✅ **提供**     | 加密（Confidentiality）、完整性、有限认证、防重放        |
      | ❌ **不强制**   | 完整 IP 头认证                                           |
      | 📦 **保护范围** | 仅加密 IP payload，IP 头通常不加密（除非用 tunnel mode） |
      | 📌 用法         | ESP 是实际通信中最常用的组件（VPN、加密通道）            |

      💡 **ESP 常独立使用**，而 **AH 很少单独使用**。当 AH 和 ESP 配合使用时，可以分别提供认证和机密性。

ESP also provides some limited authentication, but not to the degree of the AH. Though ESP is sometimes used without AH, it’s rare to see AH used without ESP.

IPsec provides for two discrete modes of operation. When IPsec is used in transport mode for end-to-end encryption, only the packet payload is encrypted. This mode is designed for peer-to-peer communication. When it’s used in tunnel mode, the entire packet, including the header, is encrypted. This mode is designed for link encryption.

##### 两种工作模式：Tunnel 与 Transport

| 模式类型     | Transport Mode            | Tunnel Mode               |
| ------------ | ------------------------- | ------------------------- |
| 🔄 加密内容   | 仅数据部分（Payload）     | 包括整个 IP 包（头+数据） |
| 🧑‍🤝‍🧑 应用场景 | 主机对主机（end-to-end）  | 网关对网关、远程接入 VPN  |
| 📌 安全层级   | 较低（传输中仍可识别 IP） | 更高（隐藏通信地址信息）  |

✅ **Tunnel Mode** 常用于 VPN 场景，可以隐藏通信的源和目标。

##### Security Association (SA) 安全关联

IPsec 的所有连接都基于 **Security Association (SA)** 建立。

| 特性                | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| 🧭 SA 定义           | 表示单向加密/认证会话的逻辑连接                              |
| 📍 单向              | 一个 SA 只能加密或解密一个方向                               |
| 🔁 双向通信          | 需要两个 SA（发送 + 接收）                                   |
| 🔄 AH + ESP 双栈通信 | 需要 **4 个 SA**（AH 发送/接收 + ESP 发送/接收）             |
| 📘 内容              | 包含使用的协议、加密算法、密钥、SPI（Security Parameters Index）等信息 |

At runtime, you set up an IPsec session by creating a security association (SA). The SA represents the communication session and records any configuration and status information about the connection. The SA represents a simplex connection. If you want a two-way channel, you need two SAs, one for each direction. Also, if you want to support a bidirectional channel using both AH and ESP, you will need to set up four SAs.

Some of IPsec’s greatest strengths come from being able to filter or manage communications on a per-SA basis so that clients or gateways between which security associations exist can be rigorously managed in terms of what kinds of protocols or services can use an IPsec connection. Also, without a valid security association defined, pairs of users or gateways cannot establish IPsec links.

##### IPsec 的优势与安全特性

| 能力             | 实现机制                         |
| ---------------- | -------------------------------- |
| 身份认证         | AH / ESP（含身份验证字段）       |
| 数据完整性验证   | 哈希（如 HMAC-SHA）              |
| 加密数据机密性   | 对称加密算法（如 AES）           |
| 防重放攻击       | 包序号 + 滑动窗口技术            |
| 灵活管理通信策略 | 每 SA 可定义允许的协议/服务      |
| 基于策略访问控制 | IPsec 策略控制哪些 IP/端口可通信 |

CISSP 备考建议

| 考点                           | 要求                                  |
| ------------------------------ | ------------------------------------- |
| AH vs. ESP                     | 区别：ESP 提供机密性，AH 不提供       |
| Tunnel Mode vs. Transport Mode | 区别：是否加密 IP 头                  |
| SA 的概念和数量需求            | 理解单向性，AH+ESP 双向通信需 4 个 SA |
| AH/ESP 使用的加密与哈希算法    | AES, HMAC-SHA 等                      |
| IPsec 使用场景和安全优势       | VPN、远程接入、主机间安全通信         |

### 6. Emerging Applications - 新兴加密技术的应用场景

随着信息安全需求日益多元化，传统加密技术正在被拓展到许多**新兴场景**中。这些场景强调：

- **去中心化**（如区块链）
- **资源受限设备上的加密**（如轻量级加密）
- **隐私保护同时仍可计算**（同态加密）

Cryptography plays a central role in many emerging areas of cybersecurity and technology. Let’s take a look at a few of these concepts: the blockchain, lightweight cryptography, and homomorphic encryption.

#### 1. Blockchain（区块链）

✅ 核心特性

- **分布式（Distributed）**：所有节点维护相同的账本副本，无需中心化管理。
- **不可篡改（Immutable）**：通过哈希链与共识机制，确保数据无法被修改。
- **公开透明（Transparent）**：所有交易可被所有节点验证。

🔒 加密技术在其中的作用

- **Hash 函数**：用于链上区块的内容摘要和链接前后区块。
- **数字签名**：确保交易的合法性和不可否认性。
- **非对称加密**：保护用户身份和交易私钥。

📌 应用举例

| 应用领域     | 描述                                  |
| ------------ | ------------------------------------- |
| 加密货币     | 如 Bitcoin, Ethereum 等，无需银行中心 |
| 不动产登记   | 防止产权纠纷，数据无法被更改或销毁    |
| 供应链溯源   | 可验证商品来源和运输路径              |
| 数字身份管理 | 利用区块链记录和验证用户身份          |

The blockchain is, in its simplest description, a distributed and immutable public ledger. This means that it can store records in a way that distributes those records among many different systems located around the world and do so in manner that prevents anyone from tampering with those records. The blockchain creates a data store that nobody can tamper with or destroy.

The first major application of the blockchain is cryptocurrency. The blockchain was originally invented as a foundational technology for Bitcoin, allowing the tracking of Bitcoin transactions without the use of a centralized authority. In this manner, the blockchain allows the existence of a currency that has no central regulator. Authority for Bitcoin transactions is distributed among all participants in the Bitcoin blockchain.

Although cryptocurrency is the blockchain application that has received the most attention, there are many other uses for a distributed immutable ledger—so much so that new applications of blockchain technology seem to be appearing every day. For example, property ownership records could benefit tremendously from a blockchain application. This approach would place those records in a transparent, public repository that is protected against intentional or accidental damage. Blockchain technology might also be used to track supply chains, providing consumers with confidence that their produce came from reputable sources and allowing regulators to easily track down the origin of recalled produce.

#### 2. Lightweight Cryptography（轻量级加密）

✅ 核心诉求

- **低功耗**
- **低延迟**
- **资源受限设备兼容性**

📌 应用环境

| 场景               | 特点                               |
| ------------------ | ---------------------------------- |
| 物联网设备（IoT）  | 微控制器、嵌入式芯片，资源极其有限 |
| 智能卡 / RFID      | 被动供电，需极省电能完成加密       |
| 卫星、远程传感器等 | 运行周期长、功耗极低的硬件环境     |
| 高速网络通信       | 对延迟敏感，需快速完成加解密       |

🔧 实现方式：

- 专用加密芯片或模块（如硬件 VPN 加速器）
- 精简版本的对称算法（如轻量化 AES、PRESENT、Speck）

🧠 CISSP 注意点：

- 轻量加密不是功能弱化，而是性能优化。
- 多用于边缘设备而非数据中心。

There are many specialized use cases for cryptography that you may encounter during your career where computing power and energy might be limited.

Some devices operate at extremely low power levels and put a premium on conserving energy. For example, imagine sending a satellite into space with a limited power source. Thousands of hours of engineering go into getting as much life as possible out of that power source. Similar cases happen here on Earth, where remote sensors must transmit information using solar power, a small battery, or other equipment.

Smartcards are another example of a low-power environment. They must be able to securely communicate with smartcard readers but only using the energy either stored on the card or transferred to it by a magnetic field.

In these cases, cryptographers often design specialized hardware that is purpose-built to implement lightweight cryptographic algorithms with as little power expenditure as possible. You won’t need to know the details of how these algorithms work, but you should be familiar with the concept that specialized hardware can minimize power consumption.

Another specialized use for cryptography is in cases where you need very low latency. That simply means that the encryption and decryption should not take a long time. Encrypting network links is a common example of low-latency cryptography. The data is moving quickly across a network and the encryption should be done as quickly as possible to avoid becoming a bottleneck.

Specialized encryption hardware also solves many low-latency requirements. For example, a dedicated VPN hardware device may contain cryptographic hardware that implements encryption and decryption operations in highly efficient form to maximize speed.

High resiliency requirements exist when it is extremely important that data be preserved and not accidentally destroyed during an encryption operation. In cases where resiliency is extremely important, the easiest way to address the issue is for the sender of data to retain a copy until the recipient confirms the successful receipt and decryption of the data.

#### 3. Homomorphic Encryption（同态加密）

定义：在数据加密状态下仍可执行计算，且解密后结果与明文计算结果一致。

应用价值

| 应用场景                | 优势                                     |
| ----------------------- | ---------------------------------------- |
| 云计算中的隐私保护      | 用户可将加密数据上传云端，云端可直接计算 |
| 医疗/金融数据分析       | 企业在不解密用户数据的情况下完成分析     |
| 多方计算（MPC）         | 各方数据保密，结果可共享                 |
| 隐私保护 AI/ML 模型训练 | 模型训练过程中不泄露数据内容             |

类型

- **部分同态（PHE）**：支持加法或乘法（但不是两者）。
- **完全同态（FHE）**：支持任意计算操作，计算能力最强但最慢。

🧠 CISSP 注意点

- 实现复杂、计算资源消耗大，但属于未来加密方向。
- 不要求理解其数学原理，但需理解其适用场景。

Privacy concerns also introduce some specialized use cases for encryption. In particular, we sometimes have applications where we want to protect the privacy of individuals but still want to perform calculations on their data. Homomorphic encryption technology allows this, encrypting data in a way that preserves the ability to perform computation on that data. When you encrypt data with a homomorphic algorithm and then perform computation on that data, you get a result that, when decrypted, matches the result you would have received if you had performed the computation on the plaintext data in the first place.

#### 总结对比表

| 技术               | 目标                         | 应用场景                             | 是否强调加密运算效率 |
| ------------------ | ---------------------------- | ------------------------------------ | -------------------- |
| Blockchain         | 数据不可篡改，去中心信任机制 | 加密货币、供应链、不动产、身份管理   | ❌（关注分布式账本）  |
| Lightweight Crypto | 节能、低功耗、低延迟         | IoT、智能卡、卫星、实时网络通信      | ✅（强调效率）        |
| Homomorphic Crypto | 隐私保护同时支持加密态计算   | 云数据分析、医疗金融隐私计算、AI训练 | ❌（计算量大）        |

## Cryptographic Attacks

As with any security mechanism, malicious individuals have found a number of attacks to defeat cryptosystems. It’s important that you understand the threats posed by various cryptographic attacks to minimize the risks posed to your systems.

| 类型             | 代表攻击方式                                      | 主要目标                     | 示例 / 工具               |
| ---------------- | ------------------------------------------------- | ---------------------------- | ------------------------- |
| **算法弱点**     | Analytic, Statistical                             | 破解算法设计本身             | 使用数学模型分析结构      |
| **实现缺陷**     | Implementation                                    | 软件实现失误                 | 编码错误、缓冲区溢出      |
| **物理特征泄露** | Side-Channel, Timing, Fault Injection             | 利用加密操作中产生的物理信息 | 电磁波、功耗、时间分析    |
| **暴力尝试**     | Brute-force, Rainbow Tables, Known/Chosen Attacks | 尝试所有组合或构造攻击样本   | hashcat、John the Ripper  |
| **协议缺陷**     | Man-in-the-Middle, Replay, Birthday               | 利用协议设计弱点             | TLS downgrade、token 重放 |
| **双重加密弱点** | Meet-in-the-Middle                                | 针对双层加密                 | 攻击 2DES                 |
| **口令猜测相关** | Dictionary, Salting 相关                          | 破解用户密码                 | 使用预构造字典表          |

#### **Analytic Attack** 

- **目标**：从算法数学结构入手，降低破解复杂度

- **防御**：选择公开评估、被社区验证的加密算法（如 AES）

This is an algebraic manipulation that attempts to reduce the complexity of the algorithm. Analytic attacks focus on the logic of the algorithm itself.

#### **Implementation Attack** 

- **目标**：利用软件或硬件实现上的编码漏洞或逻辑错误
- **典型问题**：未正确实现 padding、密钥存储不安全
- **防御**：代码审计、安全编码标准、FIPS 140-2 认证模块

This is a type of attack that exploits weaknesses in the implementation of a cryptography system. It focuses on exploiting the software code, not just errors and flaws but the methodology employed to program the encryption system.

#### **Statistical Attack** 

- **目标**：利用非随机行为，如伪随机数可预测性或浮点误差
- **防御**：使用 CSPRNG（Cryptographically Secure Pseudo-Random Number Generator）

A statistical attack exploits statistical weaknesses in a cryptosystem, such as floating-point errors and inability to produce truly random numbers. Statistical attacks attempt to find a vulnerability in the hardware or operating system hosting the cryptography application.

#### **Brute-Force Attack** 

- **目标**：穷举所有可能的密钥或密码组合

- **增强方式**：

  - **Rainbow Tables**：预计算常用密码的 hash 值
  - **高性能硬件**：GPU、FPGA 或 ASIC 加速攻击

  **防御**：

  - 增加密钥长度（位数每增加 1，破解时间翻倍）
  - 使用 salt 和 **key stretching**（如 bcrypt、PBKDF2）

Brute-force attacks are quite straightforward. Such an attack attempts every possible valid combination for a key or password. They involve using massive amounts of processing power to methodically guess the key used to secure cryptographic communications.

#### **Fault Injection Attack** 

- **目标**：通过物理破坏（电压、温度）制造设备异常行为
- **防御**：使用抗故障硬件、电压/温度检测机制

In these attacks, the attacker attempts to compromise the integrity of a cryptographic device by causing some type of external fault. For example, they might use high-voltage electricity, high or low temperature, or other factors to cause a malfunction that undermines the security of the device.

#### **Side-Channel Attack** 

- **目标**：监听设备行为，如功耗、电磁波、运行时间

- **包括**：

  - **Timing Attack**（测时攻击）：通过操作时间分析密钥

  **防御**：

  - 执行时间统一的算法（constant time implementation）
  - 电磁隔离、屏蔽罩

Computer systems generate characteristic footprints of activity, such as changes in processor utilization, power consumption, or electromagnetic radiation. Side-channel attacks seek to use this information to monitor system activity and retrieve information that is actively being encrypted.

#### **Timing Attack** 

Timing attacks are an example of a side-channel attack where the attacker measures precisely how long cryptographic operations take to complete, gaining information about the cryptographic process that may be used to undermine its security.

#### **Frequency Analysis / Ciphertext-Only Attack** 

- **目标**：仅凭密文，通过字母频率反推原文或算法类型
- **适用情境**：古典加密如凯撒密码、维吉尼亚密码
- **防御**：使用强对称加密（AES）与多样性输入掩盖频率特征

In many cases, the only information you have at your disposal is the encrypted ciphertext message, a scenario known as the ciphertext-only attack. In this case, one technique that proves helpful against simple ciphers is frequency analysis—counting the number of times each letter appears in the ciphertext. Using your knowledge that the letters E, T, A, O, I, N are the most common in the English language, you can then test several hypotheses:

1. If these letters are also the most common in the ciphertext, the cipher was likely a transposition cipher, which rearranged the characters of the plaintext without altering them.
2. If other letters are the most common in the ciphertext, the cipher is probably some form of substitution cipher that replaced the plaintext characters.

This is a simple overview of frequency analysis, and many sophisticated variations on this technique can be used against polyalphabetic ciphers and other sophisticated cryptosystems.

For a nonflawed protocol, the average amount of time required to discover the key through a brute-force attack is directly proportional to the length of the key. A bruteforce attack will always be successful given enough time. Every additional bit of key length doubles the time to perform a brute-force attack because the number of potential keys doubles.

There are two modifications that attackers can make to enhance the effectiveness of a brute-force attack:

- Rainbow tables provide precomputed values for cryptographic hashes. These are commonly used for cracking passwords stored on a system in hashed form.
- Specialized, scalable computing hardware designed specifically for the conduct of brute-force attacks may greatly increase the efficiency of this approach.

**Known / Chosen Plaintext / Chosen Ciphertext**

- **Known Plaintext**：知道部分明文-密文对

- **Chosen Plaintext**：控制明文输入，观察密文输出

- **Chosen Ciphertext**：控制密文输入，观察解密输出
- **典型攻击**：差分密码分析、侧信道 + chosen-ciphertext 联动
- **防御**：避免泄露解密接口、启用随机初始化向量（IV）

#### **Known Plaintext** 

In the known plaintext attack, the attacker has a copy of the encrypted message along with the plaintext message used to generate the ciphertext (the copy). This knowledge greatly assists the attacker in breaking weaker codes. For example, imagine the ease with which you could break the Caesar cipher described in Chapter 6 if you had both a plaintext copy and a ciphertext copy of the same message.

#### Chosen Plaintext 

In this attack, the attacker obtains the ciphertexts corresponding to a set of plaintexts of their own choosing. This allows the attacker to attempt to derive the key used and thus decrypt other messages encrypted with that key. This can be difficult, but it is not impossible. Advanced methods such as differential cryptanalysis are types of chosen plaintext attacks.

#### Chosen Ciphertext 

In a chosen ciphertext attack, the attacker has the ability to decrypt chosen portions of the ciphertext message and use the decrypted portion of the message to discover the key.

#### Meet in the Middle 

- **目标**：针对双重加密（如 2DES）找出两个密钥组合
- **过程**：从两头同时尝试匹配中间结果
- **防御**：使用三重加密（3DES 或 AES）

Attackers might use a meet-in-the-middle attack to defeat encryption algorithms that use two rounds of encryption. This attack is the reason that Double DES (2DES) was quickly discarded as a viable enhancement to the DES encryption (it was replaced by Triple DES, or 3DES).

In the meet-in-the-middle attack, the attacker uses a known plaintext message. The plaintext is then encrypted using every possible key (k1), and the equivalent ciphertext is decrypted using all possible keys (k2). When a match is found, the corresponding pair (k1, k2) represents both portions of the double encryption. This type of attack generally takes only double the time necessary to break a single round of encryption (or 2 n rather than the anticipated 2 n * 2n ), offering minimal added protection.

#### Man in the Middle 

- **目标**：中间人劫持双向加密通信，解密并转发
- **防御**：
  - 服务器使用**数字证书（PKI）验证**
  - 协议使用 **mutual TLS、HSTS、certificate pinning**

In the man-in-the-middle attack, a malicious individual sits between two communicating parties and intercepts all communications (including the setup of the cryptographic session). The attacker responds to the originator’s initialization requests and sets up a secure session with the originator. The attacker then establishes a second secure session with the intended recipient using a different key and posing as the originator. The attacker can then “sit in the middle” of the communication and read all traffic as it passes between the two parties. Some cybersecurity professionals are beginning to refer to these attacks as “on-path attacks” to avoid a gender-specific reference.

#### Birthday Attack

- **目标**：通过碰撞概率找到两个内容生成相同哈希值（对抗数字签名）
- **防御**：使用大哈希位数（如 SHA-256、SHA-3）

The birthday attack, also known as a collision attack or reverse hash matching (see the discussion of brute-force and dictionary attacks in Chapter 14, “Controlling and Monitoring Access”), seeks to find flaws in the one-to-one nature of hashing functions. In this attack, the malicious individual seeks to substitute in a digitally signed communication a different message that produces the same message digest, thereby maintaining the validity of the original digital signature.

#### Replay Attack

- **目标**：截获原始加密消息后重新发送

- **防御**：

  - 使用 **timestamp、nonce、session ID**

  - 启用 **challenge-response 协议**

The replay attack is used against cryptographic algorithms that don’t incorporate temporal protections. In this attack, the malicious individual intercepts an encrypted message between two parties (often a request for authentication) and then later “replays” the captured message to open a new session. This attack can be defeated by incorporating a timestamp and expiration period into each message, using a challenge-response mechanism, and encrypting authentication sessions with ephemeral session keys.

### Salting & Key Stretching（抗字典攻击）

| 技术               | 描述                                    | 目的                       |
| ------------------ | --------------------------------------- | -------------------------- |
| **Salt**           | 随机数据与密码拼接后再哈希              | 抵抗 rainbow tables        |
| **Key Stretching** | 多次迭代哈希加密函数，如 bcrypt、scrypt | 增加计算成本，减缓爆破速度 |

Salt might be hazardous to your health, but it can save your password! To help combat the use of brute-force attacks, including those aided by dictionaries and rainbow tables, cryptographers make use of a technology known as cryptographic salt.

The cryptographic salt is a random value that is added to the end of the password before the operating system hashes the password. The salt is then stored in the password file along with the hash. When the operating system wishes to compare a user’s proffered password to the password file, it first retrieves the salt and appends it to the password. It feeds the concatenated value to the hash function and compares the resulting hash with the one stored in the password file.

Specialized password hashing functions, such as PBKDF2, bcrypt, and scrypt, allow for the creation of hashes using salts and also incorporate a technique known as key stretching that makes it more computationally difficult to perform a single password guess.

The use of **salting**, especially when combined with **key stretching**, dramatically increases the difficulty of brute-force attacks. Anyone attempting to build a rainbow table must build a separate table for each possible value of the cryptographic salt.

##### CISSP 考点强化

- 熟知所有攻击的原理及其防御策略，特别是常考组合：
  - **Brute-force vs Rainbow Table vs Dictionary Attack**
  - **Known Plaintext vs Chosen Plaintext vs Chosen Ciphertext**
  - **Side-channel vs Timing vs Fault Injection**
  - **Meet-in-the-middle 专攻双重加密（2DES）**
- 牢记：**密钥位数越长，抵抗暴力破解越强。**
- **防御设计重点**：引入 **时间元素、随机性、密钥复杂性** 以及 **攻击表面最小化**。

## Summary

Asymmetric key cryptography, or public key encryption, provides an extremely flexible infrastructure, facilitating simple, secure communication between parties that do not necessarily know each other prior to initiating the communication. It also provides the framework for the digital signing of messages to ensure nonrepudiation and message integrity.

This chapter explored public key encryption, which provides a scalable cryptographic architecture for use by large numbers of users. We also described some popular cryptographic algorithms, and the use of link encryption and end-to-end encryption. We introduced you to the public key infrastructure, which uses certificate authorities (CAs) to generate digital certificates containing the public keys of system users and digital signatures, which rely on a combination of public key cryptography and hashing functions. You also learned how to use the PKI to obtain integrity and nonrepudiation through the use of digital signatures. You learned how to ensure consistent security throughout the cryptographic lifecycle by adopting key management practices and other mechanisms.

We also looked at some of the common applications of cryptographic technology in solving everyday problems. You learned how cryptography can be used to secure email (using PGP and S/MIME), web communications (using TLS), and both peer-to-peer and gatewayto-gateway networking (using IPsec).

Finally, we covered some of the more common attacks used by malicious individuals attempting to interfere with or intercept encrypted communications between two parties. Such attacks include birthday, cryptanalytic, replay, brute-force, known plaintext, chosen plaintext, chosen ciphertext, meet-in-the-middle, man-in-the-middle, and birthday attacks. It’s important for you to understand these attacks in order to provide adequate security against them.

### 1. Asymmetric (Public Key) Cryptography

#### ✅ Key Concepts

- **Uses a key pair**: one public, one private.
- **Scalable**: Suitable for large groups or untrusted environments.
- **Main benefits**:
  - **Confidentiality**: Encrypt with receiver’s public key; decrypt with private key.
  - **Authentication & Nonrepudiation**: Sign with sender’s private key; verify with public key.
  - **Integrity**: Achieved via message digests (hashes).

##### 🔑 Use Cases:

- Secure communication with unknown parties.
- Digital signatures and PKI integration.

------

### 🏗 2. Public Key Infrastructure (PKI)

#### 🏛 Key Components

- **Certificate Authorities (CAs)**: Trusted third parties that issue digital certificates.
- **Digital Certificates (X.509)**: Bind a public key to an identity; signed by CA.
- **Registration Authorities (RAs)**: Verify identities for CAs.
- **Certificate Lifecycle**:
  - **Enrollment → Verification → Revocation**
  - Revocation methods: CRL, OCSP, Certificate Stapling

#### 🔐 Digital Signature Process

1. Hash message to produce digest.
2. Encrypt digest with sender’s private key = digital signature.
3. Receiver decrypts with sender’s public key and recomputes digest to verify.

------

### 📡 3. Encryption Models

#### 🔗 Link Encryption

- Encrypts **entire communication path** (headers included).
- Needs to decrypt/re-encrypt at each hop.
- Example: VPN tunnel endpoints.

#### 🧑‍🤝‍🧑 End-to-End Encryption

- Encrypts **only the payload** from source to destination.
- Faster routing; e.g., TLS, SSH.

------

### ✉️ 4. Secure Applications of Cryptography

#### 📬 Email

- **PGP**: Web-of-trust model; flexible, user-managed.
- **S/MIME**: PKI-based; integrates with enterprise email platforms.

#### 🌐 Web Communication

- **TLS**:
  - Uses public key crypto for key exchange, then symmetric for data.
  - TLS 1.3 removes support for insecure features (e.g., RSA key exchange, SSL fallback).
  - Employs cipher suites specifying key exchange, auth, symmetric encryption, and hashing.

#### 🌍 Networking

- **IPsec**:
  - **AH**: Integrity, authentication.
  - **ESP**: Confidentiality, partial authentication.
  - **Modes**: Tunnel (link-level), Transport (end-to-end)

------

### 🚀 5. Cryptography in Emerging Applications

#### 📒 Blockchain

- Immutable, distributed ledger.
- Used in cryptocurrency, supply chain tracking, notarization.

#### 🧬 Lightweight Cryptography

- Designed for resource-constrained devices (e.g., smartcards, satellites).

#### 🔬 Homomorphic Encryption

- Enables computation on encrypted data without decryption.
- Ideal for privacy-preserving data analysis.

------

### 💥 6. Cryptographic Attacks & Defenses

| Attack Type                                 | Description                                    | Defense                                   |
| ------------------------------------------- | ---------------------------------------------- | ----------------------------------------- |
| **Analytic / Statistical**                  | Exploit flaws in algorithm logic               | Use vetted algorithms (e.g., AES, RSA)    |
| **Implementation**                          | Exploit coding flaws                           | Secure coding, peer reviews               |
| **Side-channel / Timing / Fault Injection** | Observe physical signals (e.g., time, power)   | Shielding, constant-time execution        |
| **Brute-force / Rainbow Table**             | Try every possible key or hash                 | Long keys, salting, key stretching        |
| **Known/Chosen Plaintext or Ciphertext**    | Use known values to reverse-engineer keys      | Randomization, strong IVs                 |
| **Meet-in-the-Middle**                      | Break 2-layer encryption like 2DES             | Use 3DES or AES instead                   |
| **Man-in-the-Middle (MITM)**                | Hijack session setup and impersonate endpoints | TLS, certificate pinning                  |
| **Birthday Attack**                         | Exploit hash collisions                        | Use strong hash algorithms (SHA-2, SHA-3) |
| **Replay**                                  | Resend captured valid message                  | Use timestamps, nonces                    |

------

#### 🧂 Password Security Enhancements

- **Salt**: Random value added to passwords before hashing.
- **Key Stretching**: Iterative hashing (PBKDF2, bcrypt, scrypt).
- **Result**: Defends against dictionary/rainbow attacks.

------

### 🧠 CISSP Focus Tips

- Understand **when to use asymmetric, symmetric, or hybrid encryption**.
- Know **TLS vs IPsec**, **PGP vs S/MIME**, and **AH vs ESP**.
- Memorize **certificate lifecycle** and **trust hierarchy in PKI**.
- Master **attack types**, how they differ, and how to mitigate them.
- Be prepared to map **real-world scenarios to cryptographic solutions** (e.g., signing software, securing emails, encrypted sessions).

## Exam Essentials

- **Understand the key types used in asymmetric cryptography.** Public keys are freely shared among communicating parties, whereas private keys are kept secret. To encrypt a message, use the recipient’s public key. To decrypt a message, use your own private key. To sign a message, use your own private key. To validate a signature, use the sender’s public key.

- **Be familiar with the three major public key cryptosystems.** RSA is the most famous public key cryptosystem; it was developed by Rivest, Shamir, and Adleman in 1977. It depends on the difficulty of factoring the product of prime numbers. ElGamal is an extension of the Diffie–Hellman key exchange algorithm that depends on modular arithmetic. The elliptic curve algorithm depends on the elliptic curve discrete logarithm problem and provides more security than other algorithms when both are used with keys of the same length.

- **Know the fundamental requirements of a hash function.** Good hash functions have five requirements. They must allow input of any length, provide fixed-length output, make it relatively easy to compute the hash function for any input, provide one-way functionality, and be collision-resistant.

- **Be familiar with the major hashing algorithms.** The successors to the Secure Hash Algorithm (SHA), SHA-2 and SHA-3, make up the government standard message digest function. SHA-2 supports variable-length message digests, ranging up to 512 bits. SHA-3 improves upon the security of SHA-2 and supports the same hash lengths.

- **Know how cryptographic salts improve the security of password hashing.** When straightforward hashing is used to store passwords in a password file, attackers may use rainbow tables of precomputed values to identify commonly used passwords. Adding salts to the passwords before hashing them reduces the effectiveness of rainbow table attacks. Common password hashing algorithms that use key stretching to further increase the difficulty of attack include PBKDF2, bcrypt, and scrypt.

- **Understand how digital signatures are generated and verified.** To digitally sign a message, first use a hashing function to generate a message digest; then encrypt the digest with your private key. To verify the digital signature on a message, decrypt the signature with the sender’s public key and then compare the message digest to one you generate yourself. If they match, the message is authentic.

- **Understand the public key infrastructure (PKI).** In the public key infrastructure, certificate authorities (CAs) generate digital certificates containing the public keys of system users. Users then distribute these certificates to people with whom they want to communicate. Certificate recipients verify a certificate using the CA’s public key.

- **Know the common applications of cryptography to secure email.** The emerging standard for encrypted messages is the S/MIME protocol. Another popular email security tool is Phil Zimmerman’s Pretty Good Privacy (PGP). Most users of email encryption rely on having this technology built into their email client or their web-based email service.

- **Know the common applications of cryptography to secure web activity.** The de facto standard for secure web traffic is the use of HTTP over Transport Layer Security (TLS). This approach relies on hybrid cryptography using asymmetric cryptography to exchange an ephemeral session key, which is then used to carry on symmetric cryptography for the remainder of the session.

- **Know the common applications of cryptography to secure networking.** The IPsec protocol standard provides a common framework for encrypting network traffic and is built into a number of common operating systems. In IPsec transport mode, packet contents are encrypted for peer-to-peer communication. In tunnel mode, the entire packet, including header information, is encrypted for gateway-to-gateway communications.

- **Be able to describe IPsec.** IPsec is a security architecture framework that supports secure communication over IP. IPsec establishes a secure channel in either transport mode or tunnel mode. It can be used to establish direct communication between computers or to set up a VPN between networks. IPsec uses two protocols: Authentication Header (AH) and Encapsulating Security Payload (ESP).

- **Be able to explain common cryptographic attacks.** Ciphertext-only attacks require access only to the ciphertext of a message. One example of a ciphertext-only attack is the bruteforce attack, which attempts to randomly find the correct cryptographic key. Frequency analysis, another ciphertext-only attack, counts characters in the ciphertext to reverse substitution ciphers. Known plaintext, chosen ciphertext, and chosen plaintext attacks require the attacker to have some extra information in addition to the ciphertext. The man-in-the-middle attack fools both parties into communicating with the attacker instead of directly with each other. The birthday attack is an attempt to find collisions in hash functions. The replay attack is an attempt to reuse authentication requests.
