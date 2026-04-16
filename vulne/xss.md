# Cross-Site Scripting (XSS)

## What is it?

Cross-Site Scripting (XSS) happens when attacker-controlled input is included in a page or browser-executed context without proper protection.

This can allow malicious JavaScript to run in another user’s browser.

---

## Common Types

- Reflected XSS
- Stored XSS
- DOM-Based XSS

---

## Where it commonly appears

- Search boxes
- Comment sections
- Profile fields
- Support tickets
- Admin notes
- Chat messages
- Markdown / rich text features
- Query parameters rendered in UI
- Client-side routing / fragments

---

## Why it happens

- Unescaped output
- Unsafe DOM manipulation
- Using `innerHTML`
- Unsafe template rendering
- Weak HTML sanitization
- Trusting user input in frontend code
- Rendering user content inside script or attribute contexts

---


