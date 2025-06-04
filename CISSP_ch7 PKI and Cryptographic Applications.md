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

##### RSA's Five Basic Requirements（RSA 对加密哈希函数的五大要求）

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

##### Table 7.1 – Hash Algorithm Memorization Chart

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

##### 总结回顾

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

##### Which Key Should I Use?

1. If you want to encrypt a confidential message, use the recipient’s public key.
2. If you want to decrypt a confidential message sent to you, use your private key.
3. If you want to digitally sign a message you are sending to someone else, use your private key.
4. If you want to verify the signature on a message sent by someone else, use the sender’s public key.

These four rules are the core principles of public key cryptography and digital signatures.

### 2. Digital Signature Standard

**DSS 是专门用于“数字签名”的一套标准，规定了哪些非对称算法可以用于签名用途。**

NIST specifies the digital signature algorithms acceptable for federal government use in Federal Information Processing Standard (FIPS) 186-4, also known as the **Digital Signature Standard (DSS)**. This document specifies that all federally approved digital signature algorithms must use the **SHA-3 hashing** functions.

DSS also specifies the encryption algorithms that can be used to support a digital signature infrastructure. There are three currently approved **standard encryption algorithms**:

■✓ The Digital Signature Algorithm **(DSA)** as specified in FIPS 186-4. This algorithm is a variant of an algorithm developed by Dr. Taher Elgamal, the creator of the ElGamal asymmetric cryptosystem discussed earlier in this chapter.

■✓ The Rivest–Shamir–Adleman **(RSA)** algorithm, as specified in ANSI X9.31.

■✓ The Elliptic Curve DSA **(ECDSA)**, as specified in ANSI X9.62.

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

## Public Key Infrastructure

