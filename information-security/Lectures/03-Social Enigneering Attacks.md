### Lecture 03 – Social Engineering Attacks (Summary Notes)

---

### 1. Concept and Importance

- **Definition**: Social engineering is the manipulation of people to make them give up confidential information, grant access, or perform actions that violate security policy.
- **Target**: Primarily humans (users, employees, helpdesk) rather than software or hardware.
- **Role in attacks**:
  - Often the **first step** in broader attacks (malware infection, APTs, fraud).
  - Bypasses strong technical controls by exploiting **human weaknesses**.

---

### 2. Why Social Engineering Works

- **Human limitations**: People cannot be “patched” like software; they get tired, distracted, or emotional.
- **Underestimation**: Organizations invest heavily in technical security but underestimate human factors.
- **Psychological levers**:
  - **Authority** – “This is your CEO / bank / police.”
  - **Urgency** – “Act now or your account will be closed.”
  - **Scarcity** – “Limited-time offer / last chance.”
  - **Social proof** – “Everyone else has already done this.”
  - **Liking/rapport** – Friendly, relatable attacker.
  - **Reciprocity** – Attacker first does a “favor,” expects one back.
  - **Commitment/consistency** – Small initial agreement leads to larger compliance.

---

### 3. Common Social Engineering Techniques

#### 3.1 Phishing (Email/Web)
- **Phishing**: Mass fraudulent emails/websites that mimic trusted entities to:
  - Steal **credentials** (usernames, passwords, OTPs).
  - Deliver **malware** via attachments or malicious links.
- **Signs of phishing**:
  - Suspicious or spoofed sender address.
  - Generic greetings (“Dear Customer”).
  - Spelling/grammar issues, unexpected attachments.
  - Links that look right but point to malicious domains.

#### 3.2 Spear Phishing and Whaling
- **Spear phishing**:
  - Targeted at specific individuals or groups.
  - Uses information from **reconnaissance** (LinkedIn, websites, social media).
  - Highly personalized, much harder to spot.
- **Whaling**:
  - Targets senior executives (“big fish”).
  - Common in **Business Email Compromise (BEC)** – fake CEO/CFO requests for urgent wire transfers or sensitive data.

#### 3.3 Vishing and Smishing
- **Vishing (Voice phishing)**:
  - Attacker calls pretending to be bank, IT support, government, etc.
  - Uses **caller ID spoofing** to look legitimate.
  - Tries to extract PINs, passwords, OTPs or convince user to install remote access tools.
- **Smishing (SMS phishing)**:
  - Malicious links or phone numbers sent via SMS/messaging apps.
  - Typical lures: package delivery, account lock, prize notifications.

#### 3.4 Pretexting
- **Pretexting**: Creating a believable story (pretext) to justify sensitive requests.
  - Examples: fake auditor, new employee, vendor, law enforcement, or “IT verification.”
  - Supported by details learned from **open-source information**.
  - Goals: bypass authentication, reset passwords, obtain internal data.

#### 3.5 Baiting and Quid Pro Quo
- **Baiting**:
  - Offering something attractive to lure victims into compromising actions.
  - Examples: infected USB labeled “Salaries,” free pirated software/media, free Wi-Fi access point.
- **Quid Pro Quo**:
  - “Something for something” – benefit in exchange for compliance.
  - Example: fake tech support offers performance fixes if user disables security or shares credentials; surveys promising rewards for detailed personal data.

#### 3.6 Tailgating (Piggybacking)
- **Tailgating**:
  - Attacker physically follows authorized person into secure area without a badge.
  - Exploits politeness (holding doors) and busy environments.
  - Once inside, attacker can access systems, plug in devices, observe layout.

#### 3.7 Shoulder Surfing
- **Shoulder surfing**:
  - Observing screens and keyboards to capture passwords, PINs, or confidential data.
  - Can be up-close (line at ATM) or at a distance (cameras, binoculars).
  - Risky in public places like cafés, airports, conferences.

