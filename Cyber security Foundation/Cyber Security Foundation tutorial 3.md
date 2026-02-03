# Cyber Security Foundation tutorial 3

# Access Control Tutorial - Solutions & Explanations
# 访问控制教程 - 答案与解析

This document contains the solutions, logic, and principles for the problems found in the "Tutorial_Access Control.pdf".
本文档包含了 "Tutorial_Access Control.pdf" 中问题的答案、逻辑推导及原理。

---

## Problem 1: Discretionary Access Control (DAC) Graphs
## 问题 1：自主访问控制 (DAC) 图

**Context / 背景:**
For the DAC model, an alternative representation of the protection state is a directed graph. Subjects and Objects are nodes. [cite_start]A directed line from a Subject to an Object indicates an access right [cite: 2-4].
[cite_start]对于 DAC 模型，保护状态的另一种表示形式是有向图。主体和客体是节点。从主体指向客体的有向线表示访问权限 [cite: 2-4]。

### Part (a)
[cite_start]**Question:** Draw a directed graph that corresponds to the access matrix for User A, B, C and Files 1-4 [cite: 5-32].
**问题：** 画出对应于用户 A、B、C 和文件 1-4 的访问矩阵的有向图。

**Answer & Logic / 答案与逻辑:**
* **Principle:** Create a node for every User and File. Draw arrows where a user has a right to a file.
    **原理：** 为每个用户和文件创建一个节点。如果用户对文件有权限，则画一条箭头。

* **Graph Structure / 图结构描述:**
    * **User A (Node)**
        * $\rightarrow$ **File 1**: {Own, Read, Write}
        * $\rightarrow$ **File 3**: {Own, Read, Write}
    * **User B (Node)**
        * $\rightarrow$ **File 1**: {Read}
        * $\rightarrow$ **File 2**: {Read, Write}
        * $\rightarrow$ **File 3**: {Read}
        * $\rightarrow$ **File 4**: {Write}
    * **User C (Node)**
        * $\rightarrow$ **File 2**: {Read, Write}
        * $\rightarrow$ **File 4**: {Own, Read, Write}

### Part (b)
[cite_start]**Question:** Draw a directed graph that corresponds to the access matrix for Subjects $S_1, S_2, S_3$ and various objects ($F_1, P_1, D_1$, etc.) [cite: 33-70].
**问题：** 画出对应于主体 $S_1, S_2, S_3$ 和各种客体（$F_1, P_1, D_1$ 等）的访问矩阵的有向图。

**Answer & Logic / 答案与逻辑:**
* **Principle:** Subjects can also act as Objects (e.g., $S_1$ controlling $S_2$).
    **原理：** 主体也可以作为客体（例如 $S_1$ 控制 $S_2$）。

* **Graph Structure / 图结构描述:**
    * **Node $S_1$**
        * $\rightarrow$ **$F_1$**: {Owner}
        * $\rightarrow$ **$F_2$**: {Read}
        * $\rightarrow$ **$P_1$**: {Wakeup / Control}
        * $\rightarrow$ **$D_1$**: {Seek, Owner}
    * **Node $S_2$**
        * $\rightarrow$ **$F_2$**: {Write, Execute}
        * $\rightarrow$ **$S_2$**: {Control} (Reflexive / 自反)
        * $\rightarrow$ **$D_2$**: {Owner, Seek}
    * **Node $S_3$**
        * $\rightarrow$ **$S_3$**: {Control}
        * $\rightarrow$ **$F_2$**: {Write, Stop}

### Part (c)
**Question:** Is there a one-to-one correspondence between the directed graph representation and the access matrix representation? Explain.
**问题：** 有向图表示法和访问矩阵表示法之间是否存在一一对应关系？请解释。

**Answer / 答案:**
**Yes / 是**

**Logic / 逻辑:**
Both representations store the exact same data.
1.  **Matrix $\to$ Graph:** Every non-empty cell becomes an edge.
2.  **Graph $\to$ Matrix:** Every edge becomes a cell entry.
No information is lost or created in the conversion.

两种表示法存储完全相同的数据。
1.  **矩阵 $\to$ 图：** 每个非空单元格变成一条边。
2.  **图 $\to$ 矩阵：** 每条边变成一个单元格条目。
在转换过程中没有任何信息丢失或增加。

---

## Problem 2: Scalability (DAC vs. RBAC)
## 问题 2：扩展性（DAC 与 RBAC 对比）

**Context / 背景:**
System with $N$ job positions. [cite_start]Position $i$ has $U_i$ users and requires $P_i$ permissions[cite: 72].
[cite_start]系统有 $N$ 个职位。职位 $i$ 有 $U_i$ 个用户，需要 $P_i$ 个权限 [cite: 72]。

### Part (a)
[cite_start]**Question:** For a traditional discretionary access control (DAC) scheme, how many relationships between users and permissions must be defined? [cite: 73]
**问题：** 对于传统的自主访问控制（DAC）方案，必须定义多少个用户与权限之间的关系？

**Answer / 答案:**
$$\sum_{i=1}^{N} (U_i \times P_i)$$

