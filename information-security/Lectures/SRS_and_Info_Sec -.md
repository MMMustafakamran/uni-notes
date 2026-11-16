### SRS and Information Security (Summary Notes)

---

### 1. Role of SRS in Security

- **SRS (Software Requirements Specification)** defines what the system must do.
- Security must appear as explicit **requirements** in the SRS, not as an afterthought.
- Clear security requirements guide design, implementation, and testing.

---

### 2. Mapping CIA to Requirements

- **Confidentiality**:
  - Requirements for authentication, authorization, and encryption.
- **Integrity**:
  - Requirements for checksums/hashes, access controls, and audit trails.
- **Availability**:
  - Requirements for uptime, redundancy, and resilience to DoS.

---

### 3. Common Security Requirements in SRS

- Authentication/authorization (password policies, MFA, RBAC).
- Data protection (TLS for transit, encryption at rest).
- Logging and auditing of security events.
- Input validation and secure error handling.
- Compliance with regulations and standards where relevant.

---

### 4. Traceability and Testability

- Security requirements should be:
  - **Traceable** to business goals, risks, or regulations.
  - **Testable** so verification can confirm they’re satisfied.
- Good SRS practice helps ensure information security is embedded throughout the software lifecycle.


