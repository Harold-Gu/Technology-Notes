# Cyber Security Foundation tutorial 2

### 1. Threat, Vulnerability, and Risk (威胁、漏洞与风险)

**English:** The core difference lies in their relationship to security incidents. A **Threat** is a potential external danger (like a hacker or a virus) that can cause harm. A **Vulnerability** is an internal weakness or flaw in a system (like an unpatched software bug). **Risk** is the probability and impact of a threat actually exploiting a vulnerability to cause loss or damage.

### 2. Three-Way Handshake Process (三次握手过程)

**English:** This is the process used by the TCP protocol to establish a reliable connection between a client and a server. It involves three steps: 1. The client sends a **SYN** (synchronize) packet to request a connection. 2. The server responds with a **SYN-ACK** (synchronize-acknowledge) packet. 3. The client sends a final **ACK** (acknowledge) packet to confirm, and the connection is established.

**中文：** 这是 TCP 协议用于在客户端和服务器之间建立可靠连接的过程。它包含三个步骤：1. 客户端发送 **SYN**（同步）包请求连接；2. 服务器回复 **SYN-ACK**（同步-确认）包；3. 客户端发送最后的 **ACK**（确认）包进行确认，连接随即建立。

### 3. Man-in-the-Middle Attack (中间人攻击)

**English:** A Man-in-the-Middle (MitM) attack occurs when an attacker secretly intercepts and relays communication between two parties who believe they are talking directly to each other. To prevent this, users should use strong encryption protocols (like HTTPS/TLS), utilize Virtual Private Networks (VPNs) to secure data channels, and avoid connecting to unsecured public Wi-Fi networks.

**中文：** 中间人 (MitM) 攻击是指攻击者秘密拦截并转发通信双方的信息，而双方却误以为他们在直接交谈。为了预防这种情况，用户应使用强加密协议（如 HTTPS/TLS），利用虚拟专用网络 (VPN) 保护数据通道，并避免连接不安全的公共 Wi-Fi 网络。

### 4. DDoS Attack (分布式拒绝服务攻击)

**English:** A Distributed Denial of Service (DDoS) attack involves overwhelming a target server or network with a flood of malicious internet traffic from multiple compromised devices (botnets), causing the service to crash or become inaccessible. Prevention methods include implementing firewalls to filter traffic, using rate limiting to restrict request volume, and utilizing Content Delivery Networks (CDNs) to absorb and disperse the attack traffic.

**中文：** 分布式拒绝服务 (DDoS) 攻击涉及利用来自多个受感染设备（僵尸网络）的海量恶意互联网流量淹没目标服务器或网络，导致服务崩溃或无法访问。预防方法包括部署防火墙过滤流量，使用速率限制来控制请求量，以及利用内容分发网络 (CDN) 来吸收和分散攻击流量。

### 5. The Seven Layers of the OSI Model (OSI 模型的七层)

**English:** The Open Systems Interconnection (OSI) model standardizes networking into seven layers. From bottom to top:

1. **Physical:** Transmits raw bit streams (cables).
2. **Data Link:** Manages node-to-node transfer (MAC addresses).
3. **Network:** Handles routing and addressing (IP).
4. **Transport:** Ensures end-to-end reliability (TCP/UDP).
5. **Session:** Manages communication sessions.
6. **Presentation:** Formats and encrypts data.
7. **Application:** Provides the interface for end-user software (HTTP, SMTP).

**中文：** 开放系统互连 (OSI) 模型将网络标准化为七层。从下到上依次为：

1. **物理层：** 传输原始比特流（电缆）。
2. **数据链路层：** 管理节点到节点的传输（MAC 地址）。
3. **网络层：** 处理路由和寻址（IP）。
4. **传输层：** 确保端到端可靠性（TCP/UDP）。
5. **会话层：** 管理通信会话。
6. **表示层：** 格式化和加密数据。
7. **应用层：** 为最终用户软件提供接口（HTTP, SMTP）。



![image-20260127144450843](C:\Users\ghy001\AppData\Roaming\Typora\typora-user-images\image-20260127144450843.png)

