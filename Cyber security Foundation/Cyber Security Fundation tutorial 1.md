# Cyber Security Foundation tutorial 1 

## 1.Explain, with examples, how a system that uses all the best encryption techniques can still be insecure

A secure system requires defense in depth. Encryption is just a mechanism to delay an adversary—it is not a shield. If the endpoint is compromised, the keys are mishandled, or the user is tricked, the mathematics of the encryption become irrelevant.

## 2.Explain, with examples, the terms Confidentiality, Integrity and Availability (CIA).

The **CIA Triad** serves as the foundational framework for information security, balancing three critical objectives to protect digital assets. **Confidentiality** ensures that sensitive data remains private and accessible only to authorized users, preventing leaks and eavesdropping. **Integrity** guarantees that information remains accurate and trustworthy, certifying that it has not been tampered with or corrupted during transit or storage. Finally, **Availability** ensures that systems and data are reliable and accessible when needed, preventing downtime from attacks like ransomware or hardware failures.

## 3.Many companies, such as Google, Microsoft, etc., use single sign-on (SSO) for user authentication. SSO is an authentication process that allows a user to access multiple applications or systems with one set of login credentials, typically a username and password. Instead of logging in separately to each application, the user authenticates once, and this authentication is trusted across multiple systems. Think about the university email login system, once you login your email (get authenticated), you could use the Moodle, My Campus system without log in separately to each system. Another example is Google account, YouTube and other Google service apps. What cybersecurity aspects (choose from Confidentiality, Integrity, Availability, Authenticity, Accountability, and Non-repudiation) can SSO user authentication provide to a company’s system? Please explain the reason for each aspect achieved.

Single Sign-On (SSO) enhances a company's cybersecurity posture by centralizing the authentication process, allowing users to access multiple systems with one set of credentials. This mechanism primarily strengthens **Authenticity** by utilizing a trusted Identity Provider to verify user identity, and **Confidentiality** by minimizing the number of times a user must enter (and potentially expose) their password. Additionally, SSO ensures **Integrity** through the use of digitally signed tokens that prevent tampering during the authentication hand-off, while establishing **Accountability** by creating a unified, centralized audit trail of all user access across the ecosystem.

## 4.Please list at least three cybersecurity standards.

Three widely recognized cybersecurity standards are **ISO/IEC 27001**, the **NIST Cybersecurity Framework (CSF)**, and **PCI DSS**, each serving distinct roles in information protection. **ISO 27001** is a global standard focused on governance, requiring organizations to implement an Information Security Management System (ISMS) to manage risk systematically. The **NIST CSF** provides a flexible, voluntary framework that helps organizations of all sizes align their security strategies with business goals through core functions like Identify, Protect, and Recover. In contrast, **PCI DSS** is a highly specific, prescriptive standard designed strictly for the payment industry, enforcing rigorous technical controls on any organization that processes or stores credit card data.

## 5.Please summarize the main cybersecurity terminology we introduced in the lecturer, and describe their relationships.

The lecture defines cybersecurity as the protection of **assets** (valuable digital or non-digital items) against **threats** that exploit system **vulnerabilities** (collectively the "attack surface") to mitigate **risk**. This protection is achieved through a "High-level plan" that uses **policies** (rules) enforced by **mechanisms** (software/hardware) to secure six key aspects: **Confidentiality, Integrity, Availability, Authenticity, Accountability, and Non-repudiation**. Finally, the lecture emphasizes that security is a **socio-technical** discipline, meaning technical solutions must be integrated with human factors and compliance to be truly effective.



