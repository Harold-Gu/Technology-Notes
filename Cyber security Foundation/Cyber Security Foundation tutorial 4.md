# Cryptography I: Tutorial Solutions (密码学 I：教程习题详解)

This document contains solutions and detailed explanations for the Week 5 Tutorial on Cryptography I.
本文档包含第5周密码学 I 教程的习题解答和详细解释。

---

## 📚 Problem 1: Linear Block Cipher Attack (线性分组密码攻击)

### ❓ Question (题目)
**English:**
Suppose we have a linear block cipher $EL$ that encrypts 128-bit blocks. It follows the linearity property: $EL(k, [m_1 \oplus m_2]) = EL(k, m_1) \oplus EL(k, m_2)$ . Describe how, with 128 chosen ciphertexts, an adversary can decrypt any ciphertext without knowledge of the secret key $k$ .

**中文:**
假设我们要攻击一个加密 128 位数据块的线性分组密码 $EL$。它满足线性性质：$EL(k, [m_1 \oplus m_2]) = EL(k, m_1) \oplus EL(k, m_2)$ 。请描述攻击者如何利用 128 个“选择密文”，在不知道密钥 $k$ 的情况下解密任何密文 。

### 💡 Solution & Explanation (答案与解析)

**The Strategy (攻击策略):**
Since the cipher is linear, the decryption function $DL$ is also linear . We can use a "Basis Vector" attack.
由于密码是线性的，其解密函数 $DL$ 也是线性的 。我们可以使用“基向量”攻击。

1.  **Select Basis (选择基底):**
    The adversary chooses 128 specific ciphertexts, $C^{(1)}, C^{(2)}, \dots, C^{(128)}$. Let each $C^{(i)}$ be a block with the $i$-th bit set to 1 and all other bits set to 0.
    攻击者选择 128 个特定的密文 $C^{(1)}, C^{(2)}, \dots, C^{(128)}$。令每个 $C^{(i)}$ 的第 $i$ 位为 1，其余位均为 0。

2.  **Get Plaintexts (获取明文):**
    Using the "chosen ciphertext" capability, obtain the decryption for each basis vector: $P^{(i)} = DL(k, C^{(i)})$ .
    利用“选择密文”的能力，获取每个基向量的解密结果：$P^{(i)} = DL(k, C^{(i)})$ 。

3.  **Decrypt Target (解密目标):**
    For any new ciphertext $C$, express it as the XOR sum of the basis vectors: $C = \bigoplus_{i=1}^{128} b_i C^{(i)}$ (where $b_i$ is the $i$-th bit of $C$).
    Due to linearity, the plaintext $P$ is:
    $$P = \bigoplus_{i=1}^{128} b_i P^{(i)}$$
    对于任何新的密文 $C$，将其表示为基向量的异或和。根据线性性质，明文 $P$ 即为对应 $P^{(i)}$ 的异或和。

---

## 📚 Problem 2: ECB & CBC Decryption (ECB 与 CBC 模式解密)

### 📊 Setup: Decryption Table (准备工作：解密表)
Based on the provided encryption table , we reverse the mapping ($C \to m$) to create a decryption table:
根据提供的加密表 ，我们反转映射 ($C \to m$) 以创建解密表：

| Cipher ($C$)    |   0   |   1   |   2   |   3   |   4   |   5   |   6   |   7   |   8   |   9   |   a   |   b   |   c   |   d   |   e   |   f   |
| :-------------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Plain ($m$)** | **7** | **0** | **b** | **8** | **3** | **2** | **9** | **d** | **a** | **4** | **f** | **1** | **e** | **6** | **c** | **5** |

### (a) ECB Mode (电子密码本模式)

**Ciphertext:** `187606` 



**Calculation:**
* `1` $\to$ `0`
* `8` $\to$ `a`
* `7` $\to$ `d`
* `6` $\to$ `9`
* `0` $\to$ `7`
* `6` $\to$ `9`

**Answer:** `0ad979`