**Logic / 逻辑:**
In DAC, permissions are assigned directly to users. If a role has 10 users and 5 permissions, the admin must make $10 \times 5 = 50$ assignments.
在 DAC 中，权限直接分配给用户。如果一个角色有 10 个用户和 5 个权限，管理员必须进行 $10 \times 5 = 50$ 次分配。

### Part (b)
[cite_start]**Question:** For a role-based access control (RBAC) scheme, how many relationships between users and permissions must be defined? [cite: 74]
**问题：** 对于基于角色的访问控制（RBAC）方案，必须定义多少个用户与权限之间的关系？

**Answer / 答案:**
$$\sum_{i=1}^{N} (U_i + P_i)$$

**Logic / 逻辑:**
In RBAC, an intermediary "Role" is used.
1.  Assign $U_i$ users to the Role ($U_i$ links).
2.  Assign $P_i$ permissions to the Role ($P_i$ links).
Total links = $U_i + P_i$.
在 RBAC 中，使用中间的“角色”。
1.  将 $U_i$ 个用户分配给角色（$U_i$ 个链接）。
2.  将 $P_i$ 个权限分配给角色（$P_i$ 个链接）。
总链接数 = $U_i + P_i$。

---

## Problem 3: VAX/VMS Access Modes
## 问题 3：VAX/VMS 访问模式

**Context / 背景:**
[cite_start]VAX/VMS uses 4 modes: Kernel, Executive, Supervisor, User [cite: 75-80].
[cite_start]VAX/VMS 使用 4 种模式：内核、执行、监管、用户 [cite: 75-80]。

### Part (a)
**Question:** What are the advantages and disadvantages of providing four modes instead of two (kernel and user)? [cite: 84-85]
**问题：** 提供四种模式而不是两种（内核和用户）有什么优缺点？

**Answer / 答案:**

* **Advantages (优点):**
    * **Least Privilege (最小权限):** Critical but non-kernel tasks (like file system management) run in "Executive" mode. They are protected from users but cannot crash the whole kernel easily.
        （关键但非内核的任务（如文件系统管理）在“执行”模式下运行。它们受到保护免受用户干扰，但不会轻易导致整个内核崩溃。）
    * **Defense in Depth (纵深防御):** A breach in an outer layer (Supervisor) doesn't grant full Kernel access.
        （外层（监管层）的破坏不会给予完全的内核访问权限。）

* **Disadvantages (缺点):**
    * **Complexity (复杂性):** Harder to design and define boundaries.
        （设计和定义边界更困难。）
    * **Performance (性能):** More overhead for context switching between multiple layers.
        （在多个层之间进行上下文切换的开销更大。）

### Part (b)
**Question:** Can you make a case for even more than four modes? [cite: 86]
**问题：** 你能说明需要超过四种模式的理由吗？

**Answer / 答案:**
**Yes. / 是的。**

**Logic / 逻辑:**
Modern computing requires layers below the OS or specifically isolated from it:
1.  **Hypervisor (Ring -1):** To manage multiple Operating Systems (Virtualization).
2.  **TrustZone (TEE):** Hardware isolation for biometrics and banking apps.
3.  **Sandboxing:** Ultra-restricted modes for web browsers or untrusted scripts.

现代计算需要低于操作系统或与操作系统隔离的层级：
1.  **管理程序 (Ring -1):** 用于管理多个操作系统（虚拟化）。
2.  **信任区 (TEE):** 用于生物识别和银行应用的硬件隔离。
3.  **沙盒:** 用于网络浏览器或不可信脚本的超受限模式。

---

## Problem 4: UNIX File Security (The "730" Trap)
## 问题 4：UNIX 文件安全（"730" 陷阱）

**Context / 背景:**
A file with mode **644** is inside a directory with mode **730**.
一个权限模式为 **644** 的文件位于一个权限模式为 **730** 的目录中。
* **File 644:** Owner (RW), Group (R), Others (R).
* **Dir 730:** Owner (All), **Group (Write/Execute)**, Others (None).

**Question:** How might the file be compromised in this case? [cite: 90]
**问题：** 在这种情况下，文件可能会如何被破坏？

**Answer / 答案:**
A user in the **Group** can **delete or replace** the file.
**组**内的用户可以**删除或替换**该文件。

**Logic / 逻辑:**
1.  **Principle:** In UNIX, the permission to add, remove, or rename a file is governed by the **Directory's Write bit**, not the file's bits [cite: 87-89].
    [cite_start]**原理：** 在 UNIX 中，添加、删除或重命名文件的权限由**目录的写位**控制，而不是文件的权限位 [cite: 87-89]。
2.  **The Attack:** Since the directory is **730**, the Group has Write access (`3` = `-wx`). A group member cannot write *into* the file (file is 644 read-only for group), but they can **unlink (delete)** the file from the directory and create a **new file** with the same name.
    **攻击方式：** 由于目录是 **730**，组拥有写权限 (`3` = `-wx`)。组成员不能写入文件*内部*（文件对组是 644 只读），但他们可以从目录中**取消链接（删除）**该文件，并创建一个同名的**新文件**。