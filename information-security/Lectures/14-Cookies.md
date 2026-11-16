### Lecture 14 – Cookies (Summary Notes)

---

### 1. Purpose and Basics

- **Cookies**: Small key–value pairs stored by the browser and sent with HTTP requests.
- Provide **state** in stateless HTTP:
  - Sessions (logged-in user).
  - Preferences, carts, etc.
- Set via `Set-Cookie` header, sent back in `Cookie` header.

---

### 2. Key Attributes

- **Expires / Max-Age**:
  - Session cookies (no expiry) vs persistent cookies (stored until expiration).
- **Domain / Path**:
  - Control which hosts/paths receive the cookie.
- **Secure**:
  - Send cookie only over HTTPS.
- **HttpOnly**:
  - Hide from JavaScript (`document.cookie`), mitigates theft via XSS.
- **SameSite**:
  - `Strict`, `Lax`, `None`.
  - Governs sending cookies with **cross-site** requests; important CSRF defense.

---

### 3. Cookie Types

- **Session vs persistent**.
- **First-party** (same site) vs **third-party** (other domains, often trackers/ads).

---

### 4. Security Issues

- **Session hijacking**:
  - Stealing session cookies (network sniffing, XSS, malware).
  - Defenses: `Secure`, `HttpOnly`, strong random session IDs.
- **Session fixation**:
  - Attacker sets/forces a known session ID.
  - Defense: regenerate session ID after login.
- **CSRF implications**:
  - Browsers automatically attach cookies to relevant requests, enabling CSRF if not mitigated (see CSRF lecture, SameSite).
- **Privacy / tracking**:
  - Third-party cookies used for cross-site tracking.

---

### 5. Best Practices

- Mark sensitive cookies as `Secure`, `HttpOnly`, and appropriate `SameSite`.
- Regenerate session IDs at login/logout.
- Limit Domain/Path and cookie lifetime.
- Avoid storing sensitive data directly in cookies; store opaque identifiers instead.


