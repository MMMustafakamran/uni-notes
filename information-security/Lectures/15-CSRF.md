### Lecture 15 – Cross-Site Request Forgery (CSRF) (Summary Notes)

---

### 1. Definition and Idea

- **CSRF**: Forces a logged-in user’s browser to send unwanted requests to a site where they are authenticated.
- Exploits the **browser’s automatic cookie sending**; attacker’s site triggers requests, victim’s browser adds valid cookies/session.

---

### 2. Typical Scenario

- User logged into `target.com` (has valid session cookie).
- Visits attacker-controlled site `evil.com`.
- `evil.com` includes hidden form or image that submits a request to `target.com`.
- Browser sends request with `target.com` cookies → server may perform action (e.g., money transfer) as the user.

---

### 3. CSRF vs XSS

- **CSRF**: Website trusts the browser; attacker abuses auto-sent cookies via cross-site requests.
- **XSS**: User trusts the website; attacker runs script in the site context.

---

### 4. Defenses

- **Synchronizer Token Pattern (CSRF token)**:
  - Server generates random token, stores it, and embeds it in forms.
  - Server verifies token on submission; missing/invalid → reject.
- **Double Submit Cookie**:
  - CSRF value stored in cookie and sent in header/form field; server checks they match.
- **SameSite cookies**:
  - `SameSite=Lax` or `Strict` restricts sending cookies on cross-site requests; strong CSRF mitigation.
- Additional:
  - Use POST (with protections) for state changes.
  - Re-authenticate for sensitive operations, consider MFA.