#### 3.8 Dumpster Diving
- **Dumpster diving**:
  - Searching trash for useful information:
    - Printed documents, contact lists, org charts.
    - Old media (CDs, USBs) not wiped.
    - Sticky notes with passwords.
  - Data found is used to craft **more convincing pretexts** or attacks.

#### 3.9 Hoaxes, Fake Alerts, and Scareware
- **Hoaxes**:
  - False security messages/emails that cause panic or trick users into unsafe actions.
  - Example: email instructing users to delete critical system files to “remove a virus.”
- **Scareware**:
  - Fake antivirus / pop-ups claiming “Your computer is infected.”
  - Prompts user to download a “cleaner” that is actually malware (trojan, ransomware).

---

### 4. Social Engineering + Malware / Kill Chain

- Social engineering is often the **delivery vector** in the Cyber Kill Chain:
  1. **Reconnaissance** – Gather info on people and org.
  2. **Weaponization** – Prepare malicious attachments, links, pretexts.
  3. **Delivery** – Phishing email, phone call, USB drop, fake site.
  4. **Exploitation** – User clicks link, opens file, installs software, or reveals credentials.
  5. **Installation** – Malware or backdoor installed.
  6. **Command & Control (C2)** – Attacker gains remote control.
  7. **Actions on Objectives** – Data theft, fraud, system disruption.

---

### 5. Defensive Measures Against Social Engineering

#### 5.1 Security Awareness and Training
- Regular, updated training for all staff on:
  - Recognizing phishing/vishing/smishing.
  - Safe handling of attachments and links.
  - Policies on sharing credentials and responding to unusual requests.
- Use **simulated phishing campaigns** to test and reinforce behavior.

#### 5.2 Policies and Verification Procedures
- Enforce **“never share passwords/OTPs”** rule (even with IT).
- Require **out-of-band verification** for high-risk actions:
  - Phone confirmation using known internal numbers for wire transfers, account changes, or large data exports.
- Formal procedures for:
  - Helpdesk identity verification.
  - Incident reporting and escalation.

#### 5.3 Technical Controls
- **Email security**:
  - Spam/phishing filters, attachment and URL scanning.
  - SPF, DKIM, DMARC to combat spoofed sender domains.
- **Web security**:
  - URL filtering, blocking known malicious domains.
  - Browser protections against pop-ups and drive-by downloads.
- **Endpoint security**:
  - Updated antivirus/EDR.
  - Application whitelisting in sensitive environments.
- **Multi-Factor Authentication (MFA)**:
  - Reduces impact of stolen passwords (though phishing-resistant MFA is best).

#### 5.4 Physical and Document Security
- Enforce badge checks at doors; discourage holding doors for unknown persons.
- Train staff to **challenge unknown individuals** politely.
- Use locked bins and **proper shredding** for sensitive documents.

#### 5.5 Culture: “Trust but Verify”
- Encourage staff to **verify** unusual or high-impact requests:
  - If a “CEO email” asks for an urgent transfer, call the CEO or known assistant using internal directory numbers.
  - If “IT” calls unexpectedly, hang up and call the official helpdesk.
- No punishment for cautious verification; reward correct reporting of suspicious activity.

#### 5.6 Monitoring and Incident Response
- Log and monitor:
  - Suspicious login activity, geolocation anomalies, mass password resets.
  - Multiple users receiving similar suspicious messages.
- Have a clear process to:
  - Revoke credentials and device access quickly.
  - Contain and investigate incidents.
  - Notify affected parties if data may be compromised.

---

### 6. Key Takeaways

- Social engineering attacks exploit **people**, not just technology.
- Techniques include phishing, spear phishing, whaling, vishing, smishing, pretexting, baiting, tailgating, shoulder surfing, dumpster diving, and scareware.
- These attacks rely on predictable psychological principles and are frequently used to deliver malware or start major breaches.
- Effective defense requires a **combination** of: user training, strict policies, technical controls, strong physical security, and a culture that supports verification and rapid reporting. 


