---

## 1. Web Architecture and Databases

A basic web architecture consists of a **Client** (using a **Browser**) interacting with a **Server**. The server contains a **Web Server** and a **Database** (DB), which is a separate logical and often physical entity.

### Database Basics

* **Purpose**: Databases provide data storage and manipulation.
* **Structure**: A designer lays out data into **Tables**.
* **Components**: Tables consist of **Columns** (categories like Name, Age, Email) and **Rows** (individual records).
* **DBMS**: Database Management Systems provide semantics for organizing data, transactions for sane manipulation, languages for querying (SQL), APIs for interoperability, and management of users/permissions.

---

## 2. SQL (Standard Query Language)

SQL is used to interact with the database through various commands:

* **SELECT**: Retrieves data (e.g., `SELECT Age FROM Users WHERE Name="Dee"` returns 28).
* **UPDATE**: Modifies existing data (e.g., changing an email address).
* **INSERT**: Adds new data into a table.
* **DROP TABLE**: Deletes an entire table and its data.

---

## 3. SQL Injection (SQLi)

SQLi is a command injection attack where the boundary between user-provided data and code is blurred. It accounts for over **50% of all web application attacks**.

### How it Works

Attackers typically prematurely terminate a text string and append a new command.

* **Normal Input**: `i192034` results in `SELECT ... WHERE id = 'i192034'`.
* **Malicious Input**: `';--` results in `SELECT ... WHERE id = '';--'`.
  * The `'` closes the string.
  * The `;` ends the statement.
  * The `--` comments out the rest of the original query.

### Common Attack Variations

* **End of Line Comments**: Using `' OR 1=1; --` to bypass login screens by making the query always evaluate to true.
* **Piggy-Backed Queries**: Chaining a second command using a semicolon, such as `; DROP TABLE Users;`.
* **Retrieving Hidden Data**: Adding `'--` to ignore conditions like `released=1` to see unreleased products.
* **UNION-Based**: Using `UNION SELECT` to retrieve data from different tables, such as the database schema (`information_schema.tables`) or user credentials.

---

## 4. Blind SQL Injections

When a server does not return direct data, attackers use "Blind" techniques to reconstruct information by observing server behavior.

* **Conditional Responses**: Triggering different page content (e.g., "Welcome back") based on whether a character guess is correct.
* **SQL Errors**: Triggering a database error (like a divide-by-zero `$1/0$`) if a condition is met.
* **Time Delays**: Inducing a pause in the server response (e.g., `WAITFOR DELAY '0:0:30'`) to confirm a correct guess.

---

## 5. Finding Targets and Evasion

* **Google Dorking**: Using specific search queries like `inurl:index.php?id=` to find potentially vulnerable sites.
* **Vulnerability Testing**: Adding an apostrophe `'` to a URL; if a SQL error is returned, the site is likely vulnerable.
* **Bypassing Filters**: Attackers may use **Hex Encoding** (e.g., `0x61646D696E`) or the **CHAR()** function to bypass simple text filters.

---

## 6. Countermeasures and Mitigation

The underlying issue is the combination of code and data in a single string.

### Primary Defenses

* **Prepared Statements & Bind Variables**: The **most effective** method. It decouples code from data. The query is compiled first with placeholders (`?`), and user data is treated strictly as data, never being re-compiled as code.
* **Whitelisting**: Only allowing input known to be safe (e.g., an integer within a range).
* **Escaping Characters**: Using functions like `mysql_real_escape_string()` to neutralize dangerous characters like `'` or `;`.

### Secondary Defense (Mitigating Impact)

* **Principle of Least Privilege**: Limit the database user permissions so they can only access necessary tables/commands.
* **Encryption**: Encrypt sensitive data (like credit card numbers) so it remains protected even if stolen.
* **Blacklisting**: Deleting specific characters (e.g., `;` or `'`). This is **flawed** because those characters may be needed for legitimate names like "Peter O'Connor".

---
