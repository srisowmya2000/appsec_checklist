<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Interactive Web Application Security Examples</title>
  <style>
    :root {
      --bg: #0b1020;
      --panel: #121933;
      --panel-2: #1a2347;
      --text: #e8ecf8;
      --muted: #aab3d1;
      --accent: #7aa2ff;
      --accent-2: #86e1c6;
      --danger: #ff8f8f;
      --ok: #99e2b4;
      --border: #2a3568;
      --chip: #202a54;
      --shadow: 0 10px 30px rgba(0,0,0,0.25);
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background: linear-gradient(180deg, #0a0f1d 0%, #0d1428 100%);
      color: var(--text);
      line-height: 1.6;
    }

    .wrap {
      width: min(1180px, calc(100% - 32px));
      margin: 0 auto;
    }

    header {
      padding: 40px 0 20px;
    }

    .hero {
      background: linear-gradient(135deg, rgba(122,162,255,0.14), rgba(134,225,198,0.10));
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 28px;
      box-shadow: var(--shadow);
    }

    h1, h2, h3 { line-height: 1.2; margin: 0 0 12px; }
    h1 { font-size: clamp(2rem, 4vw, 3rem); }
    h2 { font-size: 1.6rem; margin-top: 32px; }
    h3 { font-size: 1.1rem; margin-top: 22px; }
    p { margin: 10px 0; color: var(--text); }
    .muted { color: var(--muted); }

    .top-grid {
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 18px;
      margin-top: 18px;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 18px;
      box-shadow: var(--shadow);
    }

    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 14px;
    }

    select, input {
      background: var(--panel-2);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 10px 12px;
      font-size: 0.95rem;
      outline: none;
    }

    .chip-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 12px;
    }

    .chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: var(--chip);
      border: 1px solid var(--border);
      color: var(--text);
      border-radius: 999px;
      padding: 7px 12px;
      font-size: 0.9rem;
      cursor: pointer;
      user-select: none;
    }

    .chip.active {
      background: rgba(122,162,255,0.18);
      border-color: var(--accent);
      color: #fff;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
      margin-top: 12px;
    }

    .stat {
      background: var(--panel-2);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 14px;
    }

    .stat strong {
      display: block;
      font-size: 1.3rem;
      margin-bottom: 4px;
    }

    .section-title {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin: 34px 0 12px;
    }

    .vuln-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 18px;
      margin-top: 10px;
    }

    .severity {
      display: inline-block;
      border-radius: 999px;
      padding: 6px 10px;
      font-size: 0.8rem;
      border: 1px solid var(--border);
      background: rgba(255,255,255,0.04);
      color: var(--muted);
    }

    .severity.high, .severity.critical { color: var(--danger); }
    .severity.medium { color: #ffd48f; }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 8px 0 14px;
    }

    .tag {
      font-size: 0.78rem;
      background: rgba(134,225,198,0.12);
      color: var(--accent-2);
      border: 1px solid rgba(134,225,198,0.24);
      border-radius: 999px;
      padding: 4px 10px;
    }

    details {
      border: 1px solid var(--border);
      border-radius: 14px;
      background: var(--panel-2);
      margin-top: 12px;
      overflow: hidden;
    }

    summary {
      list-style: none;
      cursor: pointer;
      padding: 14px 16px;
      font-weight: 600;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    details > div {
      padding: 0 16px 16px;
    }

    pre {
      background: #0a1022;
      color: #dfe7ff;
      padding: 14px;
      border-radius: 14px;
      overflow-x: auto;
      border: 1px solid #24315f;
      font-size: 0.9rem;
    }

    code { font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace; }

    ul { padding-left: 20px; }
    li { margin: 6px 0; }

    .good { color: var(--ok); }
    .bad { color: var(--danger); }
    .mini {
      margin-top: 12px;
      padding: 12px 14px;
      border-radius: 14px;
      background: rgba(255,255,255,0.03);
      border: 1px solid var(--border);
    }

    .review {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 18px;
      margin-top: 16px;
    }

    .footer {
      padding: 28px 0 50px;
      color: var(--muted);
    }

    a { color: var(--accent); text-decoration: none; }
    a:hover { text-decoration: underline; }

    @media (max-width: 900px) {
      .top-grid, .vuln-grid, .review { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="hero">
        <h1>Interactive Web Application Security Examples</h1>
        <p class="muted">A single-file reference for common web vulnerabilities, insecure examples, safer patterns, and quick review guidance. Built to be simple enough for GitHub and practical enough for code review and AppSec learning.</p>

        <div class="controls">
          <select id="stackFilter">
            <option value="all">All stacks</option>
            <option value="php">PHP</option>
            <option value="python">Python</option>
            <option value="nodejs">Node.js</option>
            <option value="javascript">JavaScript</option>
            <option value="general">General</option>
          </select>
          <select id="severityFilter">
            <option value="all">All severity</option>
            <option value="critical">Critical</option>
            <option value="high">High</option>
            <option value="medium">Medium</option>
          </select>
          <input id="searchBox" type="text" placeholder="Search vulnerability, sink, mitigation..." />
        </div>

        <div class="chip-row" id="quickFilters">
          <button class="chip active" data-filter="all">All</button>
          <button class="chip" data-filter="xss">XSS</button>
          <button class="chip" data-filter="sqli">SQLi</button>
          <button class="chip" data-filter="idor">IDOR</button>
          <button class="chip" data-filter="file-upload">File Upload</button>
          <button class="chip" data-filter="ssrf">SSRF</button>
          <button class="chip" data-filter="command-injection">Command Injection</button>
          <button class="chip" data-filter="nosql">NoSQL Injection</button>
          <button class="chip" data-filter="auth">Auth Weaknesses</button>
          <button class="chip" data-filter="misconfig">Misconfiguration</button>
        </div>
      </div>

      <div class="top-grid">
        <section class="card">
          <h2>How to use this file</h2>
          <p>Use the filters to narrow by stack, severity, or vulnerability name. Open each section to view insecure code, safer patterns, impact, and what to review in a real application.</p>
          <div class="mini">
            <strong>Good for:</strong>
            <ul>
              <li>GitHub documentation</li>
              <li>Beginner AppSec learning</li>
              <li>Developer awareness</li>
              <li>Manual code review</li>
              <li>Authorized testing notes</li>
            </ul>
          </div>
        </section>

        <section class="card">
          <h2>Quick overview</h2>
          <div class="stats">
            <div class="stat"><strong id="visibleCount">9</strong><span>visible sections</span></div>
            <div class="stat"><strong>4</strong><span>stacks covered</span></div>
            <div class="stat"><strong>2+</strong><span>examples per issue</span></div>
            <div class="stat"><strong>1</strong><span>self-contained HTML file</span></div>
          </div>
        </section>
      </div>
    </header>

    <main>
      <div class="section-title">
        <h2>Vulnerability examples</h2>
        <span class="muted">Expand any card</span>
      </div>

      <section class="vuln-grid" id="vulnContainer">
        <article class="card vuln-card" data-name="xss" data-stack="php nodejs python javascript" data-severity="high">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Cross-Site Scripting (XSS)</h3>
            <span class="severity high">High</span>
          </div>
          <p class="muted">Untrusted input reaches browser-executed context without proper encoding or sanitization.</p>
          <div class="tags"><span class="tag">HTML context</span><span class="tag">DOM sinks</span><span class="tag">Output encoding</span></div>

          <details>
            <summary>Vulnerable examples <span>+</span></summary>
            <div>
              <p><span class="bad">Insecure PHP</span></p>
              <pre><code>&lt;?php
echo "&lt;h1&gt;Hello " . $_GET['name'] . "&lt;/h1&gt;";
?&gt;</code></pre>
              <p><span class="bad">Insecure Node.js / Express</span></p>
              <pre><code>app.get("/hello", (req, res) =&gt; {
  res.send(`&lt;h1&gt;Hello ${req.query.name}&lt;/h1&gt;`);
});</code></pre>
              <p><span class="bad">Insecure client-side JavaScript</span></p>
              <pre><code>document.getElementById("output").innerHTML = location.hash.substring(1);</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer patterns <span>+</span></summary>
            <div>
              <p><span class="good">Safer PHP</span></p>
              <pre><code>&lt;?php
echo "&lt;h1&gt;Hello " . htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8') . "&lt;/h1&gt;";
?&gt;</code></pre>
              <p><span class="good">Safer client-side JavaScript</span></p>
              <pre><code>document.getElementById("output").textContent = location.hash.substring(1);</code></pre>
              <ul>
                <li>Use context-aware output encoding</li>
                <li>Avoid <code>innerHTML</code> where possible</li>
                <li>Sanitize rich text if HTML is allowed</li>
                <li>Use CSP as defense-in-depth</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>Search pages, comments, profiles, support tickets</li>
                <li>DOM sinks: <code>innerHTML</code>, <code>outerHTML</code>, <code>document.write</code></li>
                <li>Template rendering of user-controlled content</li>
                <li>HTML, attribute, JavaScript, and URL contexts</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="sqli" data-stack="php python nodejs" data-severity="critical">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>SQL Injection (SQLi)</h3>
            <span class="severity critical">Critical</span>
          </div>
          <p class="muted">User input is inserted into SQL queries unsafely, altering intended database logic.</p>
          <div class="tags"><span class="tag">Raw SQL</span><span class="tag">Prepared statements</span><span class="tag">Query manipulation</span></div>

          <details>
            <summary>Vulnerable examples <span>+</span></summary>
            <div>
              <p><span class="bad">Insecure PHP</span></p>
              <pre><code>&lt;?php
$id = $_GET['id'];
$query = "SELECT * FROM users WHERE id = $id";
$result = mysqli_query($conn, $query);
?&gt;</code></pre>
              <p><span class="bad">Insecure Python</span></p>
              <pre><code>user_id = request.args.get("id")
query = f"SELECT * FROM users WHERE id = {user_id}"
cursor.execute(query)</code></pre>
              <p><span class="bad">Insecure Node.js</span></p>
              <pre><code>const query = "SELECT * FROM users WHERE email = '" + req.body.email + "'";
db.query(query);</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer patterns <span>+</span></summary>
            <div>
              <p><span class="good">Prepared statements</span></p>
              <pre><code>$stmt = $conn-&gt;prepare("SELECT * FROM users WHERE id = ?");
$stmt-&gt;bind_param("i", $_GET['id']);
$stmt-&gt;execute();</code></pre>
              <pre><code>cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))</code></pre>
              <pre><code>db.query("SELECT * FROM users WHERE email = ?", [req.body.email]);</code></pre>
              <ul>
                <li>Use parameterized queries everywhere</li>
                <li>Avoid raw string concatenation</li>
                <li>Allowlist dynamic sort and order fields</li>
                <li>Restrict DB privileges</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>Login forms, search fields, filters, sorting parameters</li>
                <li>Raw query helpers inside ORMs</li>
                <li>Admin reports and export features</li>
                <li>Unexpected response changes, time delays, or DB errors</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="idor" data-stack="python nodejs general" data-severity="high">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Insecure Direct Object Reference (IDOR)</h3>
            <span class="severity high">High</span>
          </div>
          <p class="muted">A user can access another user’s resource because the server checks the object ID, but not ownership or authorization.</p>
          <div class="tags"><span class="tag">Broken access control</span><span class="tag">Object ownership</span><span class="tag">API risk</span></div>

          <details>
            <summary>Vulnerable examples <span>+</span></summary>
            <div>
              <pre><code>app.get("/api/orders/:id", async (req, res) =&gt; {
  const order = await db.getOrderById(req.params.id);
  res.json(order);
});</code></pre>
              <pre><code>@app.route("/invoice/&lt;invoice_id&gt;")
def invoice(invoice_id):
    invoice = get_invoice(invoice_id)
    return jsonify(invoice)</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer patterns <span>+</span></summary>
            <div>
              <pre><code>app.get("/api/orders/:id", async (req, res) =&gt; {
  const order = await db.getOrderById(req.params.id);
  if (!order || order.user_id !== req.user.id) {
    return res.status(403).json({ error: "Forbidden" });
  }
  res.json(order);
});</code></pre>
              <pre><code>@app.route("/invoice/&lt;invoice_id&gt;")
def invoice(invoice_id):
    invoice = get_invoice(invoice_id)
    if not invoice or invoice["owner_id"] != current_user.id:
        return {"error": "Forbidden"}, 403
    return jsonify(invoice)</code></pre>
              <ul>
                <li>Always enforce authorization server-side</li>
                <li>Check ownership for read, update, delete, export, and download actions</li>
                <li>Do not assume UUIDs are a security control</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>User profiles, invoices, downloads, support tickets, documents</li>
                <li>Mobile APIs, SPA APIs, GraphQL object queries</li>
                <li>Numeric IDs, UUIDs, filenames, export endpoints</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="file-upload" data-stack="nodejs general" data-severity="high">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>File Upload Issues</h3>
            <span class="severity high">High</span>
          </div>
          <p class="muted">Applications trust filenames, extensions, MIME types, or storage paths too much.</p>
          <div class="tags"><span class="tag">MIME validation</span><span class="tag">Storage safety</span><span class="tag">Execution risk</span></div>

          <details>
            <summary>Vulnerable example <span>+</span></summary>
            <div>
              <pre><code>if (req.file.originalname.endsWith(".jpg")) {
  saveFile(req.file);
}</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer pattern <span>+</span></summary>
            <div>
              <pre><code>const allowedTypes = ["image/jpeg", "image/png"];
if (!allowedTypes.includes(req.file.mimetype)) {
  return res.status(400).send("Invalid file type");
}
if (req.file.size &gt; 2 * 1024 * 1024) {
  return res.status(400).send("File too large");
}
saveFileWithRandomName(req.file);</code></pre>
              <ul>
                <li>Check extension, MIME type, and content signature where possible</li>
                <li>Rename uploads safely</li>
                <li>Store outside web root when possible</li>
                <li>Prevent server-side execution of uploaded files</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>Upload handlers, file serving routes, image/document processors</li>
                <li>Public object storage permissions</li>
                <li>Archive extraction or conversion pipelines</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="ssrf" data-stack="python nodejs general" data-severity="high">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Server-Side Request Forgery (SSRF)</h3>
            <span class="severity high">High</span>
          </div>
          <p class="muted">The server fetches attacker-controlled URLs and may reach internal systems or sensitive metadata services.</p>
          <div class="tags"><span class="tag">Outbound requests</span><span class="tag">Metadata risk</span><span class="tag">Allowlist</span></div>

          <details>
            <summary>Vulnerable example <span>+</span></summary>
            <div>
              <pre><code>import requests

@app.route("/fetch")
def fetch():
    url = request.args.get("url")
    return requests.get(url).text</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer pattern <span>+</span></summary>
            <div>
              <pre><code>from urllib.parse import urlparse
import requests

ALLOWED_HOSTS = {"example.com", "api.example.com"}

@app.route("/fetch")
def fetch():
    url = request.args.get("url")
    parsed = urlparse(url)
    if parsed.hostname not in ALLOWED_HOSTS:
        return {"error": "Host not allowed"}, 400
    return requests.get(url, timeout=3).text</code></pre>
              <ul>
                <li>Use strict allowlists for outbound destinations</li>
                <li>Validate DNS and IP resolution</li>
                <li>Block private and link-local ranges</li>
                <li>Restrict redirects and outbound protocols</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>URL preview tools, webhook validators, screenshot services</li>
                <li>Image import by URL, PDF generators, avatar fetchers</li>
                <li>Internal service integrations</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="command-injection" data-stack="python nodejs" data-severity="critical">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Command Injection</h3>
            <span class="severity critical">Critical</span>
          </div>
          <p class="muted">User input reaches system shell commands unsafely.</p>
          <div class="tags"><span class="tag">Shell execution</span><span class="tag">Process control</span><span class="tag">RCE risk</span></div>

          <details>
            <summary>Vulnerable examples <span>+</span></summary>
            <div>
              <pre><code>import os
filename = request.args.get("file")
os.system("cat " + filename)</code></pre>
              <pre><code>const { exec } = require("child_process");
exec("ping -c 1 " + req.query.host);</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer patterns <span>+</span></summary>
            <div>
              <pre><code>import subprocess
subprocess.run(["cat", filename], check=True)</code></pre>
              <pre><code>const { execFile } = require("child_process");
execFile("ping", ["-c", "1", req.query.host]);</code></pre>
              <ul>
                <li>Avoid shelling out if possible</li>
                <li>Use argument arrays rather than shell concatenation</li>
                <li>Strictly validate or allowlist arguments</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li><code>exec</code>, <code>system</code>, <code>os.system</code>, <code>shell=True</code></li>
                <li>Diagnostic endpoints, file converters, admin utilities</li>
                <li>Archive extraction or external tool wrappers</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="nosql" data-stack="nodejs" data-severity="high">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>NoSQL Injection</h3>
            <span class="severity high">High</span>
          </div>
          <p class="muted">Flexible JSON-based filters or operator injection alter database query behavior.</p>
          <div class="tags"><span class="tag">MongoDB</span><span class="tag">JSON filters</span><span class="tag">Type enforcement</span></div>

          <details>
            <summary>Vulnerable example <span>+</span></summary>
            <div>
              <pre><code>app.post("/login", async (req, res) =&gt; {
  const user = await db.collection("users").findOne({
    username: req.body.username,
    password: req.body.password
  });
  if (user) return res.send("Logged in");
  res.status(401).send("Invalid");
});</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer pattern <span>+</span></summary>
            <div>
              <pre><code>app.post("/login", async (req, res) =&gt; {
  const username = String(req.body.username || "");
  const password = String(req.body.password || "");
  const user = await db.collection("users").findOne({ username, password });
  if (user) return res.send("Logged in");
  res.status(401).send("Invalid");
});</code></pre>
              <ul>
                <li>Enforce primitive types</li>
                <li>Validate schema before building queries</li>
                <li>Watch operators such as <code>$ne</code>, <code>$gt</code>, <code>$regex</code></li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>JSON body parsers, login endpoints, search filters</li>
                <li>GraphQL resolvers mapping input directly to DB filters</li>
                <li>Nested object payloads</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="auth" data-stack="nodejs python general" data-severity="medium">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Authentication Weaknesses</h3>
            <span class="severity medium">Medium</span>
          </div>
          <p class="muted">Weak login, reset, MFA, or session handling exposes accounts to abuse.</p>
          <div class="tags"><span class="tag">Enumeration</span><span class="tag">Reset flows</span><span class="tag">Brute-force</span></div>

          <details>
            <summary>Vulnerable example <span>+</span></summary>
            <div>
              <pre><code>if (!user) {
  return res.status(404).send("User does not exist");
}
if (!passwordMatches) {
  return res.status(401).send("Wrong password");
}</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer pattern <span>+</span></summary>
            <div>
              <pre><code>return res.status(401).send("Invalid credentials");</code></pre>
              <ul>
                <li>Use generic login and reset responses</li>
                <li>Rate limit repeated attempts</li>
                <li>Use expiring, single-use reset tokens</li>
                <li>Require MFA for sensitive actions where appropriate</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>Username enumeration in login or reset flows</li>
                <li>Password reset token lifetime and reuse</li>
                <li>Session invalidation on logout or password change</li>
                <li>Brute-force throttling and MFA coverage</li>
              </ul>
            </div>
          </details>
        </article>

        <article class="card vuln-card" data-name="misconfig" data-stack="python nodejs general" data-severity="medium">
          <div class="section-title" style="margin: 0 0 8px;">
            <h3>Security Misconfiguration</h3>
            <span class="severity medium">Medium</span>
          </div>
          <p class="muted">Insecure defaults, verbose errors, weak headers, or overly permissive settings expand attack surface.</p>
          <div class="tags"><span class="tag">Debug mode</span><span class="tag">CORS</span><span class="tag">Headers</span></div>

          <details>
            <summary>Vulnerable examples <span>+</span></summary>
            <div>
              <pre><code>app.run(debug=True)</code></pre>
              <pre><code>app.use(cors({
  origin: "*",
  credentials: true
}));</code></pre>
            </div>
          </details>

          <details>
            <summary>Safer patterns <span>+</span></summary>
            <div>
              <ul>
                <li>Disable debug mode in production</li>
                <li>Hide stack traces from end users</li>
                <li>Restrict CORS origins</li>
                <li>Review security headers such as CSP, HSTS, X-Content-Type-Options, Referrer-Policy</li>
                <li>Protect admin routes and remove unused services</li>
              </ul>
            </div>
          </details>

          <details>
            <summary>What to review <span>+</span></summary>
            <div>
              <ul>
                <li>Production config, default secrets, admin panels</li>
                <li>Framework debug settings and verbose errors</li>
                <li>Security headers and transport protection</li>
              </ul>
            </div>
          </details>
        </article>
      </section>

      <h2>Quick reviewer checklist</h2>
      <section class="review">
        <div class="card">
          <h3>Ask these questions</h3>
          <ul>
            <li>Is user input rendered into HTML or JavaScript?</li>
            <li>Is user input used in SQL or database queries?</li>
            <li>Are object IDs protected with server-side authorization?</li>
            <li>Can the server fetch user-supplied URLs?</li>
            <li>Are files uploaded and stored safely?</li>
            <li>Are shell or system commands built from user input?</li>
          </ul>
        </div>
        <div class="card">
          <h3>And these too</h3>
          <ul>
            <li>Can users access other users’ data or files?</li>
            <li>Are JSON filters passed directly into queries?</li>
            <li>Is debug mode enabled in production?</li>
            <li>Do errors leak internal details?</li>
            <li>Is CORS too permissive?</li>
            <li>Are session cookies hardened?</li>
          </ul>
        </div>
      </section>

      <h2>Public learning references</h2>
      <section class="card">
        <ul>
          <li><a href="https://owasp.org/www-project-top-ten/" target="_blank" rel="noopener noreferrer">OWASP Top 10</a></li>
          <li><a href="https://owasp.org/www-project-web-security-testing-guide/" target="_blank" rel="noopener noreferrer">OWASP Web Security Testing Guide</a></li>
          <li><a href="https://portswigger.net/web-security" target="_blank" rel="noopener noreferrer">PortSwigger Web Security Academy</a></li>
          <li><a href="https://www.youtube.com/results?search_query=owasp+top+10+web+application+security" target="_blank" rel="noopener noreferrer">YouTube: OWASP Top 10 search</a></li>
          <li><a href="https://www.youtube.com/results?search_query=portswigger+web+security+academy" target="_blank" rel="noopener noreferrer">YouTube: PortSwigger Web Security Academy search</a></li>
        </ul>
      </section>
    </main>

    <footer class="footer">
      <p>This single HTML file is designed for GitHub, GitHub Pages, and gradual expansion. Next steps would be adding more stacks, API examples, and a small severity matrix.</p>
    </footer>
  </div>

  <script>
    const cards = Array.from(document.querySelectorAll('.vuln-card'));
    const searchBox = document.getElementById('searchBox');
    const stackFilter = document.getElementById('stackFilter');
    const severityFilter = document.getElementById('severityFilter');
    const visibleCount = document.getElementById('visibleCount');
    const chips = Array.from(document.querySelectorAll('.chip'));

    let chipFilter = 'all';

    function matchesSearch(card, term) {
      if (!term) return true;
      return card.innerText.toLowerCase().includes(term);
    }

    function applyFilters() {
      const term = searchBox.value.trim().toLowerCase();
      const stack = stackFilter.value;
      const sev = severityFilter.value;
      let count = 0;

      cards.forEach(card => {
        const name = card.dataset.name;
        const stacks = card.dataset.stack.split(' ');
        const severity = card.dataset.severity;

        const chipOk = chipFilter === 'all' || name === chipFilter;
        const stackOk = stack === 'all' || stacks.includes(stack);
        const sevOk = sev === 'all' || severity === sev;
        const searchOk = matchesSearch(card, term);

        const show = chipOk && stackOk && sevOk && searchOk;
        card.style.display = show ? '' : 'none';
        if (show) count++;
      });

      visibleCount.textContent = count;
    }

    searchBox.addEventListener('input', applyFilters);
    stackFilter.addEventListener('change', applyFilters);
    severityFilter.addEventListener('change', applyFilters);

    chips.forEach(chip => {
      chip.addEventListener('click', () => {
        chips.forEach(c => c.classList.remove('active'));
        chip.classList.add('active');
        chipFilter = chip.dataset.filter;
        applyFilters();
      });
    });

    applyFilters();
  </script>
</body>
</html>
