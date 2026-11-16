---

## 1. Introduction to Web Traffic Structure

Web security aims to ensure users can safely browse the web by visiting various sites without incurring harm.

**HTTP (Hyper Text Transfer Protocol)**: An "application-layer" protocol used for exchanging collections of data between a browser (client) and a web server.

**Message Model**: HTTP uses a message-based model where the client sends a request and the server returns a response.

**Statelessness**: HTTP is stateless, meaning it has no inherent way of recognizing the same client from a previous session. Without additional mechanisms, a user would have to log in for every single page load.

---

## 2. Web Security Goals

The primary goals for secure browsing are:

* **Integrity**: Site A must not be able to affect a user's session on Site B.
* **Confidentiality**: Site A must not be able to steal information from the user's device or from Site B.

---

## 3. Interacting with Web Servers

Resources on a server are identified by a URL (e.g., `http://www.cs.umd.edu/~dml/home.html`):

* **Protocol**: Common protocols include http, https, ftp, and tor.
* **Hostname/Server**: This is translated into an IP address by DNS.
* **Path to Resource**: Can be Static Content (a fixed file) or Dynamic Content (generated on the fly by the server).

---

## 4. HTTP Requests and Responses

### Request Methods

**GET**: Designed to retrieve data. All data is included in the URL query string.

* **Characteristics**: Can be cached, bookmarked, and remains in browser history. It should never be used for sensitive data.

**POST**: Used to upload data to a resource. Data is sent in the message body rather than the URL.

* **Characteristics**: Never cached, cannot be bookmarked, and has no data length restrictions.

### Common HTTP Headers

Headers describe the capabilities and requirements of the client and server:

* **Accept**: Tells the server what content types (images, documents) the client can handle.
* **Cookie**: Submits previously issued cookies back to the server.
* **Host**: Specifies the hostname in the requested URL.
* **Referer**: Indicates the URL from which the request originated.
* **User-Agent**: Provides info about the browser or software generating the request.
* **Connection**: Instructions for the TCP connection.
* **Keep-Alive**: Allows a single TCP connection to stay open for multiple requests/responses. This is default in HTTP/2.0.

---

## 5. HTTPS and Security Attacks

**HTTPS (Secure)** is an encrypted version of HTTP using SSL/TLS to encrypt all communication between client and server.

### Common Vulnerabilities

* **SSL Strip**: An attack that forces a browser to communicate over insecure HTTP instead of HTTPS. This can be done via manual proxy settings, ARP Poisoning, or creating a malicious Wi-Fi hotspot.
* **TLS Downgrade Attacks**: Forcing a protocol to abandon high-quality encryption for older, weaker modes (cleartext) for backward compatibility.
* **Mixed Content**: Occurs when a secure HTTPS page loads sub-resources (images, scripts) over an insecure HTTP connection.

---

## 6. Defensive Strategies

* **Server-side**: Implement HTTP Strict Transport Security (HSTS).
* **User-side**: Enable Forced HTTPS / Always On in browser settings.

### Best Practices

* Remove backward compatibility for insecure TLS versions.
* Bookmark the HTTPS versions of critical sites (like banking) and only access them via bookmarks.
* Never bypass certificate warnings.

---
