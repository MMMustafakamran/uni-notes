## Introduction to Information Security – Summary Notes

### 1. Core Idea and Goals

- **Information security** protects the **confidentiality, integrity, and availability (CIA)** of information on systems that store, process, and transmit it, using **technology, people, and processes**.
- **Organizational goals**:
  - **Prevent data and identity theft**
  - **Avoid legal/regulatory penalties**
  - **Maintain productivity and uptime**
  - **Prevent or limit cyberterrorism and large‑scale disruption**
- Importance: attacks and breaches are **frequent, large‑scale, and high‑impact**, making security a persistent **top IT priority**.

### 2. Modern Attacks and Breaches

- **Attack examples**:
  - **Fake antivirus / scareware** to trick users into installing malware or paying money.
  - **Wireless camera compromise** due to poor/default security.
  - **ATM malware** (e.g., Ploutus) to force cash out or skim data.
  - **Social media hijacking** via weak passwords, phishing, or credential reuse.
  - **Malicious files/links** on marketplaces like Craigslist/eBay.
- **Breach patterns**:
  - Universities/hospitals: stolen **personal, financial, and medical data**.
  - Tech/retail (e.g., Adobe, Target): stolen **credentials and card data**.
- **Sony 2011 breaches (PSN, SOE, SonyPictures)**:
  - All exploited **SQL injection**.
  - Tens of millions of accounts exposed; repeated incidents across related systems.

### 3. Why Defense Is Hard

- **Always‑connected devices**: almost everything is online, reachable globally.
- **Attack speed**: automated tools scan **millions of hosts in minutes**.
- **Sophisticated evasion**: malicious traffic hides inside normal **HTTP/HTTPS/DNS/email**, often encrypted.
- **Low skill requirement**: tools (e.g., **Kali Linux**, exploit kits) enable **inexperienced attackers**.
- **Rapid vulnerability discovery and weaponization**.
- **Slow patching**: vendors and organizations delay fixes; many systems stay **unpatched**.
- **Botnets and DDoS**: large numbers of compromised devices (e.g., **Mirai**) can overwhelm targets.

### 4. Attacker Types and Motives

- **Cybercriminals**: financially motivated; steal money or data for resale.
- **Script kiddies**: low skill; use others’ tools for thrills, curiosity, or notoriety.
- **Vulnerability brokers**: find/buy **0‑days** and sell to highest bidder.
- **Insiders**: already trusted; may leak, steal, or manipulate data for revenge, gain, or ideology.
- **Cyberterrorists**: ideologically driven; target **critical infrastructure** to cause fear or damage.
- **Hacktivists**: political/social motives; deface sites, leak data, or disrupt services to protest.
- **State‑sponsored groups**: strategic advantage and espionage; target governments, militaries, and key industries.

### 5. Advanced Persistent Threats (APT) and Stuxnet

- **APT characteristics**:
  - **Advanced**: custom malware, rootkits, **0‑day exploits**, stealthy C2.
  - **Persistent**: long‑term campaigns; repeated probing and hidden presence.
  - **Threat**: focused on **high‑value targets** and **strategic objectives**.
- **Stuxnet**:
  - Targeted specific **Siemens ICS** used in Iranian nuclear facilities.
  - Used multiple 0‑days and highly tailored logic.
  - Demonstrates that malware can achieve precise **physical and geopolitical impact**.

### 6. Cyber Kill Chain (7‑Step Attack Model)

1. **Reconnaissance** – gather data on systems, software, and people.
2. **Weaponization** – build exploit + payload (e.g., malicious document).
3. **Delivery** – send payload (phishing, web exploit, USB, etc.).
4. **Exploitation** – trigger vulnerability (user opens file, visits site, etc.).
5. **Installation** – install malware/backdoor for persistence.
6. **Command & Control (C2)** – compromised host contacts attacker infrastructure.
7. **Actions on Objectives** – data theft, lateral movement, destruction, or espionage.

### 7. Fundamental Security Principles (Defense in Depth)

- **Layering**: multiple independent security layers (firewall, IDS/IPS, endpoint security, logging, access control).
- **Limiting (least privilege)**:
  - Restrict access to only what users/processes need.
  - Use technical controls (ACLs, RBAC, segmentation) and procedural controls (need‑to‑know, policy).
- **Diversity**:
  - Avoid single‑vendor or single‑technology dependence.
  - Mix products and platforms so one flaw does not break all defenses.
- **Obscurity**:
  - Do not leak unnecessary internal details (OS versions, internal IPs, stack info, detailed errors).
  - Makes targeted exploitation more difficult (but not a primary defense alone).
- **Simplicity**:
  - Keep internal configurations understandable and maintainable.
  - Externally, make analysis and exploitation complex.
  - Complexity tends to create misconfigurations and weak points.

### 8. Big‑Picture Takeaways

- Attacks are **more frequent, more damaging, and more automated**, while powerful tools are widely accessible.
- Effective security programs:
  - Enforce **CIA** using integrated **technology, people, and process** controls.
  - Account for diverse **attacker types and motives**, including APTs.
  - Use lifecycle models like the **Cyber Kill Chain** to detect and disrupt attacks early.
  - Apply **layering, limiting, diversity, obscurity, and simplicity** to build resilient defenses.


