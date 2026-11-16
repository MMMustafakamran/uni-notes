### Lecture 16 – Cross-Site Scripting (XSS) (Summary Notes)

---

### 1. Concept and SOP

- **XSS**: Injecting malicious scripts into web pages so they execute in the context of a trusted site.
- Breaks assumptions of the **Same Origin Policy** by making the browser run attacker code as if it came from the target origin.

---

### 2. Types of XSS

- **Stored (Persistent)**:
  - Malicious script stored on server (DB, comments, profiles) and served to many users.
- **Reflected**:
  - Script comes from current request (e.g., URL parameter) and is reflected in response.
  - Triggered by crafted links/emails.
- **DOM-based**:
  - Vulnerability lives in client-side JS; reads untrusted data (e.g., `location`) and writes to DOM unsafely.

---

### 3. Impact

- Steal cookies (if not HttpOnly), tokens, or other sensitive data.
- Perform actions as the user (change settings, initiate transactions).
- Inject fake forms/UI for phishing, keylogging, etc.

---

### 4. Defenses

- **Input validation**:
  - Whitelist expected formats, but not sufficient alone.
- **Context-specific output encoding** (primary):
  - Escape untrusted data before inserting into:
    - HTML body, attributes, JS, URLs, CSS.
- **Use safe APIs / templating**:
  - Prefer `textContent` over `innerHTML`.
  - Use frameworks that escape by default.
- **Content Security Policy (CSP)**:
  - Restrict allowed script sources, reduce impact of injected scripts.
- **HttpOnly + Secure cookies**:
  - Mitigate cookie theft and ensure cookies only sent over HTTPS.


