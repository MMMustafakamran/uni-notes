### Lecture 17 – Access Control (Summary Notes)

---

### 1. AAA: Authentication, Authorization, Accounting

- **Authentication**: Who are you? (passwords, tokens, biometrics).
- **Authorization**: What are you allowed to do? (permissions, roles).
- **Accounting (Auditing)**: What did you do? (logs for monitoring and forensics).

---

### 2. Core Principles

- **Least privilege**: Grant only the minimum rights needed.
- **Separation of duties**: Split critical tasks between different roles.
- **Need-to-know**: Access to information only when required for duties.

---

### 3. Access Control Models

- **DAC (Discretionary Access Control)**:
  - Resource owner decides who can access what.
  - Implemented with file permissions, ACLs.
- **MAC (Mandatory Access Control)**:
  - System-enforced policies; labels (e.g., Secret, Top Secret).
  - Used in high-security environments.
- **RBAC (Role-Based Access Control)**:
  - Permissions grouped into roles; users assigned to roles.
  - Easier enterprise management (Admin, Manager, User).
- **ABAC (Attribute-Based Access Control)** (if applicable):
  - Decisions based on attributes of user, resource, environment and policy rules.

---

### 4. Mechanisms and Pitfalls

- Mechanisms:
  - ACLs on objects.
  - Groups/roles for users.
  - Capability lists (per-subject rights).
- Pitfalls:
  - Over-privileged accounts.
  - Missing server-side checks.
  - Insecure Direct Object References (IDOR) via predictable IDs in URLs.

---

### 5. Best Practices

- Enforce least privilege and regularly review permissions.
- Use RBAC/ABAC for scalable, maintainable policies.
- Implement access checks on the server, not just in the UI.
- Log and audit access for anomaly detection and compliance.