### (b) CBC Mode (密码分组链接模式)

**Ciphertext:** `301be`
**IV:** `1` 
**Formula:** $P_i = D_K(C_i) \oplus C_{i-1}$ (with $C_0 = IV$) .



**Calculation:**
1.  **Block 1 ($C_1=3$):**
    $D_K(3) = 8$.
    $P_1 = 8 \oplus IV = 8 \oplus 1 = \mathbf{9}$.
2.  **Block 2 ($C_2=0$):**
    $D_K(0) = 7$.
    $P_2 = 7 \oplus C_1 = 7 \oplus 3 = \mathbf{4}$.
3.  **Block 3 ($C_3=1$):**
    $D_K(1) = 0$.
    $P_3 = 0 \oplus C_2 = 0 \oplus 0 = \mathbf{0}$.
4.  **Block 4 ($C_4=b$):**
    $D_K(b) = 1$.
    $P_4 = 1 \oplus C_3 = 1 \oplus 1 = \mathbf{0}$.
5.  **Block 5 ($C_5=e$):**
    $D_K(e) = c$ (binary `1100`).
    $P_5 = c \oplus C_4 = c \oplus b = 1100_2 \oplus 1011_2 = 0111_2 = \mathbf{7}$.

**Answer:** `94007`

### (c) Security Analysis (安全性分析)

**Why is ECB insecure? (ECB 为何不安全?)**
**English:** ECB is deterministic. Identical plaintext blocks are encrypted into identical ciphertext blocks . Attackers can observe these repeating patterns to infer structural information about the message .
**中文:** ECB 是确定性的。相同的明文块会被加密成相同的密文块 。攻击者可以通过观察这些重复的模式来推断消息的结构信息 。

**Recommendation (建议):**
**English:** Use **Cipher Block Chaining (CBC)** mode. It uses an Initialization Vector (IV) and chains previous ciphertexts into the current encryption, ensuring identical plaintexts produce different ciphertexts .
**中文:** 使用 **密码分组链接 (CBC)** 模式。它使用初始化向量 (IV) 并将前一个密文链接到当前的加密中，确保相同的明文产生不同的密文 。

---

## 📚 Problem 3: CBC Error Propagation (CBC 错误传播)

### ❓ Question (题目)
**English:** Suppose an error occurs in a block of ciphertext on transmission using CBC. What effect is produced on the recovered plaintext blocks? 
**中文:** 假设在使用 CBC 传输过程中，密文块发生了一个错误。这对恢复出的明文块会产生什么影响？

### 💡 Solution & Explanation (答案与解析)

**Answer:**
If ciphertext block $C_i$ has an error:
如果密文块 $C_i$ 发生错误：

1.  **Block $P_i$ (Current Block):**
    **Effect:** Completely garbled / Random noise.
    **Reason:** $P_i = D_K(C_i) \oplus C_{i-1}$. Since $C_i$ is the input to the decryption function, any change in $C_i$ results in a completely different, unpredictable output.
    **影响:** 完全损坏 / 随机噪声。
    **原因:** 因为 $C_i$ 是解密函数的输入，输入的改变会导致输出完全不可预测。

2.  **Block $P_{i+1}$ (Next Block):**
    **Effect:** Bit errors in specific positions.
    **Reason:** $P_{i+1} = D_K(C_{i+1}) \oplus C_i$. The error in $C_i$ is directly XORed with the decrypted value. The error appears in $P_{i+1}$ at the exact same bit position as it did in $C_i$.
    **影响:** 特定位置的比特错误。
    **原因:** 错误的 $C_i$ 直接参与异或运算，因此 $C_i$ 哪里错了，$P_{i+1}$ 就会在哪里出错。

3.  **Subsequent Blocks ($P_{i+2}, \dots$):**
    **Effect:** No effect.
    **Reason:** These blocks do not rely on $C_i$.
    **影响:** 无影响。
    **原因:** 后续块不依赖于 $C_i$。