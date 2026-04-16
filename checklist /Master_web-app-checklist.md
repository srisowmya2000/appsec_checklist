# Master Web Application Security Checklist

A simple checklist for reviewing common web application security risks.

---

## 1. Authentication

- [ ] Strong password policy is enforced
- [ ] Multi-factor authentication (MFA) is enabled for sensitive actions
- [ ] Login flow does not allow username/email enumeration
- [ ] Password reset tokens are random, single-use, and expire quickly
- [ ] Default credentials are removed
- [ ] Account lockout or throttling exists for repeated failed logins
- [ ] Sensitive actions require re-authentication where appropriate

---

## 2. Session Management

- [ ] Session cookies use `HttpOnly`
- [ ] Session cookies use `Secure`
- [ ] Session cookies use `SameSite`
- [ ] Session IDs are random and sufficiently long
- [ ] Sessions are invalidated on logout
- [ ] Session fixation is prevented after login
- [ ] Idle timeout exists
- [ ] Absolute session timeout exists

---

## 3. Access Control

- [ ] Authorization is enforced on the server side
- [ ] Users cannot access other users’ resources
- [ ] Admin routes are properly restricted
- [ ] Object-level access checks exist for IDs and UUIDs
- [ ] Hidden form fields and client-side checks are not trusted
- [ ] Role-based access control is implemented correctly
- [ ] Sensitive actions are protected against privilege escalation

---

## 4. Input Validation

- [ ] All input is validated on the server side
- [ ] Allowlists are used where possible
- [ ] Query parameters are validated
- [ ] Request body fields are validated
- [ ] Headers are validated where applicable
- [ ] File names and URLs are validated
- [ ] Validation errors do not leak internal details

---

## 5. Output Encoding

- [ ] HTML output is escaped
- [ ] JavaScript context is handled safely
- [ ] User content is sanitized before rendering
- [ ] DOM sinks such as `innerHTML` are reviewed
- [ ] Safe templating is used
- [ ] Rich text is sanitized if supported

---

## 6. Database Security

- [ ] Parameterized queries are used
- [ ] Unsafe raw SQL is avoided
- [ ] ORM usage is reviewed for unsafe raw queries
- [ ] Database permissions follow least privilege
- [ ] Database errors are not exposed to users
- [ ] Sensitive data is encrypted or hashed properly

---

## 7. File Upload Security

- [ ] File extension validation exists
- [ ] MIME type validation exists
- [ ] File size restrictions are enforced
- [ ] Uploaded files are renamed safely
- [ ] Uploaded files are stored safely
- [ ] Dangerous files cannot execute on the server
- [ ] File content inspection is performed where appropriate

---

## 8. API Security

- [ ] Authentication is enforced on sensitive endpoints
- [ ] Authorization is checked on every request
- [ ] Rate limiting is enabled
- [ ] CORS is configured securely
- [ ] Mass assignment risks are reviewed
- [ ] Sensitive endpoints are logged
- [ ] Error messages do not leak internals

---

## 9. Security Misconfiguration

- [ ] Debug mode is disabled in production
- [ ] Stack traces are hidden from users
- [ ] Directory listing is disabled
- [ ] Default credentials and secrets are changed
- [ ] Admin panels are protected
- [ ] Unused services and routes are removed
- [ ] Security headers are reviewed

---

## 10. Dependencies and Components

- [ ] Dependencies are inventoried
- [ ] Vulnerable packages are updated
- [ ] Unused packages are removed
- [ ] Dependency scanning is enabled
- [ ] Third-party components are reviewed regularly
- [ ] Framework security best practices are followed

---

## Notes

This checklist is intended for:

- secure code review
- manual web application testing
- application security learning
- authorized bug bounty and penetration testing
