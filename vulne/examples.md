# Web Application Security Examples

> Beginner-friendly examples of common vulnerabilities — what insecure code looks like, what safer code looks like, and how to mitigate each issue.
> For secure coding education, code review, and authorized testing only.

---

## Table of Contents

1. [Cross-Site Scripting (XSS)](#1-cross-site-scripting-xss)
2. [SQL Injection (SQLi)](#2-sql-injection-sqli)
3. [Insecure Direct Object Reference (IDOR)](#3-insecure-direct-object-reference-idor)
4. [Server-Side Request Forgery (SSRF)](#4-server-side-request-forgery-ssrf)
5. [File Upload Issues](#5-file-upload-issues)
6. [Command Injection](#6-command-injection)
7. [NoSQL Injection](#7-nosql-injection)
8. [Authentication Weaknesses](#8-authentication-weaknesses)
9. [Security Misconfiguration](#9-security-misconfiguration)
10. [Quick Reviewer Checklist](#10-quick-reviewer-checklist)

---

## 1. Cross-Site Scripting (XSS)

**What is it?**
XSS happens when untrusted user input is rendered in the browser without protection, allowing attacker-controlled JavaScript to run in another user's session.

### ❌ Vulnerable (PHP)

```php
<?php
echo "<h1>Hello " . $_GET['name'] . "</h1>";
?>
```

**Why it's risky:** User input is directly embedded into HTML with no encoding. An attacker can inject `<script>` tags or event handlers.

### ✅ Safer (PHP)

```php
<?php
echo "<h1>Hello " . htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8') . "</h1>";
?>
```

**Why it's safer:** Special characters are escaped before rendering, neutralising injected markup.

---

### ❌ Vulnerable (Client-side JavaScript)

```js
document.getElementById("output").innerHTML = location.hash.substring(1);
```

### ✅ Safer (Client-side JavaScript)

```js
document.getElementById("output").textContent = location.hash.substring(1);
```

**`textContent` never parses HTML — it treats everything as plain text.**

### 🔍 What to look for

- `innerHTML`, `outerHTML`, `document.write`
- Reflected query parameters
- User-generated content (comments, bios, support tickets)
- Search result pages
- Rich text or Markdown rendering

### 🛡️ Mitigation

- Use output encoding appropriate to the context (HTML, JS, URL, CSS)
- Use safe templating engines with auto-escaping
- Prefer `textContent` over `innerHTML`
- Sanitise HTML if rich text is required (e.g. DOMPurify)
- Use Content Security Policy (CSP) as defence-in-depth

---

## 2. SQL Injection (SQLi)

**What is it?**
SQLi happens when user input is concatenated into SQL queries, allowing attackers to alter query logic or exfiltrate data.

### ❌ Vulnerable (PHP)

```php
<?php
$id = $_GET['id'];
$query = "SELECT * FROM users WHERE id = $id";
$result = mysqli_query($conn, $query);
?>
```

### ✅ Safer (PHP)

```php
<?php
$stmt = $conn->prepare("SELECT * FROM users WHERE id = ?");
$stmt->bind_param("i", $_GET['id']);
$stmt->execute();
$result = $stmt->get_result();
?>
```

---

### ❌ Vulnerable (Python)

```python
user_id = request.args.get("id")
query = f"SELECT * FROM users WHERE id = {user_id}"
cursor.execute(query)
```

### ✅ Safer (Python)

```python
user_id = request.args.get("id")
cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))
```

### 🔍 What to look for

- Raw SQL query strings
- String concatenation inside queries
- Search and filter parameters passed to DB
- Login forms and report export endpoints
- Sort/order parameters
- ORM raw query helpers (e.g. `raw()`, `execute()`)

### 🛡️ Mitigation

- Use prepared statements / parameterised queries
- Never concatenate user input into SQL
- Allowlist sort/order field names
- Restrict database user permissions
- Hide database errors from end users

---

## 3. Insecure Direct Object Reference (IDOR)

**What is it?**
IDOR happens when a user can access another user's resource by changing an ID, UUID, or filename — a broken access control issue.

### ❌ Vulnerable (Node.js / Express)

```js
app.get("/api/orders/:id", async (req, res) => {
  const order = await db.getOrderById(req.params.id);
  res.json(order); // no ownership check!
});
```

### ✅ Safer (Node.js / Express)

```js
app.get("/api/orders/:id", async (req, res) => {
  const order = await db.getOrderById(req.params.id);

  if (!order || order.user_id !== req.user.id) {
    return res.status(403).json({ error: "Forbidden" });
  }

  res.json(order);
});
```

---

### ❌ Vulnerable (Python / Flask)

```python
@app.route("/invoice/<invoice_id>")
def invoice(invoice_id):
    invoice = get_invoice(invoice_id)
    return jsonify(invoice)
```

### ✅ Safer (Python / Flask)

```python
@app.route("/invoice/<invoice_id>")
def invoice(invoice_id):
    invoice = get_invoice(invoice_id)

    if not invoice or invoice["owner_id"] != current_user.id:
        return {"error": "Forbidden"}, 403

    return jsonify(invoice)
```

### 🔍 What to look for

- `/api/users/:id`, `/api/orders/:id`, etc.
- Invoice and document download endpoints
- Support ticket access
- Export and report endpoints
- Mobile app APIs
- GraphQL object lookups
- UUIDs (they are not a substitute for authorisation)

### 🛡️ Mitigation

- Enforce authorisation on every request — never assume
- Verify ownership server-side
- Review read, update, delete, and export endpoints
- Never trust client-provided object references
- Test endpoints with low-privileged accounts

---

## 4. Server-Side Request Forgery (SSRF)

**What is it?**
SSRF happens when the server makes HTTP requests to attacker-controlled URLs, potentially exposing internal services or cloud metadata endpoints.

### ❌ Vulnerable (Python)

```python
import requests

@app.route("/fetch")
def fetch():
    url = request.args.get("url")
    return requests.get(url).text  # fetches any URL!
```

### ✅ Safer (Python)

```python
from urllib.parse import urlparse
import requests

ALLOWED_HOSTS = {"example.com", "api.example.com"}

@app.route("/fetch")
def fetch():
    url = request.args.get("url")
    parsed = urlparse(url)

    if parsed.hostname not in ALLOWED_HOSTS:
        return {"error": "Host not allowed"}, 400

    return requests.get(url, timeout=3).text
```

### 🔍 What to look for

- URL preview / link unfurl features
- Image import by URL
- Webhook testing functionality
- PDF or screenshot generators
- Avatar fetchers
- RSS / feed import
- Any backend integration accepting a URL

### 🛡️ Mitigation

- Use strict allowlists for outbound destinations
- Validate resolved IPs against blocklists (private, loopback, link-local)
- Restrict HTTP redirects
- Set short request timeouts
- Limit outbound protocols (HTTPS only where possible)

---

## 5. File Upload Issues

**What is it?**
Trusting filenames, extensions, or MIME types too much can lead to malicious file uploads, stored XSS, or code execution.

### ❌ Vulnerable (Node.js)

```js
if (req.file.originalname.endsWith(".jpg")) {
  saveFile(req.file); // extension-only check
}
```

**Why it's risky:** File content may not match the extension. A `.php` file renamed to `.jpg` bypasses this.

### ✅ Safer (Node.js)

```js
const allowedTypes = ["image/jpeg", "image/png"];

if (!allowedTypes.includes(req.file.mimetype)) {
  return res.status(400).send("Invalid file type");
}

if (req.file.size > 2 * 1024 * 1024) {
  return res.status(400).send("File too large");
}

saveFileWithRandomName(req.file);
```

### 🔍 What to look for

- Extension-only or MIME-only validation
- Missing file size limits
- Files stored inside web root
- Predictable or preserved upload filenames
- Image/document converters
- File preview systems
- Cloud storage bucket permissions

### 🛡️ Mitigation

- Validate extension + MIME type + content signature where possible
- Rename uploaded files with random names
- Store files outside the web root
- Prevent execution of uploaded files on the server
- Restrict the set of allowed file types
- Scan or inspect files where appropriate

---

## 6. Command Injection

**What is it?**
Command injection happens when user input reaches system shell commands, leading to arbitrary command execution.

### ❌ Vulnerable (Python)

```python
import os

filename = request.args.get("file")
os.system("cat " + filename)  # shell injection!
```

### ✅ Safer (Python)

```python
import subprocess

filename = request.args.get("file")
subprocess.run(["cat", filename], check=True)
```

---

### ❌ Vulnerable (Node.js)

```js
const { exec } = require("child_process");
exec("ping -c 1 " + req.query.host);
```

### ✅ Safer (Node.js)

```js
const { execFile } = require("child_process");
execFile("ping", ["-c", "1", req.query.host]);
```

**The key difference: argument arrays bypass the shell entirely — no injection possible.**

### 🔍 What to look for

- `exec`, `system`, `os.system`, `shell=True`
- Admin utility endpoints
- Image and document converters
- Archive extraction features
- Diagnostic or debug endpoints

### 🛡️ Mitigation

- Avoid shelling out when a library API exists
- Use argument arrays, never string concatenation
- Never use `shell=True` (Python) or `exec` (Node.js) with user input
- Strictly allowlist permitted input values
- Run the process with the least required privilege

---

## 7. NoSQL Injection

**What is it?**
NoSQL injection often appears in MongoDB applications where JSON operators like `$ne`, `$gt`, or `$regex` are accepted as query parameters.

### ❌ Vulnerable (Node.js + MongoDB)

```js
app.post("/login", async (req, res) => {
  const user = await db.collection("users").findOne({
    username: req.body.username,
    password: req.body.password  // objects allowed in body!
  });

  if (user) return res.send("Logged in");
  res.status(401).send("Invalid");
});
```

**Attack payload:** `{ "username": "admin", "password": { "$ne": "" } }` — logs in without knowing the password.

### ✅ Safer (Node.js)

```js
app.post("/login", async (req, res) => {
  const username = String(req.body.username || "");
  const password = String(req.body.password || "");

  const user = await db.collection("users").findOne({
    username,
    password
  });

  if (user) return res.send("Logged in");
  res.status(401).send("Invalid");
});
```

### 🔍 What to look for

- JSON body parsers without type enforcement
- Login and authentication endpoints
- Search and filter query builders
- Nested JSON objects passed to DB queries
- GraphQL resolvers that forward filters directly

### 🛡️ Mitigation

- Enforce primitive types (cast to `String`, `Number`, etc.)
- Validate schema before executing queries
- Reject requests containing unexpected operator keys
- Avoid passing raw JSON filter objects into DB lookups

---

## 8. Authentication Weaknesses

**What is it?**
Weak login flows, insecure reset tokens, missing rate limiting, and user enumeration all undermine authentication.

### ❌ Vulnerable — user enumeration

```js
if (!user) {
  return res.status(404).send("User does not exist");
}
if (!passwordMatches) {
  return res.status(401).send("Wrong password"); // reveals username validity!
}
```

### ✅ Safer

```js
// Same message regardless of which check failed
return res.status(401).send("Invalid credentials");
```

### 🔍 What to look for

- Different error messages for wrong username vs. wrong password
- Password reset token reuse or predictable tokens
- Reset tokens that never expire
- No rate limiting or account lockout on login
- No MFA on sensitive actions
- Sessions not invalidated on logout or password change

### 🛡️ Mitigation

- Use generic responses for all login and reset failures
- Issue random, single-use, short-lived reset tokens
- Rate-limit and throttle login and reset flows
- Require MFA where appropriate
- Invalidate all sessions on logout and password change
- Require re-authentication before sensitive actions

---

## 9. Security Misconfiguration

**What is it?**
Insecure defaults, debug settings, missing security headers, and weak CORS configurations create easy entry points.

### ❌ Vulnerable — debug mode in production (Python / Flask)

```python
app.run(debug=True)
```

**Why it's risky:** Verbose errors, internal stack traces, and in some setups, interactive debuggers exposed to the internet.

### ✅ Safer

```python
app.run(debug=False)
```

---

### ❌ Vulnerable — overly permissive CORS (Node.js)

```js
app.use(cors({
  origin: "*",
  credentials: true  // wildcard + credentials = dangerous
}));
```

### ✅ Safer

```js
app.use(cors({
  origin: "https://yourdomain.com",
  credentials: true
}));
```

### 🔍 What to look for

- Debug mode enabled in production
- Stack traces or internal errors shown to users
- Default credentials left unchanged
- Exposed admin panels with no access control
- Missing security headers
- Wildcard or overly permissive CORS rules
- Directory listing enabled
- Unused services still exposed

### 🛡️ Mitigation

- Disable debug mode in all production environments
- Never return stack traces to end users
- Use strict, specific CORS rules
- Set the following security headers:
  - `Content-Security-Policy`
  - `X-Content-Type-Options: nosniff`
  - `Referrer-Policy`
  - `Strict-Transport-Security`
- Protect admin interfaces with authentication and IP restriction
- Remove or disable unused routes and services
- Rotate all default credentials and secrets

---

## 10. Quick Reviewer Checklist

Use this when reviewing any web application for common security issues.

- [ ] Is user input rendered in HTML or JavaScript?
- [ ] Is user input used in SQL or NoSQL queries?
- [ ] Are object IDs protected with server-side authorisation?
- [ ] Can users access other users' data or files?
- [ ] Can the server fetch user-supplied URLs?
- [ ] Are file uploads validated and stored safely?
- [ ] Are shell or system commands used with user input?
- [ ] Are JSON filters passed directly into database queries?
- [ ] Is debug mode disabled in production?
- [ ] Are stack traces or internal errors hidden from users?
- [ ] Are security headers present and correctly configured?
- [ ] Is CORS restricted to known origins?
- [ ] Are sessions protected and properly invalidated?

---

*These examples are for education, code review, and authorized security testing only.*
